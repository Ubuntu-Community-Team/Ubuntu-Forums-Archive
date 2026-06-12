---
title: "Suspend/resume problems with screen on Dell Latitude D630 and 10.10"
date: 2011-02-19
forum: Hardware
---

### Post by austin.lund on 2011-02-19
I've very recently just run into troubles with the resuming of my screen with a suspend/resume cycle.  It has worked great until now.

I've checked my /var/log/dpkg.log and nothing has been upgraded in the last month (well before this started happening) which has affected the kernel or nvidia (binary driver).

I've tried booting into single user mode and used "pm-suspend" with the same results ensuing. However I did find out that the resume does seem to complete and I'm able to interact with the system and use the sysreq key.  I tried typing "vbetool dpms on" to get the display back on, but nothing happened.

My video card is:

01:00.0 VGA compatible controller: nVidia Corporation G86M [Quadro NVS 135M] (rev a1)

My edid is attached.

Is there any way to get more logging output to figure out what is going on?

UPDATE:

"vbetool vbestate save" gives zero bytes output after the cycle and 2k before.  Doing "vbetool post" and "vbetool vbestate restore" don't do anything.  After using those commands the save command still gives nothing.

---

### Post by austin.lund on 2011-02-25
OK.  So nobody replied to this.  But I found the problem.  

The cgroup-bin package runs a service which seems to be causing issues.  Probably with the nvidia driver.  Can anyone else receate this on 10.10?

---

