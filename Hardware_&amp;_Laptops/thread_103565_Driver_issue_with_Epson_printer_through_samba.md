---
title: "Driver issue with Epson printer through samba"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by Michel F on 2005-12-14
I have an Epson cx6600 printer connecte through USB on a XP box. On my Ubuntu box, I have configured samba to share files with the XP box and to print remotely.
That works well if I use the GimpPrint drivers (I use the cx6400 in absence of a cx6600 driver).
I tried to install the epson-avasys drivers (pips). It does not work.
It seems that if one follows the installation instructions carefully, the only possibility is to have a usb connected printer : The port used is a "file" port (ekplp:) and then the epkd daemon redirects the "file" port to /dev/usb/lp0.

Has anyone ever tried (and get working) such a configuration ?

Help appreciated.

Michel

---

### Post by teaker1s on 2005-12-14
cx6600 driver Doesn't work, I'm using 8300 with gimp print, I think you need cups to get it to work if networked on ubuntu, if on xp it's SMB option possibly-try it I'll be honnest I don't know if it will or won't work

gksudo gnome-cups-manager

---

### Post by Michel F on 2005-12-14
Thank you teaker1s.

Using a gimp print driver works (I use the cx6400) with cups and samba. So connectivity is ok.

I am just trying to use the avasys driver in the same context.

---

### Post by DUNC4N on 2005-12-16
Wow, I have a CX6600 hooked up to my main rig, and I would very much know how you got it to work. I just figured out the networking thing sorta. Could you give me instructions step by step? I would really appreciate it.

Thanks.

**Edit, so far I did apt get samba, and I can see my ubuntu machine from my windows machine

---

### Post by Michel F on 2005-12-16
Hi Duncan,

As you can see, I am labelled as a "Ubuntu Newbie Brew", and that's what I am. So, if I have my printer working, it's perhaps more luck than skill...

My cx6600 is connected by USB to a XP PC. On this XP PC, I have configured the network wizard with Workgroup name = MYNETWORK and PC name MAIN. I have set the printer as shared and put CX6600 as share name.

On my Ubuntu PC, I have installed the samba package, with synaptic. I have set the network working (System>administration>Network) and defined the workgroup as MYNETWORK and the PC name as LAB

Restart Ubuntu.

That was enough to enable me to shre folders two-way between tht two PCs.

Then, I have configured the printer (system>Administration>Print).Choose Network print. Select samba. You then have a popup for you to input a Windows username and password. Then a window for you to input the Windows host name (MAIN) and the Windows share name for the printer (CX6600). You then have to select the printer make (Epson) and model to point to the correct driver in the GIMP-PRINT list. Here choose either CX6400 or CX8400, since CX6600 is not supported by GIMP-PRINT. I have it work with both.

I suggest to restart again Ubuntu. And it worked for me. Maybe for you also.

---

### Post by DUNC4N on 2005-12-16
Hey thanks Michel, I'll give it a try when I get home.

---

### Post by Michel F on 2006-01-05
Any idea ?

PS: Happy new-year everybody!

---

### Post by Michel F on 2006-02-03
Well, this is not a sound thread so, no success...
I also posted something on Epson avasys's forum. It's so silent there, you could hear a fly scratching its back...
Has anyone out here tried to accomplish what I want, ie use the epson avasys driver in a network ?
Help appreciated.

---

### Post by teaker1s on 2006-06-06
since last time there is a new driver avaliable that I created a deb package using alien and the correct epson driver will now print

[http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)

---

