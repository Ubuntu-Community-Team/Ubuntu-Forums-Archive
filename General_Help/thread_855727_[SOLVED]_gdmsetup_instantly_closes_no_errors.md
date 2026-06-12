---
title: "[SOLVED] gdmsetup instantly closes no errors"
date: 2008-07-10
forum: General Help
---

### Post by jerome1232 on 2008-07-10
if I open gdmsetup whether it be gui (system>>admin>>login window) or terminal (gksudo gdmsetup) it will prompt me for pw, then open the window and instantly close it, no errors are spit out when launched via terminal.
I have tried ctrl-alt-f1

sudo /etc/init.d/gdm stop
sudo aptitude reinstall gdm

that ran through and gave an error calling some init-rc.d? script (don't know how to grab the output from a virtual terminal)

sudo /etc/init.d/gdm start

poped open a terminal and

gksudo gdmsetup

still exits with no errors spit out. any help would be great even if it involves wiping some settings :(

---

### Post by jerome1232 on 2008-07-10
output of kern.log this is what happens when i open it

Jul 10 16:10:34 ubuntu kernel: [  322.990532] gdmsetup[6316]: segfault at 0 rip 0 rsp 7fff68e0f738 error 14
Jul 10 16:14:34 ubuntu kernel: [  442.338699] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 10 16:14:34 ubuntu kernel: [  442.338715] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 10 16:14:34 ubuntu kernel: [  442.338729] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 10 16:14:59 ubuntu kernel: [  463.807675] gdmsetup[6897]: segfault at 0 rip 0 rsp 7ffff318aaa8 error 14
Jul 10 16:17:33 ubuntu kernel: [  541.583641] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 10 16:17:33 ubuntu kernel: [  541.583657] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 10 16:17:33 ubuntu kernel: [  541.583671] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode


output of auth.log this also is what happens when i open it

Jul 10 16:17:32 ubuntu gdm[6609]: pam_unix(gdm:session): session closed for user jeremy
Jul 10 16:17:39 ubuntu gdm[6985]: pam_smbpass(gdm:auth): unrecognized option [missingok]
Jul 10 16:17:39 ubuntu gdm[6985]: pam_unix(gdm:session): session opened for user jeremy by (uid=0)
Jul 10 16:30:38 ubuntu sudo: pam_smbpass(sudo:auth): unrecognized option [missingok]
Jul 10 16:30:38 ubuntu sudo:   jeremy : TTY=unknown ; PWD=/home/jeremy ; USER=root ; COMMAND=/usr/sbin/gdmsetup
Jul 10 16:30:38 ubuntu sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Jul 10 16:30:38 ubuntu sudo: pam_unix(sudo:session): session closed for user root

---

### Post by jerome1232 on 2008-07-10
bumpity bump

---

### Post by jerome1232 on 2008-07-12
hopeful bump.

---

### Post by jerome1232 on 2008-07-12
here is the output of strace (the last bit)
```
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)
nanosleep({0, 1000000}, NULL)           = 0
writev(10, [{"GIOP\1\2\1\0\231\0\0\0", 12}, {"\10\302>\n\3\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0<\2|\200\201"..., 153}], 2) = 165
poll([{fd=6, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}], 4, -1) = 1
read(10, "GIOP\1\2\1\1Z\0\0\0", 12)     = 12
read(10, "\10\302>\n\0\0\0\0\1\0\0\0\1\0\0\0\f\0\0\0\1\1\1\1\1\0"..., 90) = 90
wait4(8714, 0x7fff0a3ec66c, WNOHANG, NULL) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
stat("/sys", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
open("/proc/stat", O_RDONLY)            = 16
read(16, "cpu  183663 3491 38580 1399473 9"..., 8191) = 1243
close(16)                               = 0
stat("/proc/8714", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
open("/proc/8714/stat", O_RDONLY)       = 16
read(16, "8714 (gdmsetup) R 8713 8714 8714"..., 8191) = 222
close(16)                               = 0
nanosleep({0, 100000000}, NULL)         = 0
wait4(8714, 0x7fff0a3ec66c, WNOHANG, NULL) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\1\0\n\0!\0 \5\210\1\0\0\234\377\234\377\1\0\1\0\0\0\0"..., 180}], 1) = 180
read(3, 0x6277f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(15, 0x7fff0a3ee680, 255)           = -1 EAGAIN (Resource temporarily unavailable)
wait4(8714, [{WIFSIGNALED(s) && WTERMSIG(s) == SIGSEGV}], 0, NULL) = 8714
--- SIGCHLD (Child exited) @ 0 (0) ---
unlink("/tmp/libgksu-O28IHH/.Xauthority") = 0
rmdir("/tmp/libgksu-O28IHH")            = 0
writev(12, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
close(12)                               = 0
writev(10, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
close(10)                               = 0
close(9)                                = 0
close(8)                                = 0
unlink("/tmp/orbit-jeremy/linc-2209-0-73287d94801e6") = 0
close(11)                               = 0
exit_group(0)                           = ?
```
[B]
read(15, 0x7fff0a3ec670, 1)             = -1 EAGAIN (Resource temporarily unavailable)[/B]
it does that for like 1 MB of text.

I've backup my gdm-conf and gdm-conf-custom, are there any other files I would need to back up to do a --purge on the gdm package?

may be a bug [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/42712](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/42712)

---

### Post by jerome1232 on 2008-07-16
I happened on this thread [http://ubuntuforums.org/showthread.php?p=5398494#post5398494](http://ubuntuforums.org/showthread.php?p=5398494#post5398494) with a solution, recompiling my video drivers solved the problem.

---

