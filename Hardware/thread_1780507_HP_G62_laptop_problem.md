---
title: "HP G62 laptop problem"
date: 2011-06-12
forum: Hardware
---

### Post by Grecomon on 2011-06-12
Dear Sir ,Madam
 
I have problem with my HP g62-b75ev laptop, at first I could install 11.04 latest version, but later a complete blank screen would appear at startup when I boot from ubuntu, I reinstalled 2-3 times 11.04, still same problem, later I couldn't even install 11.04 so I installed 11.04 LTS, still same problem, I could work the laptop for a bit, but later same problem.
 
I noticed that the problem appeared after I worked with my terminal or I installed ati drivers for linux.
 
Thank you all in advance.
 
Technical Characteristics:
Intel Core i5-460M (2.53GH)
4GB DDR3
Ati Mobility RadeonHD 5470 1GB Dedicated
3 USB 2.0 , Vga-out

---

### Post by mörgæs on 2011-06-12
Hi, welcome to the fora.

There have been a lot of problems with closed-source drivers lately. How does the computer behave if you install and stick to the open source drivers?

---

### Post by Grecomon on 2011-06-12
What do you mean open source?
 
Could you give me some more informations about this?
 
Also I forgot to mention, that my laptop has 2 graphic cards and switch them at my command, one on board and the other the ATI HD mobility radeon

---

### Post by mörgæs on 2011-06-12
If you do a plain installation, the open source drivers will be used initially, but later the system shows the option of using 'restriced', 'proprietary' (or something similar) drivers. 

What happens if you ignore this and stick to the initial drivers?

---

### Post by webofunni on 2011-06-12
Is this a hybrid graphics system ?

---

### Post by Grecomon on 2011-06-12
> **webofunni said:**
> Is this a hybrid graphics system ?
 
Yes, one intel graphic card  and one ATI graphic card

---

### Post by Grecomon on 2011-06-12
> **mörgæs said:**
> If you do a plain installation, the open source drivers will be used initially, but later the system shows the option of using 'restriced', 'proprietary' (or something similar) drivers. 
 
What happens if you ignore this and stick to the initial drivers?
 
Haven't tried it yet, but I don't think it will be a good choice

---

### Post by webofunni on 2011-06-12
> **Grecomon said:**
> Yes, one intel graphic card  and one ATI graphic card

Yes, then installing ati driver may create problems. remove them. If you want to use the external graphics card, use the bumblebee [http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Bumblebee](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Bumblebee)

---

### Post by Grecomon on 2011-06-12
> **webofunni said:**
> Yes, then installing ati driver may create problems. remove them. If you want to use the external graphics card, use the bumblebee [http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Bumblebee](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Bumblebee)
 
And what would this do?
Allow me to switch between graphic cards as also fixing my problem?

---

### Post by webofunni on 2011-06-12
Your problem, I guess came from the driver that you installed recently. Remove them and use that to switch graphics cards

---

### Post by Grecomon on 2011-06-13
> **webofunni said:**
> Your problem, I guess came from the driver that you installed recently. Remove them and use that to switch graphics cards
 
During the installation, it writes that ot changes between nvidia and intel.

THe problem is that I have an Ati and an Intel

---

### Post by lingo-zh on 2011-06-13
> **Grecomon said:**
> During the installation, it writes that ot changes between nvidia and intel.

THe problem is that I have an Ati and an Intel

_[]("http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Vga_switcheroo")_how about vga_swotcherool? you can have a try.here is the link [http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Main_Page)

---

### Post by webofunni on 2011-06-13
> **Grecomon said:**
> During the installation, it writes that ot changes between nvidia and intel.

THe problem is that I have an Ati and an Intel

If you are able to install that successfully then install glxgears in the system and try 

glxgears

and 

optirun glxgears 

observ the f per s in the o/p. If you are able to find a huge difference then that means that bumblebee is working. 


Also this is a new package. They do have a launch pad page at [https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux) and a mailing list. Register at mailing list and ask them about the problems that you are facing or file a bug report, if it is not working.

---

