---
title: "Bluetooth GPS (IBM X31)"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by gnottage on 2005-11-26
I wanted to try to document some of the things I've been doing to get my Bluetooth GPS reciever working under Ubuntu. My setup is like this:

IBM X31 Laptop with inbuilt Bluetooth running Ubuntu Breezy (5.10)
Holux GR-231 Bluetooth GPS
Navigator 4.4.14 from [www.directions.ltd.uk](www.directions.ltd.uk) (Not Open Source, but runs on Windows, PocketPC and Linux, so I had it to try already)

**Why do I want to use the GPS under Ubuntu Linux?**
Well, using XP-Pro this Laptop seems to dislike remembering the connection, and so it's very unreliable under Windows. Therefore why not try to get it working under Ubuntu and see how well it works. This means it wone cost me money to buy more hardware or software, and hopefully I can get the use I want from what I've already paid for.

**What Did I do?**
This is the hard part. I can't remember everything I did, but I'll try to see what's been done. First The Navigator software:
- Install the Navigator Application by reading the files on the first CD
- Install RAR software, as the maps are rar'd up
- Get the update from directions.ltd.uk and patch it up
- You might need Alien which takes a rpm and creates a deb file
- Install the maps which is a command line application in the Navigator directory
- Install QT
- Troubleshoot the errors which related (for me) to QT being not quite installed correctly (Debian way, Navigator was tested on rpm distro's like Red Hat). I did someting and it worked!
- run npfcNavigator &

I still get a warning: "WARNING: nasd (network audio system) is not running", which I will try to fix, so that the laptop will speak the directions to me!

Bluetooth:
- Install gnome-bluetooth, bluez-utils
- Get bluetooth running by using Fn+F5 (I need to get a visual representation, and hopefully allow Bluetooth to be independant of WLAN)
- sudo hcitool scan, which gives the MAC (or similar) address for the GPS
- sudo hidd --connect 00:XX:XX:XX:XX:XX, which allows Gnome Bluetooth to see  my Holux GR-231. I couldn't do anything with it, which was frustrating for a while.
- sudo rfcomm connect hci0 00:XX:XX:XX:XX:XX to actually connect the laptop to the GPS using bluetooth. I hadn't found that command on Ubuntu forums, so went searching over at Gentoo (distro I used to use, and is on my server). That returns the device information I then typed into Navigator, which then was happy to tell me where I am in the world!

I know this leaves out some details, but I can't recall everything as it's taken a few sessions when I've had a few spare minutes. Now I want the audio working, and to test it on the road. Also the bluetooth Off/On thing. Hope this helps someone...

Mods: If there's a better place for this, or someone wants to FAQ something from it, feel free to do whatever is good for the Linux community. I just wanted to share what info I've come accross.

---

### Post by mips on 2005-11-26
For the Bluetooth & Fn key issue you might want to have a look at these:

[http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html#tpbosd](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html#tpbosd)    This looks like one helluva good guide for IBM users.

[http://aaltonen.us/archive/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/](http://aaltonen.us/archive/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/)
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

These links are not X31 specific but IBM specific but I think they will be usefull.

I can only point you here for the NAS stuff, [http://radscan.com/nas/nas-links.html](http://radscan.com/nas/nas-links.html)

---

### Post by gnottage on 2005-11-26
> Now I want the audio working

It looks like all I needed to do was a:

```
sudo apt-get install nas
```

as I no longer have the error.

Thanks mips for you links. I'll see what I can get working...

---

