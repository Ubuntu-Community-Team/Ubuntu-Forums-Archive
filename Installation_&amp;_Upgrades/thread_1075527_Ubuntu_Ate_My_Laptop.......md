---
title: "Ubuntu Ate My Laptop......"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by amclpreston on 2009-02-20
Hi

I've just tried to install Ubuntu 8.04 on my laptop and it hasn't worked.....

Just to recap.., Its an Acer 527 Travelmate, about 750Mhz, 10Gb Hd that had Windows XP on it. I use it mainly for surfing, with a USB Mobile Broadband connection, no landline. I'm in a poor signal area, so speed on the internet is poor. However, recently its gone from poor to abysmal to "Got to do something about this..."

I read around forums that said Ubuntu was much faster on surfing than XP. I have an Ubuntu disc, and have just tried to install it.

I chose the full reboot now option , and the thing started off, cd drive whirring away, got the moving bar on the screen, then the African bird, then some menu words across top of the screen, then a couple of icons under that, Examples, and Install. And the CD drive keot whirring, and whirring, and ..., an hour later it was still whirring, but nothing else was happening.

I had a cup of tea, went back to it and prodded the eject button, in the hope that a message like... "Abandon, or continue install?" would come up. Nothing at all happened, so I switched it off by pulling the plug out of the wall. 

Start again. Except this time, when the install options came up I chose the one which said something like..."Install, boot from Cd with a little help" and off it went, and at some point abit later a little message flicked up which said "Installer needs 256 Mb memory, you have 255Mb, installation may fail, continue?"  So I thought, well, I mean its got just about everything it wants.... so pressed continue.

And it very slowly, slowly, indeed took me through the 7 step part about language, country, keyboard type etc, and the bit about overwriting the hard disc completely, and it all seemed alright, though incredibly slow and then it all went silent, nothing. I left it like that for 10 minutes to see if it would spring to life. But no. 

So thought, ********. I'll reinstall XP, only to remember that the XP disc that I have is an upgrade disc not one you can just install straight off. So I pulled out an old Windows 98 system disc to start from scratch...., and it rapidly came up with a command error, or memory failure message.....

So I'm not a very happy bunny at all. This is the second time I've tried Linux. About 2 years ago I installed the then current version of Ubuntu, only to find that Linux didn't seem to like winmodems very much, and so returned to XP.

So what now, anyone with some advice? Is it going to need one of those fixit cd's that'll reformat the hard disc or..?

Any way round this?

Andrew

---

### Post by insineratehymn on 2009-02-20
Well... sorry first of all.

I assume that you're using a live CD installation disk. I would definitely use an alternate CD installation disk. It does the exact same thing, except it does it with CLI graphics instead of gnome; it runs much faster and much smoother. Sure, you don't get a nice map telling you where your time zone is or a fancy text box to test your keyboard but it does the trick.

Also, on a comptuer this slow I would consider a stripped down version. Yes, Ubuntu is "faster" that surfing; but I would compare the resources needed to run Ubuntu to being a little less than XP. You get alot more out of what you got, but it isn't a miracle system.

---

### Post by amclpreston on 2009-02-20
Granted , this machine is getting on. But 750Mhz isn't all that slow, or prehistoric. And 2 years ago, it loaded up Ubuntu fine, and since then it has loaded up XP fine. So I don't really accept ... unless Ubuntu is bigger, fatter, requires more resources to install than XP...  

The install disc is one I bought from someone on ebay who sells these regularly, If I remember, downloading looked like a very long job, so I took what seemed the more straightforward approach. Thank you for quick response

Andrew

---

### Post by insineratehymn on 2009-02-20
Youre welcome for the response. DLing the ISO, on anything other than dialup takes about 4 hours at most; I wouldn't pay for something that is distributed for free.

Ubuntu states their system **requirements** as follows:
> # 300 MHz x86 processor
# 64 MB of system memory (RAM)
# At least 4 GB of disk space (for full installation and swap space)
# VGA graphics card capable of 640x480 resolution
# CD-ROM drive or network card 

from: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

However, it states its **recommended** requirements as follows:
> # 700 MHz x86 processor
# 384 MB of system memory (RAM)
# 8 GB of disk space
# Graphics card capable of 1024x768 resolution
# Sound card
# A network or Internet connection

from: same site

It also states after that even with these **recommended** requirements that visual effects may "...not run smoothly."

Remember, 8.10 comes out of box with compiz; which to describe best in two words is "processor heavy".

For the heavy stuff, they suggest:
> 
# 1.2 GHz x86 processor
# 384 MB of system memory (RAM)
# Supported graphics card

from: same site


Ill tell you this... even with that, you are really pushing it with compiz.

I bet if you installed just a shell on that computer it would fly. ;)

---

### Post by amclpreston on 2009-02-20
It isn't flying anywhere right now, Ubuntu has eaten the hard disc.

This laptop is how I earn a small living from a couple of websites.
And If Ubuntu has grown, big and fat, and resource hungry whatever it
says on the pack, perhaps the 'pack' needs to change.  

Is this something that I can recover from, or is it the fixit cd's that it needs?

Sorry if this sounds a bit ungracious, but at root, earlier today the machine worked, and now
it doesn't.

---

### Post by insineratehymn on 2009-02-20
You can try reinstalling the system if you like, but if you suspect an HD failure I don't think you're going to get very far with that either. I hardly see an OS eating a hard drive, though. Try the fixit option, I've never tried it before and I really have no idea what to expect from it.

---

### Post by amclpreston on 2009-02-28
> **amclpreston said:**
> Hi

I've just tried to install Ubuntu 8.04 on my laptop and it hasn't worked.....

Just to recap.., Its an Acer 527 Travelmate, about 750Mhz, 10Gb Hd that had Windows XP on it. I use it mainly for surfing, with a USB Mobile Broadband connection, no landline. I'm in a poor signal area, so speed on the internet is poor. However, recently its gone from poor to abysmal to "Got to do something about this..."

I read around forums that said Ubuntu was much faster on surfing than XP. I have an Ubuntu disc, and have just tried to install it.

I chose the full reboot now option , and the thing started off, cd drive whirring away, got the moving bar on the screen, then the African bird, then some menu words across top of the screen, then a couple of icons under that, Examples, and Install. And the CD drive keot whirring, and whirring, and ..., an hour later it was still whirring, but nothing else was happening.

I had a cup of tea, went back to it and prodded the eject button, in the hope that a message like... "Abandon, or continue install?" would come up. Nothing at all happened, so I switched it off by pulling the plug out of the wall. 

Start again. Except this time, when the install options came up I chose the one which said something like..."Install, boot from Cd with a little help" and off it went, and at some point abit later a little message flicked up which said "Installer needs 256 Mb memory, you have 255Mb, installation may fail, continue?"  So I thought, well, I mean its got just about everything it wants.... so pressed continue.

And it very slowly, slowly, indeed took me through the 7 step part about language, country, keyboard type etc, and the bit about overwriting the hard disc completely, and it all seemed alright, though incredibly slow and then it all went silent, nothing. I left it like that for 10 minutes to see if it would spring to life. But no. 

So thought, ********. I'll reinstall XP, only to remember that the XP disc that I have is an upgrade disc not one you can just install straight off. So I pulled out an old Windows 98 system disc to start from scratch...., and it rapidly came up with a command error, or memory failure message.....

So I'm not a very happy bunny at all. This is the second time I've tried Linux. About 2 years ago I installed the then current version of Ubuntu, only to find that Linux didn't seem to like winmodems very much, and so returned to XP.

So what now, anyone with some advice? Is it going to need one of those fixit cd's that'll reformat the hard disc or..?

Any way round this?

Andrew

Small update...

I did buy a fixit disc, removed the Linux partitions from the harddrive, and reset it as empty except for the Master Boot Record.

I then got a CD of Ubuntu 8.10, ordered as the i386 (alternate version I think it's called) to try to reduce the 'installation strain'. When I received the CD there didn't seem to be much that identified it as any different to a standard 8.10 distro. I tried to install, system fell over.., it went illegal , I think it used to be called, with a stream of I/O errors. 

I played around with the menu, function keys..., until at some point I tried to get out of something..., pressed 'Esc' and the whole thing went off and started to install, and did so successfully. 

Now.....

My preferred browser is Opera, because I found under Windows XP seemed to be a bit faster than Firefox, and also seemed to be able to 'hang on' better in my rather poor signal UK '3' network usb mobile brodband area. That is, it seldom dropped the connection.

So this morning, I downloaded Opera for Linux, Ubuntu.  It's got its icon on the desktop, ready to install. As I'm new, I then went to Add/Remove programs.... and that seems to refer to the various Linux packages. So I clicked on the Opera icon on the desktop to see if I can install it from there, and it opened a new window in the middle of the desktop..'Package Installer -opera" and a little message which said....

Status : Error - Dependency not satisfiable : libqt3-mt

and it wouldn't go any further.

Is this familiar to anyone?

Thank you
Andrew

---

### Post by ikisham on 2009-02-28
The most simple answer to that is: go to System>Administration>Synaptic Package Manager, then search for libqt3-mt, mark for installation and install it. Do the same thing if anything else is missing (I _suppose_ the package in Add/Remove.. is made for full ubuntu installs).

---

### Post by amclpreston on 2009-02-28
> **ikisham said:**
> The most simple answer to that is: go to System>Administration>Synaptic Package Manager, then search for libqt3-mt, mark for installation and install it. Do the same thing if anything else is missing (I _suppose_ the package in Add/Remove.. is made for full ubuntu installs).

Thank you for fast reply. I've just tried it, and the search comes up with nothing for  libqt3-mt

---

### Post by ikisham on 2009-02-28
The most up-to-date is Qt4 (it's what I have installed). But to stay in safe grounds search for qt3 (see the picture attached). Also make sure you have 'main', 'universe', 'restricted' and 'multiverse' enabled in System>Software Sources.

---

### Post by ikisham on 2009-02-28
..

---

