---
title: "[SOLVED] Logitech Harmony 1000 - Touch Screen Universal Remote Control"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Goodson1974 on 2007-06-04
Hi all
 
I'm looking to purchase a Logitech Harmony 1000 universal remote, and was wondering if it can be used with Ubuntu.
 
From the info i've got, the software (suprise suprise!) is for Windows or Macs only.
 
If anyone knows if it can be set up and programmed using Ubuntu, then my XP partition can finally be converted to Ext3!
 
Cheers :D

---

### Post by reiki on 2007-06-08
I have the Harmony 880. I can update using WinXP in a Virtual Machine using VirtualBox. I just got it working today (just installed VirtualBox for teh first time last night). So it's not real hard to do and if you read teh user manual for VirtualBox, the information you need is there. I can help you if necessary, but you'll probably have it running in no time if you just follow teh instructions for USB in the user manual. The USB is the hardest part of the Harmony remotes in linux. Because the remotes disconnect and reconnect while updating. 

VirtualBox is the only FREE way I've found to do the HArmony updates in linux. I think VMWare Workstation might be able to handle the USB, but it costs a couple hundred dollars. VMWare Server is free but doesn't handle the USB properly. VirtualBox works.

This won't, technically, free you from WinXP.... but at least you can update your remote without having to reboot to XP on another partition. My entire directory that holds the virtual machins is only 1.9GB. So I have a complete WinXP install in a VM using only 1.9GB of space. Yes it will grow if I install more stuff into it. But I only really needed it to update my remote :)

---

### Post by Goodson1974 on 2007-06-19
Thanks for that Reiki
 
I'll give it a try next week, as i've been away and i'm off again tomorrow!
 
Sounds like it could well work though :p

---

### Post by karhulitos on 2007-08-02
I have tried to find a simple way to update my Harmony 525 on Feisty. I yesterday found some activity at [http://sourceforge.net/projects/harmonyremote/]("http://sourceforge.net/projects/harmonyremote/")
but I'm perhaps too noob to get anhthing downloaded from there. There was a another page in some corner of the web but I lost it. If my memory serves me ok, they had something to d/l from there.

Will keep searching..

[edit] this is the link I mentioned [http://www.phildev.net/phil/blog/index.php?title=harmony_software_for_linux_is_here&more=1&c=1&tb=1&pb=1]("http://www.phildev.net/phil/blog/index.php?title=harmony_software_for_linux_is_here&more=1&c=1&tb=1&pb=1")
[edit2] tried that code (harmony 0.9) but failed to update Harmony 525, throws something like
```
<head><title>Object moved</title></head>
<body><h1>Object Moved</h1>This object may be found <a HREF="/EasyZapper/Error.asp?WarningType=GetUserId%28%29%3A%20No%20user%20logged%20in&amp;ErrorPage=%2FEasyZapper%2FNew%2FProcConnectivity%2FConnectivity%5FReceive%5FZaps%2Easp&amp;ErrorType=">here</a>.</body>

```

---

### Post by Goodson1974 on 2007-08-29
Hi Reiki

I've finally got round to installing Virtualbox and i was surprised at how straight forward it all was to set up XP!

The only trouble I'm having is getting the remote to be recognised.

I enabled all of the usb connections (I think!!) and I'm getting an error which I don't understand.

I've attached a screenshot of the error.

Any help would be greatly appreciated :)

---

### Post by Goodson1974 on 2007-09-04
I fixed this problem by installing the additions iso.

---

### Post by svtfmook on 2007-09-04
excellent, i will have to try this with my h-550.

wonder if this would work with sync'ing wm6 devices too.

---

### Post by Spinalcracker on 2007-09-24
A program for all Harmony Remotes that runs natively on Linux can be found here:

[http://sourceforge.net/projects/harmonycontrol/]("http://sourceforge.net/projects/harmonycontrol/")

Or here:

[http://downloads.sourceforge.net/harmonycontrol/harmony-0.11.tar.bz2?modtime=1188577190&big_mirror=0]("http://downloads.sourceforge.net/harmonycontrol/harmony-0.11.tar.bz2?modtime=1188577190&big_mirror=0")

Once downloaded, extract... open a terminal and CD to the extracted folder... run sudo ./configure...  once done run sudo make install.  This will install to /usr/bin

Note:  libusb package must be installed first.  This can be grabbed from synaptic or apt-get

---

### Post by hebetude on 2007-12-29
Note: you can't update via harmonycontrol (as they state in their forums).  I apparently did update my remote via this tool, but couldn't ever get it reconnected.  I even went through all the manual unbinding of usb devices etc etc. and just couldn't get it to reconnect.

Also, the interface via windows is a million times better.  They apparently only distribute an older version of the update website via normal web browsers.  However, they have a very nice website for the super-lame proprietary browser tool.

I hate buying windows hardware for all the above linux incompatibilities, but since you don't find out about bs like this until after you buy something.  BTW, that standard looking usb cable that comes with it is no normal usb cable.  I tried using a more conveniently sized usb cable and the remote software for windows wouldnt connect to it.  One day I will get over this logitech fetish and my linux computing will be much more straight forward :)

---

