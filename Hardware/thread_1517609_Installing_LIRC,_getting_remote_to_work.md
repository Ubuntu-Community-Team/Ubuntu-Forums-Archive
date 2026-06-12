---
title: "Installing LIRC, getting remote to work"
date: 2010-06-25
forum: Hardware
---

### Post by Kdar on 2010-06-25
I bought, recently, Rosewill RRC-127 remote. And I was trying to make it work with my HTPC, which is using Ubuntu 10.04.

I tried to install LIRC, both from Synaptic and also from CVS. But I am not sure if it was installed correctly.. since typing mode2 or irw in terminal didn't do anything. And when I type irw, it just sits and do nothing there.

I am also not sure which driver I need to pick in configuration after LIRC install.

---

### Post by IcarusR on 2010-06-25
Instructions here

[https://help.ubuntu.com/community/Install_Lirc]("https://help.ubuntu.com/community/Install_Lirc")

And Lirc manual

[http://www.lirc.org/html/index.html]("http://www.lirc.org/html/index.html")

---

### Post by laceration on 2010-06-25
These knock-off remotes most likely use the standard Microsoft media center configs/drivers.  Rosewill is the Newegg house brand.  I like buying from Newegg because in the customer reviews there are always some reports of how the product works in Linux, I suggest you check those out.

---

### Post by Kdar on 2010-06-25
Thanks for the link on help.ubuntu, I will try to follow this one, it seem to explain things much better.. espcially about "irw", I was confused if it was suppose to hang there in terminal or not.

There was few reviews that stated that it worked in Ubuntu. I tried it on 10.04, but it didn't really worked.
Going to try on 9.10, which is my desktop anyways, more convenient to configure it than before TV.

I have a question. One of those reviews, someone stated that he installed LIRC from CVS.

after you download and make & make install the package from CVS. So I need to do "sudo apt-get install lirc"?

---

### Post by IcarusR on 2010-06-25
If you are compiling from scratch you dont use apt-get, if you do it will probably over-rite the version you've compiled.
Use checkinstall to create  .deb which you can uninstall easily should be in the repository.

[http://www.asic-linux.com.mx/~izto/checkinstall/]("http://www.asic-linux.com.mx/~izto/checkinstall/")

---

### Post by Kdar on 2010-06-25
[http://wiki.xbmc.org/index.php?title=Remote_Control_Reviews](http://wiki.xbmc.org/index.php?title=Remote_Control_Reviews)
On this page it listed Mediagate GP-IR02BK, which seems almost identical to my remote, except branding.

Have anyone used it?

I am also confused about configuration of LIRC after install....
There are two fields.. one: Remote Control Configuration
and other: IR transmitter, if present..

in the first field I pick "Windows Media Center Transceivers/Remotes(all)

and the second field? So I need to select something there?

---

### Post by Kdar on 2010-06-25
additionally, lirc0 is not created after this installation. In /dev/ there is only lircd and thats all.

---

