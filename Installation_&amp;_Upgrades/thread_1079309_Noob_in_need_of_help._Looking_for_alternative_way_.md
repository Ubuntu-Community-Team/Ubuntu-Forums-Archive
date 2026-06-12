---
title: "Noob in need of help. Looking for alternative way of installing Ubuntu."
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by jinonicolas on 2009-02-24
Hi, guys. I'm new to Ubuntu and I find myself in a position where I can learn how to use it. Problem is, I'm somewhat going without limbs when trying to install this to my old HP Pavillion. Maybe then I'd find some use for this brick.

The easiest way would've been for me to burn the downloaded Ubuntu 8.10 ISO I have here in desktop's "archive." Unfortunately, my laptop's combo drive isn't working anymore. So scratch that idea.

Another way was to boot from USB. Since I have Windows XP installed in my desktop, I used UNetbootin to make my bootable USB installer...only then did I neglect to remember that my old laptop doesn't have USB 2.0 other than those in the PCMCIA card. So scratch that idea again. I tried looking for any bios update that could let me detect my pcmcia card on boot up...but no luck there.

My last try was using Wubi with the downloaded 8.10, since my old laptop did have Windows XP installed anyway. Unfortunately, I received Error 15: file not found. So, that was a failure too.

I have no CD/DVD drive, no USB 2.0 aside from that in the PCMCIA, and no floppy drive either. Thus, my problem of having no way to boot from the Ubuntu installer.

I'm sorry if this became quite lengthy...but here's my question...

Given the fact that I have no other boot device except for the HD, is there a way where I can "copy" (for the loss of any better words) the Ubuntu installer to my C:, create like an autoexec.bat-ish to execute said installer? I'm guessing that using DOS commands on this wouldn't work...please, any help would be much appreciated (aside from getting a new odd for this brick).

Thanks in advance, guys! :D

---

### Post by theozzlives on 2009-02-24
I remember in the WIKI that you can do a network or internet install.

---

### Post by jinonicolas on 2009-02-24
I'll look into that, thanks. :) Would probably take me a couple of hours though considering my broadband isn't that fast. But thanks. :D

---

### Post by albinootje on 2009-02-24
> **jinonicolas said:**
> 
I have no CD/DVD drive, no USB 2.0 aside from that in the PCMCIA, and no floppy drive either. Thus, my problem of having no way to boot from the Ubuntu installer. 
You can indeed boot over the network, but then you need another machine serving as tftp/dhcp server, which is not so easy to set up, and you need that extra machine.

Other options are :
*) Temporarily use an external cdrom or dvd drive from a friend.
or
*) Take out the hard drive and install Ubuntu with your hard drive in another old laptop that does have working usb or cdrom drive.
or
*) Start loading the installation with "loadlin", this is a DOS program to boot Linux or Linux installations.
Explained here :
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by jinonicolas on 2009-02-24
No luck for me using grub. I did everything this [link]("https://help.ubuntu.com/community/Installation/FromWindows") told me to and I ended up with Grub not finding the iso image even if I had the alternate Ubuntu iso in hd-media. (I found this guide to use grub with downloaded iso's...just lost the link lol)

As for loadlin, what do I have to do to make it use the downloaded alternate ubuntu iso from the primary partition?

---

### Post by albinootje on 2009-02-24
> **jinonicolas said:**
>  As for loadlin, what do I have to do to make it use the downloaded alternate ubuntu iso from the primary partition?

I assumed that loadlin.exe would work with every version of MS-Windows, but apparently not.
The link for loadlin.exe in the page [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) is also broken.
Here's more info on loadlin :
[http://en.wikipedia.org/wiki/Loadlin](http://en.wikipedia.org/wiki/Loadlin)
which also has a valid download link for loadlin.exe

I suggest you keep trying with Grub for DOS, or find some other old laptop that has a working cdrom or dvd-drive.

Good luck!

---

### Post by jinonicolas on 2009-02-24
Yeah, my dilemma is mainly if this old laptop is still good for something so I'm really hesitant to buy new parts for it until I find it useful enough. I don't know if borrowing and using an external optical disk drive would help since I don't have any usb 2.0 ports aside from the one in my pcmcia. I tried booting into an external hard drive...still nothing.

I'll try some more with grub. Maybe I got something wrong...I keep getting that error that the iso could not be found for various reasons. Right now, I have ubuntu-8.10-alternate-i386.iso. Although, I am also assuming that this is the alternate ISO the guides are saying. I'll download another alternate ISO while I'm sleeping.

Thanks for all the help!

BTW...would using an older version of Ubuntu help me with my problems with Grub?

---

### Post by jinonicolas on 2009-02-24
Up!

---

### Post by jinonicolas on 2009-02-25
Up!

---

