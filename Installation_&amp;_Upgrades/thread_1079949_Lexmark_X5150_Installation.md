---
title: "Lexmark X5150 Installation"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Valburgh on 2009-02-24
Greetings, masters of Ubuntu.

I'm new to Ubuntu and installed it a few days ago.
I needed a OS that actually does the work for what it is made for whithout getting stuck between it's own software.
Ubuntu, Linux Kernel, Stable, +Wine for microsoft based software = Usfull.
However, wrong auto installed driver (for X5100), no driver for Webcam, etc. = the problem.

What must I do to make the Lexmark X5150 run on Ubuntu 8.10?

Pls. Don't send me back to the Microsoft jail.
I'm just starting to love Ubuntu.
I pimped up my Ubuntu, and it is still only using 28% of my RAM.
Further I'm starting to understand the Terminal system.

Ps. I checked up though Google, but the only thing I herd of was the lexmarkz55-CUPS-1.01 (driver?)and the  N5WSU.HQX driver from the Lexmark site. I couldn't install the z55, but I herd it worked on the Ubuntu 8.04.

The N5WSU.HQX however, was not supported by th Ubuntu system.

There must be a way for me to install this, or else I must reinstall Windows XP or buy another Printer and I prefer none of these suggestions.

Help?

---

### Post by BGFG on 2009-02-24
Hey, I have a lexmark X5410 and i'm sorry to say that their support in Linux is abysmal at best. I actually re-installed Xp and now dual boot due to my incompatible printer and webcam. 

I would suggest however, that rather than going all the way back to windows, you install windows in VirtualBox [http://www.virtualbox.org/](http://www.virtualbox.org/) and simply have a shared folder between the two OS'es. This way you can quickly start windows and print if you need to, but keep the stability and security of Ubuntu.

---

### Post by Chonnawonga on 2009-09-25
I'm a little late to the party here, but...

You can get the 5150 working with the Lexmark Z55 drivers. Just search for "Lexmark" in Synaptic and you'll find it.

Note that this also works for the Dell A940, which is just the Lexmark X5150 rebranded. In fact, you can even save money by using Lexmark's ink cartridges instead of Dell's marked-up ones. You just have to take a knife to the inside of the printer, because they put the little branding tabs in different spots on the cartridges.

---

### Post by lance bermudez on 2010-03-13
c2050 Lexmark 2050 Color Jetprinter Linux Driver is the only thing i found under synaptic with a search of "lexmark" is this the driver for the lexmark x5150 printer?

---

### Post by Chonnawonga on 2010-03-14
Hi Lance,

No, that won't work. (At least, I don't think so.) Sadly, this has become more difficult to install since about 9.10. So, try this:
[http://www.unixmen.com/hardware-linux/339-howto-setup-lexmark-z55-printer-in-ubuntudebianmint]("http://www.unixmen.com/hardware-linux/339-howto-setup-lexmark-z55-printer-in-ubuntudebianmint")

If you're having trouble finding that file, just go to the Lexmark site, go to downloads, and search for CJLZ55LE-CUPS-1.0-1.TAR.GZ

Good luck!

---

### Post by KMcCMedia on 2011-01-21
For the current release Natty 11.04 go here and note the comment at the end

[http://www1.ubuntuforums.org/showthread.php?p=10384353](http://www1.ubuntuforums.org/showthread.php?p=10384353)

I have a dell A940 printer - Essentially a Lexmark - Working fine with this driver.

---

### Post by ub-khalid on 2011-08-08
Hello

I have **Lexmark X5150**

Is here someone who can explain to me step by step how to install my printer under Ubuntu 11.04?

---

