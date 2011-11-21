OPT64 = /home/pulsar64
CFLAGS = -O3 -Wall -DFOLD_USE_INTRINSICS -I$(OPT64)/include -I/usr/include/cfitsio
PROGS = test_psrfits_read \
	raw_quant raw_read \
	raw_head two2eight rawfilterbank raw_ascii2
OBJS  = guppi_status.o guppi_databuf.o guppi_udp.o guppi_error.o \
	guppi_params.o guppi_time.o \
	write_psrfits.o read_psrfits.o misc_utils.o \
	fold.o polyco.o hget.o hput.o sla.o downsample.o
LIBS = -L$(OPT64)/lib -lcfitsio -L$(PRESTO)/lib -lsla -lm -lpthread -I/usr/include/cfitsio -lfftw3f
all: $(PROGS)
clean:
	rm -f $(PROGS) $(THREAD_PROGS) psrfits.tgz *~ *.o test_psrfits_0*.fits
INSTALL_DIR = ../bin
install: $(PROGS)
	mkdir -p $(INSTALL_DIR) && \
	cp -f $(PROGS) $(INSTALL_DIR)
.SECONDEXPANSION:
$(PROGS): $$@.c $(OBJS)
	$(CC) $(CFLAGS) $< -o $@ $(OBJS) $(LIBS) $(THREAD_LIBS)
