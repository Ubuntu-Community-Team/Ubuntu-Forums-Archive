---
title: "Install failed on dual boot Acer Aspire 9410 laptop w/ Vista"
date: 2008-09-30
forum: Hardware
---

### Post by jbhedgehog on 2008-09-30
I was trying to load Ubuntu as the second OS on my Aspire 9410 w/ Vista.

The install went fine until the partitioning.  No matter what I did it kept telling me that the partition was too small.  (I reset a partition through Vista to 70+ GB, which seemed like plenty of space).

I kept on messing around and the installer finally told me that there was a fatal with the installation and that I should re-run the installer.  Ugh.

The OS did come up but I'm guessing that it was running off the CD.  Sure...it worked great, it even found my wireless card.  But I'll be darned if I can figure out how to set the partition correctly so that the OS drops properly.

I did follow the instructions here:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

And I downloaded this OS: ubuntu-8.04.1-desktop-i386.iso

Ideas and/or suggestions?

Thanks,
JBH

---

### Post by esmailgad on 2008-09-30
I do not know what do you mean by "reset". 
I installed dual system a lot of times on different Hp and acer notebooks and disktops and I had no problem. The steps I followed were:
1-From windows I **_delete _**a partition to create a large empty space. this step is very important
2-I boot from the live ubuntu CD and choose "ubuntu installation.
3-At the step of partition creation I select "giuided to a large empty space".
that is all. Are these the steps you followed?

---

### Post by jbhedgehog on 2008-09-30
Yep.  Those are exactly the instructions.  That's why I'm kinda' baffled.

I'm going to try it again tonight and see how it goes but if the wizard doesn't do it, do you have any other suggestions?

Thanks,
JBH

---

### Post by sergiom99 on 2008-09-30
I did it following this fool-proof tutorial:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by jbhedgehog on 2008-10-01
Ok...so here's the reply upon reinstall:

[I][COLOR="Red"]The installer encountered an error copying files to the hard disk:

[Errno 28] No space left on the device[/COLOR][/I]


Which is complete nonsense 'cause my /dev/sda3 reads 65.16 Gib free!!!

I really thought I followed the instructions perfectly.  Just an FYI, I used these:

[http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

JBH

---

### Post by jbhedgehog on 2008-10-01
Ok...got it installed after I used only half of the 70 GiB.  The Ubuntu partition is now only 30 GB.  

Is there a way I can use more of the space I originally wanted to use for U?

Sorry for the newbie questions.

Last, can anybody recommend a good online tutorial for command line practice?

Gracias,
JBH

---

