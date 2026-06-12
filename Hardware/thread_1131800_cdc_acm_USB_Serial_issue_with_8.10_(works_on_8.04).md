---
title: "cdc_acm USB Serial issue with 8.10 (works on 8.04)"
date: 2009-04-21
forum: Hardware
---

### Post by akos.maroy on 2009-04-21
I'm encountering a strange issue, when connecting an embedded device using the cdc_acm USB serial module to my ubuntu machine. I have an application that connects to the device as a serial port. the application works fine on ubuntu 8.04 (kernel 2.6.24-23-generic, x86_64), but does not work on another machine using ubuntu 8.10 (2.6.27-11-generic, x86_64). I'm running the exact same application on both occasions (copied the binary over from the 8.04 machine to the 8.10 machine).

are there known issues / changes in relation to USB serial or the cdc_acm driver with either kernels after 2.6.24 or ubuntu 8.10?

the process hangs when reading from the serial port - it basically block on the read call forever. (but, this might be because the previous write command didn't go through either)

any help would be appreciated!

---

### Post by akos.maroy on 2009-04-21
some additional info follows.

the simple source code, doing the communication:

```
#include <iostream>
#include <boost/asio.hpp>

using namespace boost::asio;

static const std::string serial_device("/dev/ttyACM0");

static const unsigned char status_message[] = { 6, 10, 0, 0, 0, 0 };
static unsigned char status_ack_message[64];

int main(int argc, char **argv) {

    io_service  io;
    serial_port sp(io);

    std::cerr << "opening serial device " << serial_device << std::endl;
    sp.open(serial_device);
    std::cerr << "serial port open: " << sp.is_open() << std::endl;

    std::cerr << "setting serial port parameters" << std::endl;
    sp.set_option(serial_port_base::baud_rate(19200));
    sp.set_option(serial_port_base::character_size(8));
    sp.set_option(serial_port_base::flow_control(
                                serial_port_base::flow_control::none));
    sp.set_option(serial_port_base::parity(
                                serial_port_base::parity::none));
    sp.set_option(serial_port_base::stop_bits(
                                serial_port_base::stop_bits::one));

    std::size_t written = write(sp, buffer(status_message));
    std::cerr << "written bytes: " << written << std::endl;

    std::size_t read = sp.read_some(buffer(status_ack_message));
    std::cerr << "read bytes: " << read << std::endl;

    return 0;
}

```

the effect is, that the program hans after the output of 'written bytes':

```
$ ./asio_serial 
opening serial device /dev/ttyACM0
serial port open: 1
setting serial port parameters
written bytes: 6

```

the strace of the related calls is:

```
writev(5, [{"\6\n\0\0\0\0", 6}], 1)     = 6
write(2, "written bytes: ", 15written bytes: )         = 15
write(2, "6", 16)                        = 1
write(2, "\n", 1
)                       = 1
readv(5, 0x7fff135ac650, 1)             = -1 EAGAIN (Resource temporarily unavailable)
poll( <unfinished ...>

```

this is on ubuntu 8.10 x86_64, gcc 4.3.2, kernel 2.6.27-11-generic.

now, compiling & running the same on ubuntu 8.04, gcc 4.2.4, kernel 2.6.24-23-generic, all runs through fine:

```
$ ./asio_serial 
opening serial device /dev/ttyACM0
serial port open: 1
setting serial port parameters
written bytes: 6
read bytes: 48

```

with the relevant strace output:

```
writev(5, [{"\6\n\0\0\0\0", 6}], 1)     = 6
write(2, "written bytes: ", 15written bytes: )         = 15
write(2, "6", 16)                        = 1
write(2, "\n", 1
)                       = 1
readv(5, 0x7fffb6ee8f90, 1)             = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=5, events=POLLIN, revents=POLLIN}], 1, -1) = 1
readv(5, [{"0\v\0\0\0\0X\2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 64}], 1) = 48
write(2, "read bytes: ", 12read bytes: )            = 12
write(2, "48", 248)                       = 2
write(2, "\n", 1
)                       = 1
epoll_ctl(3, EPOLL_CTL_DEL, 5, {0, {u32=0, u64=0}}) = 0
close(5)                                = 0
close(3)                                = 0
close(4)                                = 0
exit_group(0)                           = ?
Process 24775 detached

```

---

