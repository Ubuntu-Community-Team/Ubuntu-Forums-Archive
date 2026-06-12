---
title: "Touchscreen / Xorg problem"
date: 2012-05-15
forum: Hardware
---

### Post by Tokalima on 2012-05-15
Hi,

I’m using a Galaxy Touch screen with eGalaxTouch driver and the TKCal calibration tool on Ubuntu 8.04 systems which is working quite well. I’m trying to use it in two ways, one of them is working fine, the other fails.  And no, there is no way to update the systems...
 
Method 1: 
I want to do the calibration as root, so I start an xterm in my X-Window session and execute: 
-    su –-l 
-    export DISPLAY=:0.0 
-    export XAUTHORITY=/home/user/.Xauthority 
-    TKCal /dev/usb/hiddev0 Cal 
Everything works as expected. It is also possible to start the more advanced "eGalaxTouch" utility this way.
 
Method 2: 
I want to start the calibration tool from another console and then switch to the X-Session to do the calibration. Background: There usually is a firefox running in kioskmode on the X-Session and there is no way to log into the system and run a command.
-    Press <STRG><ALT>-<F1> to switch to a console 
-    Login as root 
-    export DISPLAY=:0.0 
-    export XAUTHORITY=/home/user/.Xauthority 
-    TKCal /dev/usb/hiddev0 Cal 
This fails with: 
ERROR: No device /dev/usb/hiddev0 found.  
Please make sure the X module is installed. 

The device hiddev0 is available. Opening an xterm or any other x-client this way is working well, it seems that the TKCal tool can't access the eGalaxTouch driver. The tool "eGalaxTouch" appears on the X-Session with the message "No Touch Controller found." 
 
 
Strace gives the following: 
------- 
execve("/usr/bin/TKCal", ["TKCal", "/dev/usb/hiddev0", "Cal"], [/* 22 vars */]) = 0 
brk(0)                                  = 0x805d000 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7731000 
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory) 
open("/etc/ld.so.cache", O_RDONLY)      = 3 
fstat64(3, {st_mode=S_IFREG|0644, st_size=35982, ...}) = 0 
mmap2(NULL, 35982, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7728000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20H\0\000"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0755, st_size=112354, ...}) = 0 
mmap2(NULL, 94688, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7710000 
mmap2(0xb7724000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7724000 
mmap2(0xb7726000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7726000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2604\1"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=944876, ...}) = 0 
mmap2(NULL, 944852, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7629000 
mmap2(0xb770d000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe4) = 0xb770d000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libXinerama.so.1", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\7\0"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=6464, ...}) = 0 
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7628000 
mmap2(NULL, 9308, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7625000 
mmap2(0xb7627000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7627000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`*\4\000"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=970680, ...}) = 0 
mmap2(NULL, 993036, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7532000 
mmap2(0xb761a000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe = 0xb761a000 
mmap2(0xb761f000, 22284, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb761f000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@4\0\000"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=149328, ...}) = 0 
mmap2(NULL, 147584, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb750d000 
mmap2(0xb7530000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb7530000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\31\0\000"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=42700, ...}) = 0 
mmap2(NULL, 41700, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7502000 
mmap2(0xb750c000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xb750c000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260e\1"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0755, st_size=1364388, ...}) = 0 
mmap2(NULL, 1369712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb73b3000 
mmap2(0xb74fc000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x149) = 0xb74fc000 
mmap2(0xb74ff000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb74ff000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libxcb-xlib.so.0", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\6\0"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=4172, ...}) = 0 
mmap2(NULL, 7056, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb73b1000 
mmap2(0xb73b2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0) = 0xb73b2000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libxcb.so.1", O_RDONLY)  = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240z\0"..., 512) = 512 
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb73b0000 
fstat64(3, {st_mode=S_IFREG|0644, st_size=93832, ...}) = 0 
mmap2(NULL, 96736, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7398000 
mmap2(0xb73af000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0xb73af000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\n\0\000"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0 
mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7394000 
mmap2(0xb7396000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7396000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libXext.so.6", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220*\0"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=56156, ...}) = 0 
mmap2(NULL, 55228, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7386000 
mmap2(0xb7393000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd) = 0xb7393000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\10"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=6988, ...}) = 0 
mmap2(NULL, 9928, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7383000 
mmap2(0xb7385000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7385000 
close(3)                                = 0 
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory) 
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3 
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \16\0\000"..., 512) = 512 
fstat64(3, {st_mode=S_IFREG|0644, st_size=16616, ...}) = 0 
mmap2(NULL, 19544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb737e000 
mmap2(0xb7382000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7382000 
close(3)                                = 0 
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb737d000 
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb737c000 
set_thread_area({entry_number:-1 -> 6, base_addr:0xb737c6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0 
mprotect(0xb74fc000, 4096, PROT_READ)   = 0 
mprotect(0xb761a000, 12288, PROT_READ)  = 0 
munmap(0xb7728000, 35982)               = 0 
set_tid_address(0xb737c70             = 8768 
set_robust_list(0xb737c710, 0xc)        = 0 
futex(0xbf962600, 0x81 /* FUTEX_??? */, 1) = 0 
rt_sigaction(SIGRTMIN, {0xb77142c0, [], SA_SIGINFO}, NULL,  = 0 
rt_sigaction(SIGRT_1, {0xb7714340, [], SA_RESTART|SA_SIGINFO}, NULL,  = 0 
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL,  = 0 
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0 
uname({sys="Linux", node="buggy-SSD", ...}) = 0 
shmget(0x52c, 1492, IPC_CREAT|0666)     = 1835033 
shmat(1835033, 0, 0)                    = 0xb7730000 
fstat64(1, {st_mode=S_IFREG|0644, st_size=8659, ...}) = 0 
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb772f000 
write(1, "ERROR: No device /dev/usb/hiddev"..., 85ERROR: No device /dev/usb/hiddev0 found. 
Please make sure the the X module is installed. 
) = 85 
exit_group(0)                           = ? 
Process 8768 detached 
------- 
 
 
Your help is greatly appreciated. 
 
Thanks and regards,
Tokalima

---

