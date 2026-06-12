---
title: "escputil hangs...help!"
date: 2011-06-13
forum: Hardware
---

### Post by jmborr on 2011-06-13
Dear Ubuntu users,

I have an EPSON CX4800 printer. I installed escputil but it just hangs.

The first trouble is that I can't run escputil as single user:
```
*groups jmborr*
jmborr : jmborr adm **lp** dialout cdrom plugdev users **lpadmin** admin sambashare
*ll /dev/usb|grep lp0*
crw-rw----  1 root lp   180, 0 2011-06-13 14:11 lp0
*escputil --new --raw-device=/dev/usb/lp0 --ink-level*
Escputil version 5.2.6, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

**Cannot open /dev/usb/lp0 read/write: Permission denied**
```

Running as root, it just hangs
```
*sudo escputil --new --raw-device=/dev/usb/lp0 --ink-level*
Escputil version 5.2.6, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.
...

```

Running a trace the program stops in a write statement, but I ignore what it means :)
```
*sudo strace escputil --new --raw-device=/dev/usb/lp0 --ink-level*
...
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7856000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7856000, 4096)                = 0
open("/usr/share/locale/en_US/LC_MESSAGES/gutenprint.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/gutenprint.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/gutenprint.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/gutenprint.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/dev/usb/lp0", O_RDWR)            = 3
rt_sigaction(SIGALRM, {0x8059fe0, [ALRM], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
alarm(5)                                = 0
write(3, "\33\1@EJL ID\r\n", 11)        = -1 EINTR (Interrupted system call)
--- SIGALRM (Alarm clock) @ 0 (0) ---
sigreturn()                             = ? (mask now [])
nanosleep({0, 10000000}, NULL)          = 0
write(3, "\33\1@EJL ID\r\n", 11
...

```

Any help is greatly appreciated
Jose

---

### Post by shanksi on 2011-07-22
I'm getting exactly the same thing. Anyone know what the problem is?

---

