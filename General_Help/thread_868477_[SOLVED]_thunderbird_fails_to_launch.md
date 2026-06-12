---
title: "[SOLVED] thunderbird fails to launch"
date: 2008-07-23
forum: General Help
---

### Post by drevicko on 2008-07-23
I have been using thunderbird for ages, and recently, it stopped launching - rather, it makes an attempt to launch, then disappears. Interestingly, a new user goes into the new profile wizard, but when the wizard finishes, nothing happens (I guess it tries to launch the main program, but fails).

I'm using:

Kubuntu 8.04 (hardy)
thunderbird_2.0.0.14+nobinonly-0ubuntu0.8.04.1_i386.deb

I tried re-installing (apt-get uninstall then apt-get install, also tried apt-get purge) and removing my profile, but the same thing happens.

The problem started happening when I moved office and was without ethernet for half a day. I usually keep thunderbird open, so it launches on startup - when it tried to launch without the network, it failed, and has failed ever since.

The strace below complains about /usr/lib/thunderbird/init.d and init.d in my home folder not existing, but reintstalling didn't create these, so I guess it shouldn't be a problem. 

I can see no errors in the strace...

Here's the strace of a launch launch attempt - I'm not aware of any extensions, but I thought I'd use safe-mode just in case:

```
ian@OntoIan:~$ strace thunderbird -safe-mode
execve("/usr/bin/thunderbird", ["thunderbird", "-safe-mode"], [/* 34 vars */]) = 0
brk(0)                                  = 0x805e000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f9e000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=64539, ...}) = 0
mmap2(NULL, 64539, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f8e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260e\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1364388, ...}) = 0
mmap2(NULL, 1369712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e3f000
mmap2(0xb7f88000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x149) = 0xb7f88000
mmap2(0xb7f8b000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f8b000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e3e000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7e3e6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f88000, 4096, PROT_READ)   = 0
munmap(0xb7f8e000, 64539)               = 0
getpid()                                = 6641
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
geteuid32()                             = 1000
brk(0)                                  = 0x805e000
brk(0x807f000)                          = 0x807f000
getppid()                               = 6640
stat64("/home/ian", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/bin/thunderbird", O_RDONLY)  = 3
fcntl64(3, F_DUPFD, 10)                 = 10
close(3)                                = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {0x8055a30, ~[RTMIN RT_1], 0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, NULL, 8) = 0
read(10, "#!/bin/sh\n#\n# ***** BEGIN LICENS"..., 8192) = 5223
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6642
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/usr/bin\n", 128)              = 9
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6642
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6643
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6643
stat64("/usr/bin/run-mozilla.sh", 0xbfdfe7b8) = -1 ENOENT (No such file or directory)
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6644
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "/home/ian\n", 128)             = 10
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6644
lstat64("/usr/bin/thunderbird", {st_mode=S_IFLNK|0777, st_size=30, ...}) = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6645
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6645
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6646
close(4)                                = 0
read(3, "/usr/bin\n", 128)              = 9
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6646
chdir("/usr/bin")                       = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6647
close(4)                                = 0
read(3, "../lib/thunderbird/thunderbird\n", 128) = 31
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6647
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6650
close(4)                                = 0
read(3, "thunderbird\n", 128)           = 12
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6650
stat64("../lib/thunderbird/thunderbird", {st_mode=S_IFREG|0755, st_size=5223, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 12
getgroups32(12, [4, 20, 24, 25, 29, 30, 44, 46, 107, 109, 114, 1000]) = 12
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6651
close(4)                                = 0
read(3, "../lib/thunderbird\n", 128)    = 19
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6651
stat64("../lib/thunderbird/run-mozilla.sh", {st_mode=S_IFREG|0755, st_size=10492, ...}) = 0
geteuid32()                             = 1000
getgid32()                              = 1000
getegid32()                             = 1000
getgroups32(0, NULL)                    = 12
getgroups32(12, [4, 20, 24, 25, 29, 30, 44, 46, 107, 109, 114, 1000]) = 12
chdir("/usr/lib/thunderbird")           = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6652
close(4)                                = 0
read(3, "/usr/lib/thunderbird\n", 128)  = 21
read(3, "", 128)                        = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6652
chdir("/home/ian")                      = 0
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6653
--- SIGCHLD (Child exited) @ 0 (0) ---
close(4)                                = 0
read(3, "1\n", 128)                     = 2
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6653
open("/usr/lib/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = -1 ENOENT (No such file or directory)
open("/home/ian/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/thunderbird/init.d/S*", 0xbfdfe558) = -1 ENOENT (No such file or directory)
stat64("/home/ian/.thunderbird/init.d/S*", 0xbfdfe558) = -1 ENOENT (No such file or directory)
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e3e6f8) = 6654
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6654
--- SIGCHLD (Child exited) @ 0 (0) ---
open("/home/ian/.thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = -1 ENOENT (No such file or directory)
open("/usr/lib/thunderbird/init.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = -1 ENOENT (No such file or directory)
stat64("/home/ian/.thunderbird/init.d/K*", 0xbfdfe558) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/thunderbird/init.d/K*", 0xbfdfe558) = -1 ENOENT (No such file or directory)
exit_group(0)                           = ?
Process 6641 detached
ian@OntoIan:~$
```

---

### Post by drevicko on 2008-07-25
Solved (-:

the problem was that I had 2 monitors in the previous office, and had gone to one monitor. It seems that Thunderbird was launching on the other monitor, and was invisible (duh!). After adding the second monitor, everything works fine.

The Xserver also had nasty problems - the ATI driver didn't seem to like being told to use 2 screens when only one was found..

This post talks about the 'Big-Desktop' setup I was using:

[http://ubuntuforums.org/showthread.php?p=1773544#post1773544](http://ubuntuforums.org/showthread.php?p=1773544#post1773544)

---

