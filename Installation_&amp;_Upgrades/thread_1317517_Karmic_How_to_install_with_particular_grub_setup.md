---
title: "Karmic: How to install with particular grub setup?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by dedded on 2009-11-06
I have two questions about Ubuntu and Grub.  (If I had any sense, I'd ask them in separate posts.)

A little background is in order.  I am fairly new to Ubuntu (running 9.04 at work since July).  I've run Fedora/Red Hat at home for a few years.  And I've got a partitioning setup that I'm fond of and would like to keep.  It's sort of like this:
    ```

    sda1 - grub
    sda2 - swap
    sda5 - Old Fedora (currently F10)
    sda6 - New Fedora (currently F11)
    sda7 - /home, etc.
    sda8 - empty
```The idea is to install a new release and kick it around awhile before using it for real.  So, for example, when F12 comes out I'll install it in the partition currently occupied by F10.  By default, I'll still be booting into F11 for any real work, but I'll switch to F12 when I feel it's safe.  Next spring I'd install F13 over F11, etc.

With this scheme, it made sense to me to keep grub in a separate partition, independent of any particular OS install.  So I do.  I'd now like play around with Ubuntu a little.  I've got a spare partition to put it in.  I'd like to keep grub independent as I have been in the past.  So two questions about Ubuntu 9.10 come to mind.


1. How do I install Ubuntu without installing grub?  Do I need the alternate installation disk or will the liveCD version suffice?  Either way, will it be obvious how to not install grub?  (In Fedora's installation, there's a little box that you can uncheck.)

I understand that I'll have to format the Ubuntu partition as ext3 to continue to use grub1.


2. How do I later install grub2 (after Ubuntu has already been installed), and put it into its own partition?

I've looked at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2).  It seems that the default location for grub2 is now scattered among /boot/grub, /etc/default, and /etc/grub.d.  This seems unfortunate for my purposes.

I would not mind losing automatic updates to the grub menu when new kernels are installed.  I'm willing to edit a configuration file manually each time.

---

### Post by louieb on 2009-11-06
Install GRUB to the **boot sector of the Ubuntu / (root) partition.**
Live CD installer look for the **advanced button** on the install summary page. Should be able to select or type in /dev/sda8 or what ever partition you install it in.

Can do the same thing with the alt CD. Just can't remember where just be sure to read each page during the install.   [Illustrated Dual Boot Site]("http://members.iinet.net/%7Eherman546/index.html") good expliantion of alt install CD. 
> it made sense to me to keep grub in a separate partition, independent of any particular OS install. I do the same thing. 
after you install create a chain load entry for Ubuntu say you installed in sda8 it would look like. 
```

title  Test Linux chainload on (sda8)    
   root (hd0,7)  
   chainloader +1

```

---

### Post by dedded on 2009-11-14
Thanks, the documentation at that Illustrated guide looks pretty good.

---

### Post by vikjon0 on 2009-11-14
I am trying to understand this my self.

In the Live desktop CD you will find the grub installation check box under the advanced button on the last screen.

On alt CD I cannot find it..it seem to install grub automatically, very strange. The only way I found to control it was to run in expert mode.

Did you find any simple way to install grub efter the installation? 
BTW, grub2 is default in ubuntu 9.10. Which to me is a bit strange since it is a beta(?). I am having some problem with it on Asrock ION 330.

---

### Post by oldfred on 2009-11-14
As louieb posted Herman's site has lots of good info on grub2.

Direct link to grub2 info:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

When you install grub2 to a partition it complains and says it has to use blocklists which are a bad idea. It works just fine for now and my understanding is all chainloading has always used blocklists. Every update also shows the warning message. I am ignoring the warning until it breaks my system but then I will not be able to chainboot?

---

