---
title: "AMD64 Hangs on Boot"
date: 2008-08-21
forum: General Help
---

### Post by karaddin on 2008-08-21
I decided that it was time for me to try switching to a 64bit OS, and so merrily trotted off to install from a 8.04.1 amd64 desktop iso.  Initially I didn't have a CD so I (possibly stupidly) got lazy and used the unetbootin program to create a bootable USB with the 8.04.1.amd64.desktop iso on it.

It booted into the live CD fine, and I was able to install without any dramas, then manually fixed up my /boot/grub/menu.lst file (my hard drives are a bit messy - I have had many OS installs on many different drives, and grub always seems to detect the wrong drives now so I have to manually fix this up, really need to get some new HDs and rotate the data around and clean them up).  When I rebooted from the install, it started loading but after about 45sec of loading it would hang.  I tried booting with quiet and splash modes off and the point it was hanging was just after it had loaded my USB devices.

I then tried booting into recovery mode, and when it got to the point where it asked me what I wanted to do, I said continue booting normally and it then finished booting properly.  After a bit of mucking around (including unplugging all USB devices) I wasnt able to change this behaviour, and gave up for a couple of weeks.

I have gone back to it now and tried installing it again, this time from an iso burnt to CD, and it will no longer even boot into the live CD (also won't boot to the USB live cd, or in recovery mode anymore).  I have a logitech g15 keyboard, and a razer copperhead mouse and noticed that the point at which it hung (and the bouncy bar of loading froze) was right after it powers up the leds in the keyboard and mouse, however this behaviour was unchanged even after unplugging all USB devices.  I did take note of the last thing it tried to load when attempting to boot in recovery mode, however I can't seem to find it now, so will need to reboot to get it.  Edit: Got it now, it was "Starting Hardware Abstraction Layer Hald"

My specs are as follows:
AM2 X2 6000+
GigaByte GA-M55-SLI
4GB DDR2 800MHz
Nvidia 8800GTS 640MB
Creative X-Fi Xtreme Gamer (I realise there are issues getting this working, but don't think it should be causing a failure to boot)


Any help with this would be much appreciated

---

### Post by karaddin on 2008-08-21
Off the first page already :(

---

