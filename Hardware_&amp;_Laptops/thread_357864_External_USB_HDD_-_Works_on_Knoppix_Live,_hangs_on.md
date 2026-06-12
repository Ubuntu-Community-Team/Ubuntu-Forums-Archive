---
title: "External USB HDD - Works on Knoppix Live, hangs on Ubuntu &amp; Windows!"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Kung on 2007-02-10
Hey,

I got a compaq presario 1500 laptop from a friend. I have installed Ubuntu and Windows XP on it, dual boot. However whenever I plug in my external 2.5" usb hdd into my laptop in, It will make my system hang. I am not asking you to support or help me get it running on windows xp if you are able to help me get it working on ubuntu that is all I want, stating that it doesn't work in windows xp only is to give you an idea of what the problem may be. More detail:

In Windows XP, My computer will freeze up loading, the device manager will also freeze up - I can see the HDD in Disk Management but it freezes up when ever I try to click on it for details.

On Ubuntu when I plug the USB HDD into the laptop it picks up my hard drive straight away and shows it on the desktop but when I try to read the files it just hangs entirely.

Both operating systems are completely fresh installs.

*Now here's the real interesting part...*
Now, before I installed Ubuntu or Windows I used Knoppix to check if the laptop was working well. I was able too and still am able to use my USB HDD in Knoppix with no problems, and I am also able to use it on other computers with no problems so the ports, cable, hard drive, caddy are fine.

**Also!** When I unplug the USB HDD from my laptop while its "stuck loading" in Windows XP I see my hard drive along with my other hard drives in My Computer then it obviously disappears shortly after because I just unplugged it.

In Ubuntu, a similar thing happens. When I unplug the USB HDD I am able to see all the contents of my hard drive flash in the "Auto Play Folder" of the hard drive that opens when I plug it in.

I have also tried other USB Hard Drives with different cables and caddies with still no luck, even USB Flash Drives do the same thing... However strangely it all works fine in Knoppix Live CD.

Please help, I really need to be able to use my Hard Drive for data transfer between the many computers I use.

---

### Post by Kung on 2007-02-10
bump

---

### Post by Kung on 2007-02-11
bump?

---

### Post by KingArthur10 on 2007-02-13
I had a similar problem with a USB hard drive a while ago.  The problem ended up being a corrupt filesystem on the USB drive.  It caused both Ubuntu and Windows to hang.  The kicker was, because it caused them to hang, I couldn't format the drive for a fresh filesystem.  I had to dink and tink around until I was finally able to stumble upon something that let me format it.  I'd try making sure your settings are set to not auto-mount USB disks.  Then use gparted to format the drive.  If you have data you need to recover, I dunno what to tell you.  Tinker around and something might work.

---

