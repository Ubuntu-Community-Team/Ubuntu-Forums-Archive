---
title: "Problem with Toshiba R100 PCMCIA CD-ROM"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by pht on 2005-04-13
I am trying to run the Ubuntu Live CD on my Toshiba R100. It boots ok (from the PCMCIA CD-ROM), but Ubuntu fails to detect the CD-ROM. I am given the option to manually select which module to use to install the CD-ROM, I do not understand these options. I do not have access to a floppy-drive.

Does anyone know how to solve this problem?

---

### Post by pht on 2005-04-14
What I find wierd is the fact that I can boot from the CD, but that the Ubuntu-installer (or whatever it's called) cannot find the drive later.

---

### Post by Q4U on 2005-04-14
Hi:

I guess you are referring to the Install CD (not the Live CD, which does not use an installer and spits out a different error, on my laptop at least). Correct me if I am wrong.

I have a Toshiba laptop, too (an oldish Portege 3490 bought on ebay). It has a PCMCIA CD-ROM like yours. And I have had the same problem: the installer seems to have problem recognizing the PCMCIA.

However, I found that Warty has no problems: when trying to mount the CD-ROM, it loads the PC Card module and proceeds with the installation.

So a possible solution would be to install Warty and upgrade to Hoary over the network (using dist-upgrade). Of course, this is practical only if you have a broadband connection.

I have not had time to try this solution yet, but you might give it a shot if you feel adventurous (I have heard that a network upgrade is not always trouble-free).

Hope this helps.

Q4U

---

### Post by pht on 2005-04-14
Thank you for the tip!

I am actually using the Live CD, but I did not know how to refer to the setup procedure. (Maybe setup is a more apropriate word. :))

Actually I am not really interested in installing Ubuntu on my laptop, yet. I just wanted to test it. I tried the Live CD on my desktop and everything worked so perfect and smooth. Maybe it is easier to install Ubuntu than to use the Live CD, but I wanted to try it first, since I have heard about a lot of problems concerning Linux and laptops.

I think I will try the Warty Live CD first.

Thanks again!

---

### Post by Q4U on 2005-04-14
Actually, Ubuntu is just about the best distro as far as laptop hardware detection and configuration are concerned (in my limited experience of course).  Having said this, ultraportable laptops like ours are very difficult to support due to the unusual hardware sometimes used to save space.

I suggest you look at this site: [http://www.freed.net/opensource/R100.html](http://www.freed.net/opensource/R100.html). It contains the experience of a guy with your system running Debian (i.e. Ubuntu's "father") and a few useful links. After a cursory glance, I am quite optimistic in your case as the Ubuntu developers are putting a lot of effort in supporting the Centrino chipset (e.g. wireless networking should work) and your modem (a well-known sore spot for Linux laptops) seems to work.

Another hint: don't assume that the Live CD and the Install CD always behave in the same way (they don't in my case). A relatively easy and safe option to test your system is replacing the hard drive with another one (if available) and install ubuntu on it.

Hope this helps!

Q4U

---

