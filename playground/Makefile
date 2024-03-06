TARGET ?= x86

XCFLAGS ?= "-g -fno-jump-tables"

EVENTS ?= "instructions"
ITERATIONS ?= 100000

include Makefile.${TARGET}

gcc:FORCE clean
	pushd .. && \
	make coremark.exe XCFLAGS=${XCFLAGS} SEPARATE_COMPILE=1 CC=${PREFIX}gcc LD=${PREFIX}gcc ITERATIONS=${ITERATIONS} && \
	popd

llvm:FORCE clean
	pushd .. && \
	make coremark.exe XCFLAGS=${XCFLAGS} SEPARATE_COMPILE=1  CC=${PREFIX}clang LD=${PREFIX}gcc ITERATIONS=${ITERATIONS} && \
	popd

clean:
	pushd .. && \
	make clean && \
	fd core_portme.o -x rm \
	popd

FORCE:


.PHONY: FORCE gcc llvm clean
