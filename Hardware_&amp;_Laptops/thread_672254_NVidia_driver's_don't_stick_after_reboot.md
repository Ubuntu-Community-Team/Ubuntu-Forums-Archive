---
title: "NVidia driver's don't stick after reboot"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by lunchboxtheman on 2008-01-19
This is my first post, so forgive me if this is in the wrong category, but it's mostly hardware related I would guess.  
I'm running Ubuntu 7.10 and have an 8600GTS.  I downloaded the Linux driver from nvidia.com and installed it fine.  After restarting X, the driver works great.  I can run in any resolution I want, I can enable all of the special effects, etc.  It works as it should.
The problem comes after I restart my machine.  Right before I get to the logon screen a box pops up and says "Your video card could not be detected properly.  Your system is now running in low graphics mode."  It gives you the option to manually select the driver, but the only NVidia one available is the restriced one that you get via the updates manager.

I've tried running nvidia-config and nvidia-settings as root, and have re-written my xorg.conf file as such, but the driver doesn't seem to stick.  Also, I made a backup of the NVidia xorg.conf file and replace the one in /etc/X11 with it and restart X, but that still doesn't work :-(

Any idea?  Thanks in advance.

EDIT: I guess this should be in the multimedia section, feel free to move it mods :-)

---

### Post by sean55379 on 2008-01-20
I had a very similar issue after I updated my kernel.  I could install the driver from NVidia and it would work until I rebooted.  (I'm using Ubuntu 7.10 and have an 8600GT.)

This post on the NVidia forums helped me:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Look under the title: Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

---

### Post by lunchboxtheman on 2008-01-20
Thanks, I'll take a look and report back my findings :-)

---

### Post by lunchboxtheman on 2008-01-21
I tried everything relating to my problem in that post, and nothing worked.  It shouldn't matter, but I'm running a dual boot XP-Ubuntu machine, but each OS has its own HDD, and I'm using GRUB as my boot manager.  I tried reverting back to an older nVidia driver, but that didn't work either.  So much for Linux being a replacement desktop... it doesn't even work :-/

---

### Post by w0rt3x on 2008-01-21
Have the same problem... Tried uniinstalling and so on the stuff in the nvidia forums, hope it works :)


EDIT: Nope, the same :| Any ideas anyone?

EDIT2: I still can fix this by running 

sudo dpkg-reconfigure xserver-xorg

and restarting PC, but doing so everytime costs time...

---

### Post by w0rt3x on 2008-01-22
Cmon, doesn't anybody know? :|

---

### Post by Whiffle on 2008-01-22
On a fresh reboot, do:

lsmod

is nvidia listed in that list?    It sounds to me like the nvidia kernel module isn't getting loaded.

---

### Post by w0rt3x on 2008-01-22
Yes it is (at least for me).

PS. I thought this might be useful:

When I run 

 nvidia-settings --load-config-only, i getL

ERROR: Cannot open display 'Unix:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/wtx/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 20 of
       configuration file '/home/wtx/.nvidia-settings-rc' (no Display
       connection).

And so on for the next ~20 lines. Does this have something to do with it?

Again, remembered that this is about the same:

wtx@Unix:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for wtx:
Sorry, try again.
[sudo] password for wtx:
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080122163605
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device

Thanks in advance.

---

### Post by lunchboxtheman on 2008-01-22
> **Whiffle said:**
> On a fresh reboot, do:

lsmod

is nvidia listed in that list?    It sounds to me like the nvidia kernel module isn't getting loaded.

Yup, it sure is in that list.

---

### Post by w0rt3x on 2008-01-25
Bump :)


Now really, could anyone help? Anything would be appreciated.

---

### Post by lunchboxtheman on 2008-01-25
I FIXED IT!  .... not really, just installed Fedora.  It works great, no issues whatsoever.  Have to say I think I still prefer Ubuntu.  But, hey, I'll use whatever works.
Maybe when the next version of Ubuntu comes out I'll give it a shot again.

---

### Post by w0rt3x on 2008-01-26
> **lunchboxtheman said:**
> I FIXED IT!  .... not really, just installed Fedora.  It works great, no issues whatsoever.  Have to say I think I still prefer Ubuntu.  But, hey, I'll use whatever works.
Maybe when the next version of Ubuntu comes out I'll give it a shot again.

Hehe, that'll be VERY soon, so I guess u rushed a lil bit to mutch :) Anyway I hope I won't have to do the same...Help anyone ? :)

---

### Post by L_V on 2008-01-26
What is the status of this bug with Nvidia after reboot ?

Same issue noticed with nvidia legacy. (Kubuntu 7.10)

---

### Post by w0rt3x on 2008-01-26
> **L_V said:**
> What is the status of this bug with Nvidia after reboot ?

Same issue noticed with nvidia legacy. (Kubuntu 7.10)


It just writes:
Your video card could not be detected properly. Your system is now running in low graphics mode. :|

---

### Post by lunchboxtheman on 2008-01-28
A new nVidia driver was realased on the 21'st.  I haven't tried that one (obviously I'm running Fedora now).  Can anyone give any insight as to whether or not the new driver fixes this issue?

---

### Post by goog on 2008-01-28
I tried the new Nvidia 169.09 drivers that were released on January 21st and have the same issue. I'm running Ubuntu 7.10 x64 with a 8800gt.

Has anyone found a way to fix this yet?

---

### Post by harold4 on 2008-01-28
Have any of you tried [Envy]("http://albertomilone.com/nvidia_scripts1.html") to uninstall/install the nvidia drivers?  

That has always worked for my nvidia machines.

---

### Post by goog on 2008-01-28
> **harold4 said:**
> Have any of you tried [Envy]("http://albertomilone.com/nvidia_scripts1.html") to uninstall/install the nvidia drivers?  

That has always worked for my nvidia machines.

I tried using Envy about a week ago and the 8800gt was not supported so it would not install. Has it been updated since then?

---

### Post by goog on 2008-01-28
Update: SUCCESS!

Looks like [Envy]("http://albertomilone.com/nvidia_scripts1.html") was updated to include the 8800gt. I have restarted twice now and the drivers seem to be standing their ground.

---

### Post by lunchboxtheman on 2008-01-28
Excellent!  It's late now, but I'll reinstall Ubuntu tomorrow and see if I can get the same results.  Here's hoping it works!

EDIT: It worked for one reboot, then my whole system crashed.  The drivers don't work even after a fresh install.  **** it, windows works 99% of the time.  Call me in 10 years when Linux works that much too.

---

### Post by harold4 on 2008-01-30
> **goog said:**
> Update: SUCCESS!

Looks like [Envy]("http://albertomilone.com/nvidia_scripts1.html") was updated to include the 8800gt. I have restarted twice now and the drivers seem to be standing their ground.

Glad to hear it.

---

### Post by gsoundsgood on 2008-02-21
still not working for me....installing the nvidia drivers with latest Envy. nvdia 8600 gt. same thing as the others.
any idea?

---

