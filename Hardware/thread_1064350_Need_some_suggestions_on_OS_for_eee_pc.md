---
title: "Need some suggestions on OS for eee pc"
date: 2009-02-08
forum: Hardware
---

### Post by koolguynet on 2009-02-08
I have an Asus eee pc 1000H.  Great netbook!  Since I got it, I have been running ubuntu-eee (now called Easy Peasy).  It runs great but I am a version behind and can't tell people I am running an OS called Easy Peasy... ugggh.  I am looking for the best option to install an OS that I can just do a dist-upgrade when I am looking to move to the next version.  I know Easy Peasy won't allow for that.  Does eeebuntu?  Can I get it to run Ubuntu without a custom build?  Other suggestions? What say you?

---

### Post by MarblePanther on 2009-02-08
I personally run plain old Ubuntu with XFCE desktop.

You can install it to usb-stick or sd-card with the usb-installer.

You have to use the kernel from here however:
[www.array.org/ubuntu](www.array.org/ubuntu)

Also I mount /tmp to ramdisk and I add "noatime" to /etc/fstab, I also mount /var/log to ramdisk

---

### Post by snowpine on 2009-02-09
I agree with the panther; if your #1 concern is long-term support and ease of upgrading to the next release, I would definitely recommend Ubuntu/Xubuntu/Kubuntu instead of one of the independent third-party "remixes," which may or may not receive timely updates in the future.

Personally, I am running Cruncheee on my eee 900ha and couldn't be happier with it.

(edit) forums.eeeuser.com is a great resource to learn more about different distros on the eee. Most of the major distros have been attempted on the eee, with varying degrees of success. :)

---

### Post by 5BallJuggler on 2009-02-09
Myself and my wife both have Acer Aspire One's, we're running plain old Ubuntu8.10.
 
I've had to roll back the linux kernel due to wired and wireless connection issues with the Atheros comms card, other than that it works pretty well out of the box.

the only other issue i'm seeing is that some apps have unmaximised windows that don't fit into the screen size ie GPSdrive.

highly recommend Ubuntu8.10 for a netbook

---

### Post by MarblePanther on 2009-02-09
> **5BallJuggler said:**
> Myself and my wife both have Acer Aspire One's, we're running plain old Ubuntu8.10.
 
I've had to roll back the linux kernel due to wired and wireless connection issues with the Atheros comms card, other than that it works pretty well out of the box.

the only other issue i'm seeing is that some apps have unmaximised windows that don't fit into the screen size ie GPSdrive.

highly recommend Ubuntu8.10 for a netbook

Here are my windows on my Xubuntu desktop on my eee:
[ATTACH]102750[/ATTACH]
It is the decoration called Smallscreen in Xubuntu.
It really helps maximize space

---

### Post by glotz on 2009-02-09
[http://wiki.debian.org/DebianEeePC](http://wiki.debian.org/DebianEeePC)

If you run this you can be proud of yourself when your friends ask you the next time :)

---

### Post by koolguynet on 2009-02-15
I think I will try just regular old Ubuntu with the array kernel.  That sounds like a winning combo.  I like xfce, but I prefer gnome.  I have 2GB RAM in this little guy, so it seems to handle gnome like a champ.  One other question.... I like to keep a small partition on this with the XP OS that came with the laptop (for things like Blackberry updates, and flashing my logitech remote).  I am thinking of putting a monster HDD in my netbook.  Does anyone have a way to image my XP partition to throw it onto the new HDD?

---

### Post by m_duck on 2009-02-15
Don't forget the [acpi scripts](http://forum.eeeuser.com/viewtopic.php?id=49081&p=1) so all the extra buttons and cpu frequency scaling and stuff work. I had Ubuntu/Array kernel on my eee 1000 for a while and that was good. Playing with Cruncheee now.

---

### Post by kaffeboy on 2009-02-16
I have a Eee PC 900HA. I tried Easy Peasy back when it was Ubuntu Eee. Long story short...it sucked

Now, I've been running Eeebuntu and I must say It's my favorite Ubuntu derived distro. I've had it for a month now. Too bad I tried it on a spare drive I have just to try it out. I want to install it on the stock 160GB drive, but I'm too lazy. :KS

You should try it yourself. 

[http://eeebuntu.org/](http://eeebuntu.org/)

---

