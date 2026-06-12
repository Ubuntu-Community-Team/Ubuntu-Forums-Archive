---
title: "cpufreq-selector hangs - intrepid"
date: 2008-11-11
forum: General Help
---

### Post by The Cog on 2008-11-11
I use this line:
> cpufreq-selector -g powersave
in a script that starts Unreal Tournament to stop it running too fast. But in Intrepid, this command never exits. It seems to set the frequency then just hang. This is on an Athlon 3200+ (1GHz-2GHz clock).

As a work-round I am using cpufreq-set instead, but I'm sure cpufreq-selector shouldn't just hang there. Has anyone else seen this? Any known fixes?

---

### Post by drhex on 2008-12-14
I have noticed the same thing and used strace (which prints all the syscalls made by a program along with their arguments and return values) to see what cpufreq-selector was up to. Here is some output, we see that it is writing "ondemand" to the scaling_covernor pseudo-file:

```
...
open("/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 5
fstat64(5, {st_mode=S_IFREG|0644, st_size=4096, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7eeb000
write(5, "ondemand", 8)                 = 8
close(5)                                = 0
```

and that write succeeds as the governor is changed. But then the program is waiting for something:

```
munmap(0xb7eeb000, 4096)                = 0
gettimeofday({1229289302, 773685}, NULL) = 0
poll([{fd=3, events=POLLIN, revents=POLLIN}, {fd=4, events=POLLIN}], 2, 0) = 1
read(3, "l\2\1\1\0\0\0\0\t\0\0\0005\0\0\0\6\1s\0\6\0\0\0:1.539\0"..., 2048) = 144
read(3, 0x9092a78, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1229289302, 774090}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 774229}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 774384}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 774520}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 774664}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 774807}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 774945}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 0) = 0
gettimeofday({1229289302, 775084}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}], 2, 29889) = ? ERESTART_RESTARTBLOCK (To be restarted)
```

File "3" above is a socket which was created earlier like so:
```
socket(PF_FILE, SOCK_STREAM, 0)         = 3
connect(3, {sa_family=AF_FILE, path="/var/run/dbus/system_bus_socket"}, 33) = 0
```

And file "4", which it seems to be waiting for, was created like so:
```
inotify_init()                          = 4
inotify_add_watch(4, "/etc/PolicyKit/PolicyKit.conf", IN_MODIFY|IN_ATTRIB|IN_CREATE) = 1
inotify_add_watch(4, "/usr/share/PolicyKit/policy", IN_MODIFY|IN_ATTRIB|IN_CREATE|IN_DELETE) = 2
inotify_add_watch(4, "/var/lib/misc/PolicyKit.reload", IN_MODIFY|IN_ATTRIB|IN_CREATE) = 3

```
So I supposed it is waiting for a "policy" of some kind to be updated to reflect the governor change?
I took a quick peek at the source-code of "cpufreq-selector" but it was way over my head (no main() function!?) and the actual waiting seems to take place somewhere else.

Who can tell what's going on here?

---

### Post by drhex on 2008-12-15
I got cpufreq-selector to work now!  I was logged in as an ordinary user, but ran **cpufreq-selector** as root. Instead I should have started **polkit-gnome-authorization** and under org.gnome.conf.Change CPU Frequency scaling set Implicit Authorizations/Active Console to "Yes"- No need to be root anymore for this! :)

---

