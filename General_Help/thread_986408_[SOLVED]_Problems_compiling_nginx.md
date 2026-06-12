---
title: "[SOLVED] Problems compiling nginx"
date: 2008-11-18
forum: General Help
---

### Post by alankennedy100 on 2008-11-18
Hi

I downloaded the latest stable version of nginx but when I try to compile it fails straight away. I can't see any missing dependencies from the output, and I think it might be something obvious that I'm missing...


Here is the output:

e:~/src/nginx-0.6.32$ ./configure --sbin-path=/usr/local/sbin/ --with-http_ssl_module
checking for OS
 + Linux 2.6.27-7-generic i686
checking for C compiler ... found
 + using GNU C compiler
 + gcc version: 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
checking for gcc -pipe switch ... found
checking for gcc variadic macros ... found
checking for C99 variadic macros ... found
checking for unistd.h ... found
checking for inttypes.h ... found
checking for limits.h ... found
checking for sys/filio.h ... not found
checking for crypt.h ... found
checking for Linux specific features
checking for epoll ... found
checking for sendfile() ... found
checking for sendfile64() ... found
checking for sys/prctl.h ... found
checking for prctl(PR_SET_DUMPABLE) ... found
checking for sched_setaffinity() ... found
checking for nobody group ... not found
checking for nogroup group ... found
checking for poll() ... found
checking for /dev/poll ... not found
checking for kqueue ... not found
checking for crypt() ... not found
checking for crypt() in libcrypt ... found
checking for PCRE library ... found
checking for OpenSSL library ... found
checking for zlib library ... found
checking for int size ... 4 bytes
checking for long size ... 4 bytes
checking for long long size ... 8 bytes
checking for void * size ... 4 bytes
checking for uint64_t ... found
checking for sig_atomic_t ... found
checking for sig_atomic_t size ... 4 bytes
checking for socklen_t ... found
checking for in_addr_t ... found
checking for in_port_t ... found
checking for rlim_t ... found
checking for uintptr_t ... uintptr_t found
checking for system endianess ... little endianess
checking for size_t size ... 4 bytes
checking for off_t size ... 8 bytes
checking for time_t size ... 4 bytes
checking for setproctitle() ... not found
checking for pread() ... found
checking for pwrite() ... found
checking for strerror_r() ... found but is not working
checking for gnu style strerror_r() ... found
checking for localtime_r() ... found
checking for posix_memalign() ... found
checking for memalign() ... found
checking for sched_yield() ... found
checking for mmap(MAP_ANON|MAP_SHARED) ... found
checking for mmap("/dev/zero", MAP_SHARED) ... found
checking for System V shared memory ... found
checking for struct msghdr.msg_control ... found
checking for ioctl(FIONBIO) ... found
checking for struct tm.tm_gmtoff ... found

Configuration summary
  + using system PCRE library
  + using system OpenSSL library
  + md5 library is not used
  + sha1 library is not used
  + using system zlib library

  nginx path prefix: "/usr/local/nginx"
  nginx binary file: "/usr/local/sbin/"
  nginx configuration prefix: "/usr/local/nginx/conf"
  nginx configuration file: "/usr/local/nginx/conf/nginx.conf"
  nginx pid file: "/usr/local/nginx/logs/nginx.pid"
  nginx error log file: "/usr/local/nginx/logs/error.log"
  nginx http access log file: "/usr/local/nginx/logs/access.log"
  nginx http client request body temporary files: "/usr/local/nginx/client_body_temp"
  nginx http proxy temporary files: "/usr/local/nginx/proxy_temp"
  nginx http fastcgi temporary files: "/usr/local/nginx/fastcgi_temp"

:~/src/nginx-0.6.32$ make
make -f objs/Makefile
make[1]: Entering directory `/home/alan/src/nginx-0.6.32'
gcc -c -O -pipe  -O -W -Wall -Wpointer-arith -Wno-unused-parameter -Wno-unused-function -Wunused-variable -Wunused-value -Werror -g  -I src/core -I src/event -I src/event/modules -I src/os/unix -I objs \
		-o objs/src/core/nginx.o \
		src/core/nginx.c
cc1: warnings being treated as errors
src/core/nginx.c: In function ‘main’:
src/core/nginx.c:244: error: ignoring return value of ‘write’, declared with attribute warn_unused_result
src/core/nginx.c:249: error: ignoring return value of ‘write’, declared with attribute warn_unused_result
src/core/nginx.c:257: error: ignoring return value of ‘write’, declared with attribute warn_unused_result
make[1]: *** [objs/src/core/nginx.o] Error 1
make[1]: Leaving directory `/home/alan/src/nginx-0.6.32'
make: *** [build] Error 2

---

### Post by dexter on 2008-11-18
You are compiling the source with -Werror option:
```

       -Werror
           Make all warnings into hard errors.  Source code which triggers
           warnings will be rejected.

```

You are also using -Wno-unused-parameter -Wno-unused-function -Wunused-variable -Wunused-value, which will generate warning for all unused variables. Combine this with -Werror and it's normal that the code isn't compiling.

Try removing the -Werror option.

---

### Post by Yellow Pasque on 2008-11-18
gcc 4.3 treats some warnings as errors. This makes compiling some programs a pain.
Try this:
```
NO_WARNING_CHECKS=yes ./configure --sbin-path=/usr/local/sbin/ --with-http_ssl_module
```

---

### Post by alankennedy100 on 2008-11-18
That worked, Thanks!

---

