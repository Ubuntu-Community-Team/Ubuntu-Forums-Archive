---
title: "USB in Virtualbox, 9.04"
date: 2009-05-04
forum: Hardware
---

### Post by arak on 2009-05-04
After I installed Virtualbox and Guest additions on my Aspire One Netbook, I found that the USB options were grayed out.  I'm a noobie, so I checked all over the web to find out how I could activate the USB ports in XP which I had installed inside of Lenux.

All of the solutions seemed so complicated.

Here is my simple solution.  Go into Administration>Users and Groups> and click on the highlighted item. Then Unlock>Authenticate>Properties>User Priviledges.  At the bottom of the list you will notice "use Virtualbox." Click it and OK and then reboot.

You should be able to see your USB items.  I assume that you first will need to add the USB filter before you actually start up your guest OS.

I would be interested if it works for you too.

---

### Post by freonchill on 2009-05-04
are you using the 'open source' or 'free' virtualbox?

---

### Post by arak on 2009-05-04
Free version downloaded from the VirtualBox Website.

---

### Post by freonchill on 2009-05-04
both are "free" from their website, but one lacks usb virutalization

[http://en.wikipedia.org/wiki/Virtualbox#Licensing](http://en.wikipedia.org/wiki/Virtualbox#Licensing)

---

### Post by arak on 2009-05-05
The one with USB.  Its a .deb file.

---

### Post by hunter186 on 2009-05-08
Works great!  Thanks a bunch.  I had the same problem using Virtualbox on 9.04.  Under Hardy, I think I had to make some fstab changes to get USB working properly, but I'd read this wasn't necessary on Jaunty.  

Thanks again.

---

### Post by Billsputters on 2009-05-08
Is there any way of telling which version you have installed?  I think the OSE version doesn't have the USB options in the settings window. 

Because I just can't get USB to work.

---

### Post by markcynt on 2009-05-09
> **arak said:**
> After I installed Virtualbox and Guest additions on my Aspire One Netbook, I found that the USB options were grayed out.  I'm a noobie, so I checked all over the web to find out how I could activate the USB ports in XP which I had installed inside of Lenux.

All of the solutions seemed so complicated.

Here is my simple solution.  Go into Administration>Users and Groups> and click on the highlighted item. Then Unlock>Authenticate>Properties>User Priviledges.  At the bottom of the list you will notice "use Virtualbox." Click it and OK and then reboot.

You should be able to see your USB items.  I assume that you first will need to add the USB filter before you actually start up your guest OS.

I would be interested if it works for you too.

This way was very easy and worked fine for me but when I opened Users and Groups root was highlighted, so I chose my user account and gave it VirtualBox privileges. Great tip!

---

### Post by markcynt on 2009-05-09
> **Billsputters said:**
> Is there any way of telling which version you have installed?  I think the OSE version doesn't have the USB options in the settings window. 

Because I just can't get USB to work.

You need the [Ubuntu 9.04 version on this page]("http://www.virtualbox.org/wiki/Linux_Downloads"), provided your using Ubuntu 9.04 of course.

---

