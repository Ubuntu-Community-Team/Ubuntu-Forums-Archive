---
title: "[SOLVED] HP Pavilion dv6580/USB and modprobe problems"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by m4cph15t0 on 2007-08-19
Hi,

I'm running Ubuntu on Pavilion dv6580 laptop and I have problem with usb devices. When I plug in a usb-stick, system doesn't create a devide for it (so automount can't mount it, etc.). When the device is plugged in during boot, everything seems to work fine a later when I plug in new stuff, devices are created properly.

I spotted that in the second case module usb-storage is loaded in the kernel. When I dont boot with usb device plugged in and try modprobe usb-storage later on, modprobe hangs and can't even be killed. This happens with all usb-related modules like ehci_hcd, for example.

I had this problem on Fiesty, so I switched to Gutsy Tribe 4, hoping new kernel and libs may possibly solve the problem. Now I have 2.6.22-9-386 kernel now, but it didn't work with 2.6.18 neither. 

'strace modprobe usb-storage' stops here:
```

open("/lib/modules/2.6.22-9-386/kernel/drivers/usb/storage/libusual.ko", O_RDWR) = 3
fcntl64(3, F_SETLKW, {type=F_WRLCK, whence=SEEK_SET, start=0, len=1}) = 0
open("/proc/modules", O_RDONLY)         = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f7a000
read(4, "ipv6 257572 8 - Live 0xf8d48000\n"..., 1024) = 1024
read(4, "r_oss 16896 2 snd_pcm_oss, Live "..., 1024) = 1024
read(4, " 0xf89b3000\nbluetooth 51684 1 hc"..., 1024) = 1024
read(4, "- Live 0xf88c1000\nforcedeth 4864"..., 1024) = 548
read(4, "", 1024)                       = 0
close(4)                                = 0
munmap(0xb7f7a000, 4096)                = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=36032, ...}) = 0
mmap2(NULL, 36032, PROT_READ|PROT_WRITE, MAP_PRIVATE, 3, 0) = 0xb7f72000
init_module(0xb7f72000, 36032, ""

```

After plugging new device in dmesg says just:
```

[ 4594.852000] usb 2-1: new high speed USB device using ehci_hcd and address 6
[ 4594.988000] usb 2-1: configuration #1 chosen from 1 choice

```

... and then nothing... Probably hangs on loading modules.

Could you pls suggest me something? This worked like a charm with life CDs.

---

### Post by EXCiD3 on 2007-08-19
what boot parameters are you using? Only using noapic will disable usb support. See this thread for a little more information: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by m4cph15t0 on 2007-08-20
I experimented with noapic and nolapic, but as they didn't help I don'tuse any special boot parameters at the moment.

```
title       Ubuntu, kernel 2.6.22-9-386
root        (hd0,1)
kernel      /vmlinuz-2.6.22-9-386 root=UUID=3b8f6c21-3c2b-4131-8e11-a78ae22b20ca ro quiet
initrd      /initrd.img-2.6.22-9-386
quiet
```

I thought something is blocking loading further kernel modules, but now I tryed strace lsusb, which also ends up hanging. This is output:

```
strace lsusb
execve("/usr/sbin/lsusb", ["lsusb"], [/* 19 vars */]) = 0
brk(0)                                  = 0x805d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f0c000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=62590, ...}) = 0
mmap2(NULL, 62590, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7efc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=80504, ...}) = 0
mmap2(NULL, 83232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ee7000
mmap2(0xb7efb000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7efb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libusb-0.1.so.4", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\21\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=28376, ...}) = 0
mmap2(NULL, 31320, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7edf000
mmap2(0xb7ee5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5) = 0xb7ee5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260a\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1339816, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ede000
mmap2(NULL, 1349136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d94000
mmap2(0xb7ed8000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x143) = 0xb7ed8000
mmap2(0xb7edb000, 9744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7edb000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d93000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7d936b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7ed8000, 4096, PROT_READ)   = 0
munmap(0xb7efc000, 62590)               = 0
brk(0)                                  = 0x805d000
brk(0x807e000)                          = 0x807e000
open("./usb.ids", O_RDONLY)             = -1 ENOENT (No such file or directory)
open("/var/lib/misc/usb.ids", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=58046, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f0b000
read(3, "\37\213\10\0\0\0\0\0\2\3\214}\353r\333H\222\356o\373)j"..., 16384) = 16384
_llseek(3, 0, [16384], SEEK_CUR)        = 0
read(3, "\333\354\207f\352g\220A\252\221m\1\247X\26(\302\263\302"..., 16384) = 16384
brk(0x809f000)                          = 0x809f000
read(3, "t\300r\273.p\272L:\26\37^\356\252\234t\230 \374eqX\271"..., 16384) = 16384
read(3, "\360\27\250;\374\225\217r\311\200\'\31F\4K\312\253\340"..., 16384) = 8894
read(3, "", 4096)                       = 0
brk(0x80c0000)                          = 0x80c0000
read(3, "", 16384)                      = 0
close(3)                                = 0
munmap(0xb7f0b000, 4096)                = 0
open("/dev/bus/usb", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=80, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 4 entries */, 4096)      = 64
close(3)                                = 0
open("/dev/bus/usb", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=80, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 4 entries */, 4096)      = 64
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
open("/dev/bus/usb/001", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=100, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 5 entries */, 4096)      = 80
open("/dev/bus/usb/001/003", O_RDWR)    = 4
ioctl(4, USBDEVFS_CONNECTINFO, 0xbf819184) = 0
read(4, "\22\1\0\2\0\0\0\10m\4\31\300\0C\1\2\0\1", 18) = 18
read(4, "\t\2\"\0\1\1\0\240", 8)        = 8
read(4, "2\t\4\0\0\1\3\1\2\0\t!\21\1\0\1\"7\0\7\5\201\3\5\0\n", 26) = 26
close(4)                                = 0
open("/dev/bus/usb/001/004", O_RDWR)    = 4
ioctl(4, USBDEVFS_CONNECTINFO, 0xbf819184) = 0
read(4, "\22\1\20\1\377\377\377\10\377\10\200%#\6\0\1\0\1", 18) = 18
read(4, "\t\2 \0\1\1\0\240", 8)         = 8
read(4, "2\t\4\0\0\2\377\377\377\0\7\5\201\2 \0\0\7\5\2\2\10\0\0"..., 24) = 24
close(4)                                = 0
open("/dev/bus/usb/001/001", O_RDWR)    = 4
ioctl(4, USBDEVFS_CONNECTINFO, 0xbf819184) = 0
read(4, "\22\1\20\1\t\0\0@\0\0\0\0\6\2\3\2\1\1", 18) = 18
read(4, "\t\2\31\0\1\1\0\340", 8)       = 8
read(4, "\0\t\4\0\0\1\t\0\0\0\7\5\201\3\2\0\377", 17) = 17
close(4)                                = 0
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
open("/dev/bus/usb/001/003", O_RDWR)    = 3
ioctl(3, USBDEVFS_IOCTL, 0xbf81b11c)    = -1 ENOTTY (Inappropriate ioctl for device)
close(3)                                = 0
open("/dev/bus/usb/001/004", O_RDWR)    = 3
ioctl(3, USBDEVFS_IOCTL, 0xbf81b11c)    = -1 ENOTTY (Inappropriate ioctl for device)
close(3)                                = 0
open("/dev/bus/usb/001/001", O_RDWR)    = 3
ioctl(3, USBDEVFS_IOCTL, 0xbf81b11c)    = 11
close(3)                                = 0
open("/dev/bus/usb/002", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=80, ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
getdents(3, /* 4 entries */, 4096)      = 64
open("/dev/bus/usb/002/001", O_RDWR)    = 4
ioctl(4, USBDEVFS_CONNECTINFO, 0xbf819184) = 0
read(4, "\22\1\0\2\t\0\1@\0\0\0\0\6\2\3\2\1\1", 18) = 18
read(4, "\t\2\31\0\1\1\0\340", 8)       = 8
read(4, "\0\t\4\0\0\1\t\0\0\0\7\5\201\3\4\0\f", 17) = 17
close(4)                                = 0
open("/dev/bus/usb/002/002", O_RDWR)    = 4
ioctl(4, USBDEVFS_CONNECTINFO

```

Also I forgot to mention I have 2xAMD64.

---

### Post by m4cph15t0 on 2007-08-25
I've finally solved this problem.

All this strange behaviour was caused by uvcvideo module (driver for built-in camera), which failed to load at boot time and ruined the whole system. When usb device was connected during boot, usb-related modules were loaded properly before this error and usb was functional afterwards. 

I blacklisted uvcvideo module in my /etc/modprobe.d/blaclist file, rebooted and all problems are gone.

---

### Post by blumagic on 2008-03-19
I have been looking for a solution to this problem for about a week now. I have loaded and unloaded gutsy, feisty and dapper several times on my new HP dv9700 laptop. I have even tried fedora8. Now that I have found your post, lsusb and modprobe are working fine now. I also was getting, hald-addon-usr-csr, hanging and showing up as uninterruptable. I really appreciate your solution. One other thing, did you ever get you web cam working after blacklisting the uvcvideo module?

thanks,
blu.....

---

### Post by mjpca on 2008-03-20
This worked for me as well.  Thanks for the solution.  Has anyone posted this as a bug?  Still seems to be happening in the hardy alpha files.  I have a dv9700 as well.

---

### Post by watagan on 2008-04-10
I am running openSUSE, but there is an "r200" version of the uvcvideo driver that works ok on the 9700 without borking the usb mass storage. Have no idea how to install this on Ubuntu, but it may offer you some hope. Regards...

---

