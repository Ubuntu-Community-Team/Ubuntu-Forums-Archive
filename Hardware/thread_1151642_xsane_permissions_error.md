---
title: "xsane permissions error"
date: 2009-05-07
forum: Hardware
---

### Post by trendal.toews on 2009-05-07
Okay, just spent a couple hours with my printer (Brother MFC 210C)

It works great, including the scanner, but when I start xsane I get the permission denied failed to create file error.  I ran lsusb and my scanner is on Bus 005 Device 002. So I ran this

sudo chmod a+w /dev/bus/usb/005/002

but that didn't fix it.

Apparently xsane is trying to write a file to a folder I don't have permission to write to?  Is that correct?  If so what is the folder?

Thanks for the awesome help.  There is a literal ton of support for printer problems on Ubuntu Forums.  Its great.

---

### Post by trendal.toews on 2009-05-07
running 

strace /usr/bin/xsane

outputs this

Edit: That doesn't look like all of it...?  How do I select everything it putout.  I hit select all but if I scroll clear to the top it doesn't have my last input..?  Is this correct?



read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"(\0\4\0\3\0\340\3\\\2\0\0\0\0\0\0"..., 16}, {NULL, 0}, {""..., 0}], 3) = 16
select(6, [5], [], NULL, NULL)          = 1 (in [5])
read(5, "\1\1\350\0\0\0\0\0\3\0\340\3u\0u\0`\324}\0\0\0\0\0(\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
open("/usr/lib/libcanberra-0.11/libcanberra-pulse.la", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libcanberra-0.11/libcanberra-pulse.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libcanberra-0.11/libcanberra-alsa.la", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libcanberra-0.11/libcanberra-alsa.so", O_RDONLY) = 6
read(6, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\30\0\0\0\0\0\0@"..., 832) = 832
fstat(6, {st_mode=S_IFREG|0644, st_size=18696, ...}) = 0
mmap(NULL, 2113968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 6, 0) = 0x7ffc8a522000
mprotect(0x7ffc8a526000, 2093056, PROT_NONE) = 0
mmap(0x7ffc8a725000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 6, 0x3000) = 0x7ffc8a725000
close(6)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 6
fstat(6, {st_mode=S_IFREG|0644, st_size=67122, ...}) = 0
mmap(NULL, 67122, PROT_READ, MAP_PRIVATE, 6, 0) = 0x7ffc8a511000
close(6)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libasound.so.2", O_RDONLY) = 6
read(6, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\253\2\0\0\0\0\0@"..., 832) = 832
fstat(6, {st_mode=S_IFREG|0644, st_size=918112, ...}) = 0
mmap(NULL, 3013640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 6, 0) = 0x7ffc8a231000
mprotect(0x7ffc8a30a000, 2097152, PROT_NONE) = 0
mmap(0x7ffc8a50a000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 6, 0xd9000) = 0x7ffc8a50a000
close(6)                                = 0
mprotect(0x7ffc8a50a000, 12288, PROT_READ) = 0
mprotect(0x7ffc8a725000, 4096, PROT_READ) = 0
munmap(0x7ffc8a511000, 67122)           = 0
pipe([6, 7])                            = 0
futex(0x7ffc8ba9d1f8, FUTEX_WAKE_PRIVATE, 2147483647) = 0
mkdir("/home/tt/.cache", 0755)          = -1 EEXIST (File exists)
open("/var/lib/dbus/machine-id", O_RDONLY) = 8
fstat(8, {st_mode=S_IFREG|0644, st_size=33, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ffc946d9000
read(8, "d90ad58f6dc784957a11264a49d42671\n"..., 4096) = 33
close(8)                                = 0
munmap(0x7ffc946d9000, 4096)            = 0
open("/home/tt/.cache/event-sound-cache.tdb.d90ad58f6dc784957a11264a49d42671.x86_64-pc-linux-gnu", O_RDWR|O_CREAT|O_NOCTTY|O_CLOEXEC, 0644) = 8
fcntl(8, F_GETFD)                       = 0x1 (flags FD_CLOEXEC)
fcntl(8, F_SETFD, FD_CLOEXEC)           = 0
fcntl(8, F_SETLKW, {type=F_WRLCK, whence=SEEK_SET, start=0, len=1}) = 0
read(8, "TDB file\n\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0m"..., 168) = 168
fstat(8, {st_mode=S_IFREG|0644, st_size=8192, ...}) = 0
pread(8, "\0\0\0\0"..., 4, 44)          = 4
fcntl(8, F_SETLKW, {type=F_UNLCK, whence=SEEK_SET, start=0, len=1}) = 0
fcntl(8, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=368, len=1}) = 0
pread(8, "\270\37\0\0"..., 4, 372)      = 4
pread(8, "\0\0\0\0000\0\0\0%\0\0\0\4\0\0\0b\27\270\302\231\31\1&"..., 24, 8120) = 24
pread(8, "ubuntu\0window-new\0en_US.UTF-8\0ste"..., 37, 8144) = 37
pread(8, "\6\370\374I"..., 4, 8181)     = 4
fcntl(8, F_SETLKW, {type=F_UNLCK, whence=SEEK_SET, start=368, len=1}) = 0
stat("/home/tt/.local/share/sounds", 0x7fff9c8cec70) = -1 ENOENT (No such file or directory)
stat("/usr/local/share//sounds", 0x7fff9c8cec70) = -1 ENOENT (No such file or directory)
stat("/usr/share//sounds", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/share/gdm//sounds", 0x7fff9c8cec70) = -1 ENOENT (No such file or directory)
close(7)                                = 0
close(6)                                = 0
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"(\0\4\0\3\0\340\3\\\2\0\0\0\0\0\0"..., 16}, {NULL, 0}, {""..., 0}], 3) = 16
select(6, [5], [], NULL, NULL)          = 1 (in [5])
read(5, "\1\1\351\0\0\0\0\0\3\0\340\3u\0u\0`\324}\0\0\0\0\0(\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"(\0\4\0\3\0\340\3\\\2\0\0\0\0\0\0"..., 16}, {NULL, 0}, {""..., 0}], 3) = 16
select(6, [5], [], NULL, NULL)          = 1 (in [5])
read(5, "\1\1\352\0\0\0\0\0\3\0\340\3u\0u\0`\324}\0\0\0\0\0(\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\24\0\6\0\3\0\340\3\0\1\0\0\4\0\0\0\0\0\0\0\377\377\377\377"..., 24}, {NULL, 0}, {""..., 0}], 3) = 24
select(6, [5], [], NULL, NULL)          = 1 (in [5])
read(5, "\1 \353\0\0\0\0\0\4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\340\265=\3\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"*\2\3\0\4\0\340\3\266\321`\0+\0\1\0\24\0\6\0\3\0\340\3\372\0\0\0\6\0\0\0\0"..., 40}, {NULL, 0}, {""..., 0}], 3) = 40
select(6, [5], [], NULL, NULL)          = 1 (in [5])
read(5, "\n\2\354\0\3\0\340\3\0-E\0\0\0\0\0\360\317\361\304\377\177\0\0\200@}\0\0\0\0\0\t"..., 4096) = 132
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\222\3\4\0\5\0\340\3\0\0\0\0\323\343\224K"..., 16}, {NULL, 0}, {""..., 0}], 3) = 16
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5\30\4\0;\0\340\3\3\0\340\3i\1|\0\230\4\5\0<\0\340\3;\0\340\3'\2\0\0\0"..., 15580}, {"\0\0K\0\0\0L\0\0\200\35\0\0\0K\0\0\200\35\0\0\0L\0\0\200K\1\0\0K\0\0"..., 3200}, {""..., 0}], 3) = 18780
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5 \4\0T\0\340\3;\0\340\3\1\0\1\0\230\4\5\0U\0\340\3T\0\340\3%\2\0\0\0"..., 4492}, {NULL, 0}, {""..., 0}], 3) = 4492
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 479) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\2d\1\22\323`\0\\\2\0\0\3\0\340\3\0\0\0\0:\1\307\0\305\0R\0\20\0\0\2\7"..., 4096) = 64
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5\30\4\0Z\0\340\3\3\0\340\0035\1\35\0\230\4\5\0[\0\340\3Z\0\340\3'\2\0\0\0"..., 16144}, {NULL, 0}, {""..., 0}], 3) = 16144
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 499) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\0\230\1%\323`\0\\\2\0\0004\0\340\3\0\0\0\0C\1\343\0\264\0$\0\20\0\0\2\7"..., 4096) = 64
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5\30\4\0e\0\340\3\3\0\340\0035\1\35\0\230\4\5\0f\0\340\3e\0\340\3'\2\0\0\0"..., 16004}, {NULL, 0}, {""..., 0}], 3) = 16004
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 499) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\3\305\1W\323`\0\\\2\0\0\3\0\340\3\0\0\0\0E\1\361\0\320\0|\0\20\0\0\2"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\7\3\305\1\213\324`\0\\\2\0\0\3\0\340\3\0\0\0\0\206\1\344\0\21\1o\0\20\0\0\2"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 500) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\2\305\1\225\324`\0\\\2\0\0\3\0\340\3\0\0\0\0\203\1\325\0\16\1`\0\20\0\0\2\7"..., 4096) = 64
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5\30\4\0m\0\340\3\3\0\340\0035\1\35\0\230\4\5\0n\0\340\3m\0\340\3'\2\0\0\0"..., 16004}, {NULL, 0}, {""..., 0}], 3) = 16004
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 499) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\0\362\1\263\324`\0\\\2\0\0004\0\340\3\0\0\0\0\200\1\276\0\361\0\377\377\20\0\0\2\7"..., 4096) = 64
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5\30\4\0u\0\340\3\3\0\340\0035\1\35\0\230\4\5\0v\0\340\3u\0\340\3'\2\0\0\0"..., 16004}, {NULL, 0}, {""..., 0}], 3) = 16004
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 500) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\3\37\2\30\326`\0\\\2\0\0\3\0\340\3\0\0\0\0\336\1\202\0i\1\r\0\20\0\0\2"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 \37\2\3\0\340\3\362\0\0\0\377\0\0\0\256\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\256\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\7\3 \2u\330`\0\\\2\0\0\3\0\340\3\0\0\0\0\335\1w\0h\1\2\0\20\0\0\2"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 500) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\10\3 \2\331\330`\0\\\2\0\0\3\0\340\3\0\0\0\0\327\1\366\0b\1\201\0\20\0\0\2"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\n\3 \2\4\0\340\3\0-E\0\0\0\0\0\360\317\361\304\377\177\0\0\200@}\0\0\0\0\0\n"..., 4096) = 64
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, 0) = 0 (Timeout)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"5\30\4\0}\0\340\3\3\0\340\0035\1\35\0\230\4\5\0~\0\340\3}\0\340\3'\2\0\0\0"..., 12396}, {NULL, 0}, {""..., 0}], 3) = 12396
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 K\2\3\0\340\3\362\0\0\0\377\0\0\0\257\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\257\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 L\2\3\0\340\3\362\0\0\0\377\0\0\0\260\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\260\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 M\2\3\0\340\3\362\0\0\0\377\0\0\0\261\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\261\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 N\2\3\0\340\3\362\0\0\0\377\0\0\0\262\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\262\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 O\2\3\0\340\3\362\0\0\0\377\0\0\0\263\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\263\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 P\2\3\0\340\3\362\0\0\0\377\0\0\0\264\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\264\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\34\320Q\2\3\0\340\3f\1\0\0DPa\0\0\0\0\0\0\0\0\0\4\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\34\320Q\2\3\0\340\3f\1\0\0\226Pa\0\0\0\0\0\0\0\0\0\4\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\34\320Q\2\3\0\340\3f\1\0\0\371Pa\0\0\0\0\0\0\0\0\0\4\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 Q\2\3\0\340\3\362\0\0\0\377\0\0\0\265\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\265\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 R\2\3\0\340\3\362\0\0\0\377\0\0\0\266\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\266\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 S\2\3\0\340\3\362\0\0\0\377\0\0\0\267\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\267\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 T\2\3\0\340\3\362\0\0\0\377\0\0\0\270\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\270\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 U\2\3\0\340\3\362\0\0\0\377\0\0\0\271\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\271\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 V\2\3\0\340\3\362\0\0\0\377\0\0\0\272\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\272\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 W\2\3\0\340\3\362\0\0\0\377\0\0\0\273\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\273\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1) = 1 ([{fd=5, revents=POLLIN}])
read(5, "\241 X\2\3\0\340\3\362\0\0\0\377\0\0\0\274\4\0\0\3\0\340\3\0\0\0\0\0\0\0\0"..., 4096) = 32
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(6, [5], [5], NULL, NULL)         = 1 (out [5])
writev(5, [{"\31\0\v\0\\\2\0\0\0\0\30\0! \0\0\\\2\0\0\362\0\0\0\377\0\0\0\274\4\0\0\3"..., 44}, {NULL, 0}, {""..., 0}], 3) = 44
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0xa2c324, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}], 2, -1

---

### Post by northwestuntu on 2009-05-07
i also can't get my 210c to work.  was working fine in 8.10, but since my upgrade i can't get the scanner to work.

---

### Post by trendal.toews on 2009-05-07
Oh my scanner works fine thats not the problem.  My problem is giving xsane the permission it needs.

Have a look at [this]("http://ubuntuforums.org/showthread.php?t=590793") page.  I was running through this but didn't make it all the way because I think this page is not for jaunty but it got my printer/scanner going fine.

---

