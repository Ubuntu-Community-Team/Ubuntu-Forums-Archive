---
title: "Xsane: No devices available"
date: 2019-02-17
forum: Hardware
---

### Post by knight69 on 2019-02-17
I have a Lexmark CX317dn printer/scanner that works perfectly with Windows, but I cannot use the scanner with Ubuntu 16.04. 

Xsane reports: no devices available. 

Scanimage -L reports: no scanners were identified.

Sane-find-scanner reports: found USB scanner (vendor=0x043d [Lexmark], product=0x022f [Lexmark CX317dn]) at libusb:003:003.

Running xsane with strace shows that xsane can locate and open the Lexmark config file and driver but near the end repeats the following many times: 
     poll([{fd=3, events=POLLIN|POLLPRI}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN}], 3, 0) = 0 (Timeout)
     recvmsg(6, 0x7ffd32d1e9b0, 0)           = -1 EAGAIN (Resource temporarily unavailable) 

Running xsane and sane as root gives the same results.

If anyone has the answer to this problem please let me know.

---

### Post by brian_p on 2019-02-18
> **knight69 said:**
> 
Scanimage -L reports: no scanners were identified.


SANE cannot find a backend for the device.

[https://ubuntuforums.org/showthread.php?t=2412674](https://ubuntuforums.org/showthread.php?t=2412674)

---

### Post by knight69 on 2019-02-19
At this point, I'm not sure what the back end is that it is looking for if it's not the driver.  According to strace, multiple system calls were made successfully to the lexmark driver.

[INDENT]open("/usr/lib/x86_64-linux-gnu/sane/libsane-lexmark.so.1", O_RDONLY) = 7
close(7)                                = 0
open("/usr/lib/x86_64-linux-gnu/sane/libsane-lexmark.so.1", O_RDONLY|O_CLOEXEC) = 7
read(7, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000,\0\0\0\0\0\0"..., 832) = 832
fstat(7, {st_mode=S_IFREG|0644, st_size=100992, ...}) = 0
mmap(NULL, 2206320, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 7, 0) = 0x7fcf2c660000
mprotect(0x7fcf2c678000, 2093056, PROT_NONE) = 0
mmap(0x7fcf2c877000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 7, 0x17000) = 0x7fcf2c877000
mmap(0x7fcf2c879000, 6768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcf2c879000
close(7)                      
[/INDENT]

What else is it looking for?

---

### Post by brian_p on 2019-02-20
Your negative 'Scanimage -L ' output is the strongest possible indication that SANE cannot find a driver (backend) to use.. You need to look at where the Lexmark package puts its libsane-* files or where they are linked to.

---

