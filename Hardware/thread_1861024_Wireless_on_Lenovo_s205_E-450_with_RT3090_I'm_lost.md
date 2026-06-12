---
title: "Wireless on Lenovo s205 E-450 with RT3090 I'm lost"
date: 2011-10-15
forum: Hardware
---

### Post by moteprime on 2011-10-15
Hi.
I got a Lenovo s205 (E-450), and i just can't get wireless working right.

In another thread i found this

rfkill unblock wifi
rfkill unblock all
modprobe -r acer-wmi
in: rc.local

It works, but the network speed is awful, below 60kb/s and my old eee laptop thats playing streamed internet radio drops connections when i connect the s205. Something is wrong.


I tried Wicd (removed network manager) with rfkill unblock all in rc.local. It kinda works but network speed is unstable, falls in speed after a couple of minutes, and ends up stopping completely.


I tried ndisgrabber blacklisting these drivers:

blacklist acer_wmi
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
in: /etc/modprobe.d/blacklist.conf

Ndisgrabber sees the adapter, but wireless does not show up in network manager. (reinstalled of course).

I tried all the solutions on this excellent blog by rwh:
[http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177)

I'm a bit lost here, and could use some help. It's not unlikely that i did something wrong, but i did try all these things at least 3-4 times each.
Please help.

---

### Post by moteprime on 2011-10-17
No one to the rescue?

---

### Post by moteprime on 2011-10-22
I now got ndiswrapper working, but the network speed are again below 70-80kb/sec.
Why can i not make this work?

---

### Post by moteprime on 2011-10-25
What it took was to install this driver: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

Blacklist "acer_wmi" in /etc/modprobe.d/blacklist.conf

Add "rt3090sta" til /etc/modules

---

### Post by nitroguy on 2011-10-30
Hey there, mote!

We've gone back and forth a bit in different threads, but it seems as though you've found a solution to this networking thing, that I haven't quite gotten down. 

My wireless works by using the method shown here: ([http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177)). Unfortunatley, as you stated, wicd is rather unstable, and fails to connect quite often. To say nothing about the suspend/hibernate failure to reengage.


You seem to have a handle on a way to make this work, although I'm a bit new to this Ubuntu thing - can you help walk me through your method?

Thanks!
nitroguy

---

### Post by moteprime on 2011-10-31
Hi nitroguy.
Yes i have been all over the place to get this to work, and also the blog you found on [http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177) I wrote as mote there. It took me 3 weeks before i got it working.
I am using Ubuntu desktop 11.10 64 bit, there are som differences in the way the wifi driver works. I think that the above blog are mostly for 11.04.

If you want to try the way i had success with, first you have to remove wicd.
This is going to be by memory so i hope its right.

- connect via the wired ethernet port
[B]- apt-get  install network-manager
- apt-get remove wicd[/B]
- disconnect the wired ethernet port
Reboot.

In my system wicd left an entry in startup application, so find it and uncheck it.

Download this driver [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)
Install it by double clicking the file, software center will install it. Its takes a while but have patience.

Open a terminal and edit the file /etc/modprobe.d/blacklist.conf

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

insert this line in the end.
```
blacklist acer_wmi
```

Be sure to remove all the other blacklistings you have inserted while trying to get wifi working.
In this thread [http://ubuntuforums.org/showthread.php?t=1849602&page=3](http://ubuntuforums.org/showthread.php?t=1849602&page=3) in post #26 you can see my
/etc/modprobe.d/blacklist.conf file.
all the lines with "#" in front are just remarks.

In file /etc/modules add rt3090sta to the end of the file.

```
sudo gedit /etc/modules
```

Reboot.

---

### Post by nitroguy on 2011-10-31
Hmmm.

So, I'm close. I followed your above directions (very clear by the way, thank you!) ((For anyone else following this thread be sure to "sudo" before apt-get. A "duh" statement, but a requirement nonetheless).

So, I turn on my computer, and I see the network manager in the system tray (sorry, I forgot the Official Name of it). And Enable Wireless is indeed checked (something that couldn't happen previously). But under the wireless tab, there are no available wireless networks, despite me literally sitting on one.

Any tips? I'll keep poking around tonight to see what I can find, and update accordingly.

Thanks!!

---

### Post by moteprime on 2011-11-01
Hi.
Strange that it does not work as supposed to.
Be sure that your "/etc/modprobe.d/blacklist.conf" and "/etc/modules" are right.
If you type "modinfo rt3090sta" in a terminal, what's the output?

---

### Post by moteprime on 2011-11-01
BTW.
if you click "This bug affects you" or subscribe to the bug i reported, maybe we can get this annoying bug fixed.
[https://bugs.launchpad.net/ubuntu/+bug/875659]("https://bugs.launchpad.net/ubuntu/+bug/875659")

---

### Post by nitroguy on 2011-11-01
Here's the result of the code:

```
$ modinfo rt3090sta
filename:       /lib/modules/3.0.0-12-generic/updates/dkms/rt3090sta.ko
version:        2.3.1.3
srcversion:     FFE8374362ED5B734E14328
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```

And yes, my blacklist file and modules file are both as you say:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#testing wireless. blacklisting the wifi driver
blacklist acer_wmi
```

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3090sta
```

Anything I'm doing wrong?

---

### Post by nitroguy on 2011-11-01
Doing a bit more digging here.

Perhaps I have the wrong driver? Although it states I have 2.3.1.3, which is correct, as you say.

However, on the archive site ([https://launchpad.net/~markus-tisoft/+archive/rt3090/+build/1491488](https://launchpad.net/~markus-tisoft/+archive/rt3090/+build/1491488)) it states it's for i386. Forgive my ignorance, but isn't that 32bit? Are you running 11.10 32 bit, or 64 bit? I've got 64 bit installed, as I thought that was the appropriate version. Is this incorrect perhaps?

---

### Post by moteprime on 2011-11-02
Hi nitroguy
Your files look all right to me.
About the 32/64 bit, I am also using Ubuntu 64 bit version.
I found the solution here: [http://ubuntuforums.org/showthread.php?t=1860574&highlight=rt3090]("http://ubuntuforums.org/showthread.php?t=1860574&highlight=rt3090")
At first I, out off habit installed the newest version, but had no luck, when I checked up on the version used by cirelosborn, and the 2.3.1.3 worked.
I did notice that the build are for i386, but it must be working anyway. (i'm new to 64-bit)
And as there are only the one build version i can't be wrong about the version i downloaded, it would have been so easy to get things mixed up. it is 2.3.1.3
In the other thread rodhull seems to have the same problem as you have now, his network manager does not scan for network.
I think maybe, not to have this running in two threads and as your and his problem are the same, we should continue in the other thread?
[http://ubuntuforums.org/showthread.php?p=11416435#post11416435](http://ubuntuforums.org/showthread.php?p=11416435#post11416435)

---

### Post by rodhull on 2011-11-02
No - don't think you're doing anything wrong. I have the exact same results on my S205 - module builds, installs and loads but I can't scan for networks or manually join either - I just don't think that module works and I'm surprised it works at all on **moteprime's** rig...I agree with him - let's continue in the other thread...

---

### Post by nitroguy on 2011-11-02
Yep. This thread is officially closed (hehe, look, I can be a moderator too!) 

All future conversations will be at: [http://ubuntuforums.org/showthread.p...5#post11416435](http://ubuntuforums.org/showthread.p...5#post11416435)

Hope to see you there!

---

