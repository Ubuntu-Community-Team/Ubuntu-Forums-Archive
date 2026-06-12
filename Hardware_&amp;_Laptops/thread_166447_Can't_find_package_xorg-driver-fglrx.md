---
title: "Can't find package xorg-driver-fglrx"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by konstandinos on 2006-04-26
(I have started a new thread on this even though I've already mentioned it in another post as one of my replies)

Hi I cannot get fglrx driver to install.

(amd64, radeon x550)

I've done some research and everyone recommends I use the fglrx drivers. Problem is that when I try 'sudo dpkg-reconfigure xserver-xorg', the fglrx drivers are not present on the list.

So I proceed to try install them. First I type 'sudo apt-get install linux-amd64-generic', which just confirms that my kernel is already up to date. Then I type 'sudo apt-get install xorg-driver-fglrx' but I get the error 'E: Couldn't find package xorg-driver-fglrx'.

Now I am stuck. I have tried placing the Ubuntu Live Cd in my cdrom drive, and have checked that the deb cdrom line is uncommented in /etc/apt/sources.list - but it still doesn't install (same error).

What am I supposed to do next?

I hope someone can help.

Thanks,
Konstandinos.

---

### Post by daWabbit on 2006-04-26
If I recall correctly, ATI drivers are not free software and so are not included in the repos. You'll have to get them from ATI, themselves. I didn't have much time to search, but here is a page from their FAQ which ought to get you off to a decent start. 

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Jack

---

### Post by konstandinos on 2006-05-02
Hi

I thought I'd follow up on my post by explaining my short term solution, should anyone else find this info useful.

The Breezy Badger Ubuntu install Cd (the one that fits on 700mb) does not contain the fglrx drivers. So there are three possible solutions:

One is to download the proprietary ATI drivers and manually configure those, or, to get your hands on the Ubuntu DVD (which I've been told comes with all/most packages, including fglrx drivers), or, which is the solution I am temporarily using, just select vesa as your video driver when configuring xserver.

ie: if you're using an ATI card, and can't get fglrx/ati drivers to work, and are only needing standard 2d graphics (like me), then when you type "sudo dpkg-reconfigure xserver-xorg" just scroll down and select "vesa" as your driver, and you should have X working when you reboot.

Works for me anyway. Hope this is of help to somebody.

---

### Post by jimtang on 2007-12-28
I had exactly the same error "Couldn't find package xorg-driver-fglrx" as yours, and luckily I sorted it out!! 
I'm using ubuntu 7.10. It could be sightly differ in lower versions.

System -> Administration -> Software Sources ->
Tick all choices, especially Universal and Restricted.

Cheers.
Jim

---

### Post by pjhartt on 2008-03-09
I have had this problem. I am extremly new to Linux of any sort. When you click the restricted drivers manager to install the driver it tries to load three files / packages. If you are not connected to the internet at this point, it seems that you cannot get the required drivers. 

My way to sort this problem out was to re-install the system and connect a wired network connection, alternately I think you could be connected to a wireless network.

If you have not connected to the internet and try to download the package xorg-driver-fglrx, later when you are connected, it fails to install. It may be that you have to individually install each of the three files / packages in order to get xorg-driver-fglrx to install correctly.

The three / packages files that are loaded (when connected) in this order are

1) gcc-3.3-base
2) libstdc++5
3) xorg-driver-fglrx

Whether these can be downloaded individually I don't know, but I do hope this information is of use to someone and it does seem like a bug that you cannot get it to load once you have tried and are not connected to the internet.

I am running Ubuntu Desktop 7.10

---

