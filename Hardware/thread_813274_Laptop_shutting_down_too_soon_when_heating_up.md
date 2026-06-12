---
title: "Laptop shutting down too soon when heating up"
date: 2008-05-30
forum: Hardware
---

### Post by thetor on 2008-05-30
I'm not stressing my laptop CPU too often, but today I happened to be performing a long-running (hours) CPU-intensive task. Even if I'm running both CPU cores at 100%, my laptop never needs to run the cooling fan continuously at full blast. It runs at low speed, builds heat, and at a certain temperature the fan kicks in and runs full speed for a while, then slowing down and the cycle starts over. A temperature graph would show the distinct "sawtooth" waveform.

In case of fan failure the CPU (Intel Core 2) will throttle itself down (at 95 C I think) or shut down in extreme cases (Tjunction max = 100 C if I remember correctly)

Running todays intensive task however, I discovered that Ubuntu adds it's own layer of thermal protection. Without warning, the laptop suddenly shut down (soft shut down, obviously initiated by software). The relevant part of the system log shows the following.

```
May 30 20:39:59 kernel: [ 4794.783772] CPU1: Temperature above threshold, cpu clock throttled (total events = 1)
May 30 20:56:08 kernel: [ 5680.363104] CPU1: Temperature above threshold, cpu clock throttled (total events = 2)
May 30 21:51:59 kernel: [ 8697.684043] CPU1: Temperature above threshold, cpu clock throttled (total events = 4)
May 30 21:51:59 kernel: [ 8698.127983] ACPI: Critical trip point
May 30 21:51:59 kernel: [ 8698.127990] Critical temperature reached (82 C), shutting down.
May 30 21:51:59 init: tty4 main process (4566) killed by TERM signal
May 30 21:51:59 init: tty5 main process (4567) killed by TERM signal
May 30 21:51:59 init: tty2 main process (4573) killed by TERM signal
May 30 21:52:00 init: tty3 main process (4576) killed by TERM signal
May 30 21:52:00 init: tty6 main process (4578) killed by TERM signal
May 30 21:52:00 init: tty1 main process (5575) killed by TERM signal
May 30 21:52:02 avahi-daemon[4988]: Got SIGTERM, quitting.
May 30 21:52:03 kernel: [ 8702.010497] Critical temperature reached (75 C), shutting down.
May 30 21:52:05 exiting on signal 15
```

It seems that "the tip of the sawtooth wave" reaches beyond the throttle threshold from time to time, and the CPU is throttled down for a limited time. All is well.

Now that's interesting. The fourth time this happens, within the same second, ACPI decides to shut down. That's not very efficient, right? The cpu has been throttled down and the temperature is surely on it's way down. Why not wait a few seconds and see if the throttling worked? After three seconds the temperature was apparently down to 75 C, but then the system was already shutting down.

As I've tried to point out, the CPU fan is capable of doing its job even at high workloads. It takes a few seconds after the fan has increased speed until the temperature begins to decrease though, and I don't think that this should have to lead to a system shutdown.

Now I obviously have to restart my CPU-intensive task from the beginning, except I down't want to risk being interrupted again. Is there any way to adjust the temperature threshold so that I can run my job uninterrupted? If this is not possible, can I disable the software thermal protection entirely?

EDIT: I should perhaps mention that I'm running Ubuntu 8.04 Hardy Heron.

---

### Post by Sam Lars on 2008-05-30
There are quite a few threads about this sort of thing.
[http://ubuntuforums.org/showthread.php?t=551829&highlight=acpi+temperature+change&page=2](http://ubuntuforums.org/showthread.php?t=551829&highlight=acpi+temperature+change&page=2)


[http://ubuntuforums.org/showthread.php?t=178626&highlight=acpi+temperature+change&page=2](http://ubuntuforums.org/showthread.php?t=178626&highlight=acpi+temperature+change&page=2)

How to change the trip points of fans
[http://ubuntuforums.org/showthread.php?t=551829&highlight=acpi+temperature+change&page=2](http://ubuntuforums.org/showthread.php?t=551829&highlight=acpi+temperature+change&page=2)

Also, what kind of laptop do you have?  If it's a Dell, you can use i8kmon to control this.

---

### Post by thetor on 2008-05-31
Thanks for your reply! My laptop is a Fujitsu Siemens v3205.

I tried the procedure described in this thread: [http://ubuntuforums.org/showthread.php?t=379729](http://ubuntuforums.org/showthread.php?t=379729)
I.e. writing the new trip point values to the file /proc/acpi/thermal_zone/TZ00/trip_points However, I get "Permission denied" when I try to write to the file using sudo, and "Input/output error" when I use su. It seems that the acpi driver has changed in recent versions of the kernel, so that it no longer accepts input to this file. what's the new "correct" way to change these values?

---

### Post by Sam Lars on 2008-06-06
I think you have to be in a root terminal by doing
```
sudo -i
```
to echo to those places, not just with sudo.

---

### Post by cygnine on 2008-06-06
I actually have a similar problem and I have tried some of the methods presented in the threads you pointed to, Sam Lars, but I can't seem to get much of anything to work. 

The first thing I want to do, which seems to be the most transparent, reasonable thing to do is to use echo to set trips points (and to set them every time the OS tries to reset them to their original values, but one thing at a time here). 

In any case, these are the results I get:

```
*****@*****:~$ sudo -i echo -n 99:95:35:70:60 > /proc/acpi/thermal_zone/THM0/trip_points 
bash: /proc/acpi/thermal_zone/THM0/trip_points: Permission denied
*****@*****:~$ ls -al /proc/acpi/thermal_zone/THM0/trip_points 
-rw-r--r-- 1 root root 0 2008-06-06 21:45 /proc/acpi/thermal_zone/THM0/trip_points

```

I don't know why it won't let me change trip_points especially since it's got write permissions for root (which, by the way, I had to change myself from 444 permissions). I've written a shell script with that command in it, and when I run that script, here's what I get:

```
*****@*****:~$ sudo /etc/acpi/set-trip-points.sh 
/etc/acpi/set-trip-points.sh: line 4: echo: write error: Input/output error

```

I have no idea what the problem is there. Doing `sudo -i' doesn't change the error. Why can't I change that file? And why do I get a different error with "sudo command" than with "sudo script-containing-same-command"?

And in case you're wondering why I want to change the default trip points, it's because the only trip point commands that are in the trip_points files are a little sparse (and a little silly) in my opinion:

```
*****@*****:~$ cat /proc/acpi/thermal_zone/*/trip_points
critical (S5):           127 C
critical (S5):           99 C
passive:                 95 C: tc1=5 tc2=4 tsp=600 devices=CPU0 CPU1 

```

My laptop (CPUs) consistently runs 70C+. I'm actually quite happy if it runs 70C given the norm: I do scientific computing jobs and the temps easily run up to 90C. I've even had critical shutdowns a couple of times, which might have been averted if my trip points weren't too stupid (please excuse the leak of bitterness...) to realize that the fan should go on before 95C. In case you're wondering, my cpu freq governors are ondemand. Also, in case it matters, my GPU temp is *always* about 5C hotter than either of my cpus, and if I run videos (flash/dvds/whatever) then my gpu/cpu temps get to 90C within minutes.

I'm also running Ubuntu 8.04 with a Thinkpad T61, ATI Radeon X1300 chipset, using the restricted graphics drivers.

---

### Post by Sam Lars on 2008-06-06
Try doing a
```
sudo -i
```
by itself.  It will get you to
```
root@*****
```
and then try echoing to the file.

---

### Post by cygnine on 2008-06-07
Still no dice....

```
*****@*****:~$ sudo -i
[sudo] password for *****: 
root@*****:~# echo -n 99:95:35:70:60 > /proc/acpi/thermal_zone/THM0/trip_points
-bash: echo: write error: Input/output error

```

The permissions for /proc/acpi/thermal_zone/THM0/trip_points was changed back to r--r--r--, so I had to change it to rw-r--r-- before running that command.

By the way, I'm new to scripting: is the "echo blah > file" command the basic way to write text to a file in an automated way?

---

### Post by Barlennan on 2008-11-26
Try uninstalling powersaved and installing powernowd. That stopped the random shutdowns on my k7 laptop, but did not make the CPU temperature reporting any more accurate. The fan and CPU freq scaling are working more or less as they were before.

---

