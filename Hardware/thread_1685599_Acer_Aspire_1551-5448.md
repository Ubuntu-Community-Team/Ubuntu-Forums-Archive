---
title: "Acer Aspire 1551-5448"
date: 2011-02-10
forum: Hardware
---

### Post by dcoston on 2011-02-10
Hey,

I installed  64-bit Ubuntu 10.10 Maverick on my NotBook - Acer Aspire 1551-5448.  There are several things that are not working quite right, and I've researched them all and nothing seems to work.

1. I finally got the internal mic to work, however, it is really scratchy.  does anyone know what I can do to fix it?

2. The wireless network discovery doesn't start on start-up.  It's not a big deal, I just have to fire it up once the system starts.  It would great to get this working on start up.

3. The machine doesn't wake from Suspend or Hibernate.  I hear it is kernel related?  Which scares me, cause I'm pretty new to ubuntu and the linux community.

Any help with these issues would be much appreciated!  Like I mentioned, I am pretty new to ubuntu, but love the OS, so please speak in baby language.

Thanks!

---

### Post by dcoston on 2011-02-13
1. I finally got the internal mic to work, however, it is really scratchy. does anyone know what I can do to fix it?
 -I was able to alsa to minimize the front mic boost.  It now records anything the front mic picks up.  However, the mic still does not work with google voice?

2. The wireless network discovery doesn't start on start-up. It's not a big deal, I just have to fire it up once the system starts. It would great to get this working on start up
 -I ran this command, shutdown, and started back up, and the wireless turned on and connected to my preferred network.
sudo gedit /etc/rc.local

added this line to the bottom of the rc.local filem before the line that reads(exit 0):
/usr/bin/nmcli nm wifi on

3.  Still no progress on on starting after hibernate or sleep.  Help?

---

### Post by dcoston on 2011-03-15
Updates:

1. The Mic works wonderfully now.  After muting just the left OR right mic, the mic works.  However, applications like Google Voice and Skype like to mess with them.  In Skype, go to Options > Sound Devices > Uncheck the "Allow Skype to automatically adjust my mixer levels."  For Google Voice, you need to adjust a configuration file.  Changing the first line of "~/.config/google-googletalkplugin/options" from "audio-flags=3" to "audio-flags=1", did the trick for me.

2. Wireless on start-up works wonderfully still.

3. After a recent update, my system now wakes out of Suspend, but not Hibernate.  After reading a few reviews, I will need to compare the wake from Suspend vs. the wake from Hibernate processes.  When I get some time, I look to spend a little time working on it.

Right now, I've got my system to in a much more user friendly state, and I'll focus on my school work.

---

### Post by RussianNeuroMancer on 2011-06-01
Hello!
Did you try Natty LiveCD? For me after upgrade to Natty I can not enable wireless at all. Driver seems load, rfkill detect disabled wifi, but I can not find any way to enable it.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/791373](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/791373)
Acer Aspire 721.

---

### Post by chedabu on 2011-08-23
For the WIFI,  blacklist acer-wmi, it should stop its power management problem with the wifi card

---

