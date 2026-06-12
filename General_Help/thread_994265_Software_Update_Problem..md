---
title: "Software Update Problem."
date: 2008-11-26
forum: General Help
---

### Post by kezdetj on 2008-11-26
Has this happened to anyone else?  Update Manager downloaded a raft of updates, and now OpenOffice won't launch!  I get a notification window that says "The application cannot be started."  Any ideas anyone?

---

### Post by Wayne_V on 2008-11-26
Try "oowriter" at a shell prompt and see if you get any more descriptive error messages.

---

### Post by kezdetj on 2008-11-26
That got me the exact same error as before.:mad:

---

### Post by Wayne_V on 2008-11-26
All I can think to try is to trace it:

$ strace /usr/lib/openoffice/program/soffice -writer

(note - may have to 'sudo apt-get install strace' first)

---

### Post by kezdetj on 2008-11-28
Here's a paste of the strace output:

execve("/usr/lib/openoffice/program/", ["/usr/lib/openoffice/program/", "-scalc"], [/* 35 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ef2000
_llseek(3, 0, 0xbfe0f64c, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32strace: exec: Permission denied
) = 32
close(3)                                = 0
munmap(0xb7ef2000, 4096)                = 0
exit_group(1)                           = ?
Process 21860 detached

---

### Post by Wayne_V on 2008-11-28
The strace should start out with:

> $ strace /usr/lib/openoffice/program/soffice -scalc
execve("/usr/lib/openoffice/program/soffice", ["/usr/lib/openoffice/program/soff"..., "-scalc"], [/* 36 vars */]) = 0
brk(0)                                  = 0x9dc0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb80c4000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=68336, ...}) = 0
mmap2(NULL, 68336, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb80b3000
close(3)                                = 0


Is that the command you ran?   What do you get from  "$ ls -l /usr/lib/openoffice/program/soffice"

---

### Post by kezdetj on 2008-11-28
Permissions for everything in that directory are:
root - rwx
group - r-x
other - r-x

That's what confuses me.  The permissions seem correct for all the executables associated with Open Office, and all of this started when Ubuntu published and made available some "Security Updates" tied to Open Office.  Once those downloaded and installed, OO stopped working, even at the root user level.

---

### Post by Wayne_V on 2008-11-28
Look at the execve line in your strace output:
execve("/usr/lib/openoffice/program/", ["/usr/lib/openoffice/program/", "-scalc"], [/* 35 vars */]) = -1 EACCES (Permission denied)

It says "/usr/lib/openoffice/program", which is a directory, not an executable.

It should be:

execve("/usr/lib/openoffice/program/soffice", ["/usr/lib/openoffice/program/soff"..., "-scalc"], [/* 36 vars */]) = 0

What was the exact strace command you ran?

---

### Post by kezdetj on 2008-11-29
Sorry for the long waits between replies.  I work 10 hour days.  Anyway, below is a paste of the whole thing.



kezdeth@Poledra:~$ strace /usr/lib/openoffice/program/ -scalc
execve("/usr/lib/openoffice/program/", ["/usr/lib/openoffice/program/", "-scalc"], [/* 34 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fd9000
_llseek(3, 0, 0xbf8f5fec, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32strace: exec: Permission denied
) = 32
close(3)                                = 0
munmap(0xb7fd9000, 4096)                = 0
exit_group(1)                           = ?
Process 7392 detached
kezdeth@Poledra:~$

---

### Post by kezdetj on 2008-11-29
And the result as root:


root@Poledra:~# strace /usr/lib/openoffice/program/ -scalc
execve("/usr/lib/openoffice/program/", ["/usr/lib/openoffice/program/", "-scalc"], [/* 14 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb8067000
_llseek(3, 0, 0xbff82d5c, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32strace: exec: Permission denied
) = 32
close(3)                                = 0
munmap(0xb8067000, 4096)                = 0
exit_group(1)                           = ?
Process 25178 detached

---

### Post by zika on 2008-11-29
> **kezdetj said:**
> Has this happened to anyone else?  Update Manager downloaded a raft of updates, and now OpenOffice won't launch!  I get a notification window that says "The application cannot be started."  Any ideas anyone?

Try removing openoffice.org-gnome.

It is  a known issue. Backport is down (broken) just because of incompatibilities of OO with gnome, as I understood.

There are several threads about this on Forums.

---

### Post by kezdetj on 2008-11-29
zika:

Thank you tons!  That fixed the whole issue!

---

### Post by zika on 2008-11-29
> **kezdetj said:**
> zika:

Thank you tons!  That fixed the whole issue!

Great! I am not that lucky. My OpenOffice3.0 is missing in action ... There is a whole thread about that[ http://ubuntuforums.org/showthread.php?t=987181]("http://ubuntuforums.org/showthread.php?t=987181&goto=newpost") and, up to now, no solution ...

---

### Post by Wayne_V on 2008-11-30
FYI - this is  wrong:

# strace /usr/lib/openoffice/program/ -scalc

It needs to be

# strace /usr/lib/openoffice/program/soffice -scalc

You cannot execute a directory .....

---

