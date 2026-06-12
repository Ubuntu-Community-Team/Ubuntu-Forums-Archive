---
title: "Sleep/suspend (S3) not waking at all (weird screen)"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by jakeg on 2007-05-14
Hi,

Trying (again) to switch from Windows to Linux but a major drag for me is not being able to sleep (suspend, S3) my laptop. It goes to sleep fine, but when it tries to wake the screen is mainly still black apart from vertical lines of solid colour, predominately towards the left of the screen. These vertical lines get gradually brighter. I've tried pressing CTRL+ALT+F1 etc, and tried the following which was supposed to work with my laptop (TM C110) model but without success:

> "(8) on some systems, you can use the video_post utility mentioned here:
  [http://bugzilla.kernel.org/show_bug.cgi?id=3670](http://bugzilla.kernel.org/show_bug.cgi?id=3670). Do echo 3 > /sys/power/state
  && /usr/sbin/video_post - which will initialize the display in console mode.
  If  you are in X, you can switch to a virtual terminal and back to X using
  CTRL+ALT+F1 - CTRL+ALT+F7 to get the display working in graphical mode again."


... but no luck yet. Hibernate works but takes about as long as a cold boot so is no good at all. With Windows I'd close my laptop, then reopen it and bam, a few seconds later straight back to work. I'll have to go back to it if I can't get this working.

On the bright side, apart from this, out of the box Linux finds more than Windows XP without having to install extra drivers etc. For example, my laptop is a tablet and the screen works as a pointing device fine.

My laptop is an Acer TravelMate C110 (C111TCi) and I'm using Ubuntu 7.04.

Jake.

---

### Post by jakeg on 2007-05-19
okay, got this working now using 'vbetools' by doing the following:

> 
First, boot into X and run the following script ONCE:
#!/bin/bash
statedir=/root/s3/state
mkdir -p $statedir
chvt 2
sleep 1
vbetool vbestate save >$statedir/vbe


To suspend and resume properly, call the following script as root:
#!/bin/bash
statedir=/root/s3/state
curcons=`fgconsole`
fuser /dev/tty$curcons 2>/dev/null|xargs ps -o comm= -p|grep -q X && chvt 2
cat /dev/vcsa >$statedir/vcsa
sync
echo 3 >/proc/acpi/sleep
sync
vbetool post
vbetool vbestate restore <$statedir/vbe
cat $statedir/vcsa >/dev/vcsa
rckbd restart
chvt $[curcons%6+1]
chvt $curcons


... this comes from [http://developer.osdl.org/dev/robustmutexes/src/fusyn.hg/Documentation/power/video.txt](http://developer.osdl.org/dev/robustmutexes/src/fusyn.hg/Documentation/power/video.txt) . Note that the script that has to be run once needs to be done as root as well.

So now after suspend the laptop resumes fine... but wireless isn't working at all. If I then hibernate after a suspend though, wireless comes back fighting.

Jake

---

### Post by jakeg on 2007-05-20
I've filed a bug for the wireless not working bit:
[https://bugs.launchpad.net/ubuntu/+bug/115743](https://bugs.launchpad.net/ubuntu/+bug/115743)

---

### Post by jakeg on 2007-05-21
I figured out a hacky workaround using 'acerhk' for the wireless problem, which was caused by the RF wifi switch being disabled after a sleep/resume cycle. See the bug report for full details:

[https://bugs.launchpad.net/ubuntu/+bug/115743](https://bugs.launchpad.net/ubuntu/+bug/115743)

---

### Post by giosico on 2007-05-23
I too have the 'on wake' from sleep black screen of death with a small box of vertical wavy lines.

I am running Feisty on a HP Pavillion dv6000.

I have not tried your workarounds as they indicate wifi is broken with a fix that uses a program for Acer hot keys.

---

### Post by giosico on 2007-05-23
Moving away the btn files and then sim linking them as follows fixed my sleep problem but not my hibernate problem ...

    ln -s /etc/acpi/sleep.sh /etc/acpi/sleepbtn.sh
    ln -s /etc/acpi/hibernate.sh /etc/acpi/hibernatebtn.sh

From [https://launchpad.net/ubuntu/+source/acpi-support/+bug/47508](https://launchpad.net/ubuntu/+source/acpi-support/+bug/47508)

---

