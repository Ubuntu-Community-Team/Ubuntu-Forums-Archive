---
title: "Can you dual boot XP and UNR ?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Davestom on 2009-07-11
Hi Ubuntuforums

2 months ago, I've gotten a AA1 (Acer aspire 1, 150A). After using XP, I started missing having UBUNTU on the portable laptop. I have been reading alot about UNR - but it seems to lack the option of dual boot (acc. to some other forums)

I have XP running now, and I want to dual boot it with UNR. So the question is;
**_QUESTION:_**
**Is it possible to dual boot XP and UNR?**
and if so; **How?**

thanks for your help.

---

### Post by raymondh on 2009-07-11
> **Davestom said:**
> Hi Ubuntuforums

2 months ago, I've gotten a AA1 (Acer aspire 1, 150A). After using XP, I started missing having UBUNTU on the portable laptop. I have been reading alot about UNR - but it seems to lack the option of dual boot (acc. to some other forums)

I have XP running now, and I want to dual boot it with UNR. So the question is;
**_QUESTION:_**
**Is it possible to dual boot XP and UNR?**
and if so; **How?**

thanks for your help.

Couple of options:

1.  Install Ubuntu and then add the ubuntu-netbook-remix package
2.  UNR can come in a liveUSB ... try it out and see your options.

How?

1.  You can use the installer > guided resize (using the slider to allocate sizes in partitions)
2.  You can prior create the ubuntu/UNR partition* and during the installation, select MANUAL

Some tips:

1.  Back up your files.  There are no guarantees.
2.  Defrag windows
3.  Check the compatibility list
4.  Try the LiveUSB first (in live session) and see how your system relates to UNR/Ubuntu.

* You may have difficulties using XP's disk management tool to shrink XP.  You may use gparted. Or, you may just use the guided-resize option mentioned above.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)
[https://answers.edge.launchpad.net/netbook-remix](https://answers.edge.launchpad.net/netbook-remix)

Good luck.  Post back if you need further assistance.

---

### Post by Alxl on 2009-07-20
I downloaded Portable Ubuntu Remix from   [http://sourceforge.net/](http://sourceforge.net/)   and am also using XP. 
And one does not need to reboot to get to the one or the other.
 I am new to Linux and do not understand how it was done but you can read about it, if still interested.
Let us know

---

### Post by /usr/sbin on 2009-07-20
Another option is to download the UNR img and then write it to a USB, this allows you to run it live or have the option to install it.

---

