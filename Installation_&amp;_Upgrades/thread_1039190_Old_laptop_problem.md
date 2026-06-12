---
title: "Old laptop problem"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by kevinson on 2009-01-14
Hey there,

Last week I was thinking of using my old(read very old) laptop again. I installed windows xp on it, worked fine but still a little bit slow. I recently got interested in Ubuntu and downloaded it. I tried to install on laptop and everything went fine, until the moment you get to the screen with a skull (or am I hallucinating? :P) on the background, then it freezes. Only option it to power off. Sometimes when booting from the cd it hangs at an easy fase, sometimes when fully booted.
I then tried XUBUNTU, installation went smoothly. But then the booting...it freezes after a random moment, sometimes at the loading screen and sometimes when fully loaded.

Is there any solution to this, or an even lighter OS maybe?

Specs:
700MHz cpu
192MB RAM
20gb HDD - completely formatted

Thanks in advance

---

### Post by snowpine on 2009-01-14
I would recommend upgrading your ram to 512mb for Ubuntu. If you are stuck with only 192mb, your best bet is the "xubuntu alternate install cd." It uses a text-based installer but once installed it is the same system.

If you want to go even lighter than Xubuntu, my personal favorites are Crunchbang or Crunchbang Lite. They are not "official" releases, though, if that's important to you.

---

### Post by kevinson on 2009-01-14
> **snowpine said:**
> I would recommend upgrading your ram to 512mb for Ubuntu. If you are stuck with only 192mb, your best bet is the "xubuntu alternate install cd." It uses a text-based installer but once installed it is the same system.

If you want to go even lighter than Xubuntu, my personal favorites are Crunchbang or Crunchbang Lite. They are not "official" releases, though, if that's important to you.


I know ubuntu wouldn't want to work because of the RAM but XUBUNTU should work though. As its requirements state '192MB RAM'. And I did try XUBUNTU, installation went smoothly but the boot doesn't.

I might go lighter if nobody knows any other solution then buying more RAM (which is not an option).

---

### Post by snowpine on 2009-01-14
OK, I misunderstood the situation. Try this. When you boot Xubuntu, at the Grub bootloader screen, press 'e' to edit the boot parameters. Delete the words 'splash' and 'quiet', then press enter followed by 'b' to boot. This will give you a more detailed text output instead of the Xubuntu splash screen. Take note of which messages are displayed when the crash occurs, and hopefully you can use that information to troubleshoot the problem.

---

### Post by kerry_s on 2009-01-14
what model? some have quirks you have to work around. for instance on my ibm t20 i have to add a option to xorg.conf before i can even run X or it just freezes.

you don't really have enough ram to run a normal distro from cd.

you can try dsl if you want a live cd:
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

you have enough to run a normal linux, but not live, you'll have to install it using the non live method, for example for xubuntu you need to use the alternate cd:
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/xubuntu-8.10-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/xubuntu-8.10-alternate-i386.iso)

debian should be fine:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

i run 2 old computers:
vaio pcg-f430 450mhz 256mb ram, running a debian custom install.
ibm t20 700mhz 128mb ram, running arch linux. just got this back from grandma it has 256mb ram, but 1 memory slot has just gone bad, so it only use half, the 128mb ram. i'm still expermenting with it.

---

### Post by kevinson on 2009-01-14
I removed the quiet but no error messages, it just hangs without a message/warning.

As far as I can see it's a compaq armada m700.

---

### Post by snowpine on 2009-01-14
A quick search turned up this thread on the armada m700:

[http://ubuntuforums.org/showthread.php?t=999850](http://ubuntuforums.org/showthread.php?t=999850)

---

### Post by kerry_s on 2009-01-14
after a quick google it seems for that model you have to define the video ram.

> I suggest to specify "VideoRam 8192" in your graphics card specification; I don't know if it makes any difference on this laptop, but it's a safe thing to do. The XFree86 in my Armada 100S froze strangely if the amount of videoram was not defined.

so if you have it installed, at boot use the second boot line for single mode.
edit the xorg.conf:
sudo nano /etc/X11/xorg.conf

scroll down to the video driver section and add:

Option "VideoRam" "8192"

then save and reboot(ctrl+alt+delete).

---

### Post by kevinson on 2009-01-14
> **snowpine said:**
> A quick search turned up this thread on the armada m700:

[http://ubuntuforums.org/showthread.php?t=999850](http://ubuntuforums.org/showthread.php?t=999850)

Thanks, I Googled a bit but didn't find information like that.
I'll try DSL.


edit:


> **kerry_s said:**
> after a quick google it seems for that model you have to define the video ram.



so if you have it installed, at boot use the second boot line for single mode.
edit the xorg.conf:
sudo nano /etc/X11/xorg.conf

scroll down to the video driver section and add:

Option "VideoRam" "8192"

then save and reboot(ctrl+alt+delete).

What exactly do you mean with "use the second boot line for single mode" ?



edit:
It somehow booted in Xubuntu :S might be a one-time boot...

---

### Post by kevinson on 2009-01-14
Had to bring this post up again.

I installed DSL but now my mouse doesn't work anymore...
It isn't a USB mouse but one with a green connecter thingy.

---

### Post by kerry_s on 2009-01-14
> **kevinson said:**
> Had to bring this post up again.

I installed DSL but now my mouse doesn't work anymore...
It isn't a USB mouse but one with a green connecter thingy.

in dsl boot with "xsetup" on the boot line. you got enough ram you can boot to ram.

**dsl toram xsetup**

(i think, been awhile since i used dsl)

---

### Post by kevinson on 2009-01-14
> **kerry_s said:**
> in dsl boot with "xsetup" on the boot line. you got enough ram you can boot to ram.

**dsl toram xsetup**

(i think, been awhile since i used dsl)

doesn't work :S, should that remove the mouse problem?

---

### Post by kerry_s on 2009-01-14
> **kevinson said:**
> doesn't work :S, should that remove the mouse problem?

use the f? key to see the boot options when it starts.
with xsetup you choose the type of mouse you have.

---

### Post by kevinson on 2009-01-14
> **kerry_s said:**
> use the f? key to see the boot options when it starts.
with xsetup you choose the type of mouse you have.

I grabbed another mouse and it's working now :D, this one has an usb connector.

Thanks for your help all :D):P

---

