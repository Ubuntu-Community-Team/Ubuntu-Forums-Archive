---
title: "Wacom Bamboo Fun Driver install help please (9.10)"
date: 2009-12-23
forum: Hardware
---

### Post by chris_0076 on 2009-12-23
Hello this is my first post here. 

I just installed Ubuntu and I am in the process of finalizing installation of ins and outs. When I went looking for how to install the tablet, man oh man. I don't ave the slightest idea of what I am supposed to do. I have seen many sites that tell how to install for other versions and how to install at uber-hacker level but I have yet to find somewhere that I could easily understand as to how I may get my tablet to work.

I have the xserver-xorg-input-wacom and wacom-tools packages installed. I have the driver downloaded and it is sitting on on my desktop... but I have no clue what to do with it. I have the tablet sitting right in front of me. The tablet does work as a mouse at the moment if that helps. It just has no pressure sensitivity.

I know almost nothing about Ubuntu but I am trying to learn. So any help that I get whether it be in general Ubuntu usage things or hacks or something that will get my tablet to work would be greatly appreciated.


Short:
I am knew to Ubuntu; please help me.
My Wacom Bamboo Fun tablet des not have pressure sensitivity.
I have xserver-xorg-input-wacom and wacom-tools installed.
I have the 0.8.4-4 driver downloaded.
I hope this is the correct forum.



Thanks for any and all help,
Chris

---

### Post by Favux on 2009-12-24
Hi chris_0076,

Welcome to Ubuntu Forums!

Which model Bamboo Fun do you have?  Is it one of the new Pen and Touch models?

---

### Post by chris_0076 on 2009-12-24
No it is one of the old ones.

---

### Post by Favux on 2009-12-24
Hi chris_0076,

Ok, just check in Synaptic Package Manager that both xserver-xorg-input-wacom & wacom-tools are installed (search 'wacom').  If not install whatever isn't installed and reboot.  Then go to [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") in the "Re: Wacom tablets in Ubuntu guide/howto" thread.  Install one of the modified wacom.fdi's following the instructions.  Since you have a usb tablet it would be either the .fdi mentioned in 1 or 3.  There's a link to set up wacomcpl and another for your pad.  Then you should be good to go.

---

### Post by chris_0076 on 2009-12-24
Thanks, It works now. At first it did not have any pressure sensitivity in GIMP but I found this site:
[http://twodayslate.wordpress.com/2008/01/20/wacom-tablet-in-ubuntu/](http://twodayslate.wordpress.com/2008/01/20/wacom-tablet-in-ubuntu/)
at the end it tells you how to configure it to work.

Hope this helps someone later.
Chris

---

### Post by chris_0076 on 2009-12-24
More problems! I just rebooted and it will not let me log on saying something about the GNOME Power Manager has problems. What do I do? Right now I am using my ubuntu CD so that I can post this.

The only thing that I have done other than setting up the tablet is making Gimp-Painter. It had just finished so I restarted and now it does not work. Should I just do a clean install and start over?

EDIT

I also commented out the line
#. /etc/X11/Xsession

in the xinitrc file at /etc/X11/xinit

```
#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
#. /etc/X11/Xsession
```


I guess this is kind of outside of the scope of this forum... should I move the topic?

---

### Post by Favux on 2009-12-24
Hi chris_0076,

Good!  Looks like you've got everything working.

The Wacom stuff wouldn't have anything to do with the problems you're having now.  If you hadn't commented out the line in xinitrc you'd be "looping", which is not what's happening now.

You should start a new thread if you can.  The gome power manager issue is separate from what you did for the Bamboo.  Either in Hardware and Laptops forum or in the Installation and Upgrade forum.

---

### Post by chris_0076 on 2009-12-24
Oh... ok good to know it is not the tablet.

Thank you very much for all of your help!

---

