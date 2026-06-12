---
title: "BrOffice: how do I do to upgrade it to the latest versio?"
date: 2008-11-09
forum: General Help
---

### Post by ieBrazil on 2008-11-09
You see,

I just have installed, by Synaptic Manager, the Brazilian version of OpenOffice, BrOffice. But the one it got is 2.sth. I know that we do already have 3.0 one. 

So, my point is: what do I do to get this version?

Tnx u all. A lot!



ieBrazil

---

### Post by scouser73 on 2008-11-09
It seems that the Brazilian version for OpenOffice is still at 2.4.1

[http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US")

---

### Post by ieBrazil on 2008-11-09
> **scouser73 said:**
> It seems that the Brazilian version for OpenOffice is still at 2.4.1

[http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US")


Nope. Take a look at the official site:
[http://www.broffice.org/](http://www.broffice.org/)

There one will read:

BrOffice.org 3.0.0 disponível [available]

Tnx anyway.

---

### Post by ugm6hr on 2008-11-10
I haven't installed the Brazilian version, but I would have thought the files structure must be the same as the en-US version...

Download the appropriate "install_pt-BR_deb.tar.gz" file from here: [ftp://www.broffice.org/stable/3.0.0/](ftp://www.broffice.org/stable/3.0.0/)
(BrOo_3.0.0_20080930_LinuxIntel_install_pt-BR_deb.tar.gz for 32-bit; BrOo_3.0.0_20080930_LinuxX86-64_install_pt-BR_deb.tar.gz for 64-bit)

Then the instructions here should work with a little modification: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

But in simple terms:
Download the appropriate tar.gz to /home/*username*
Double-click the tar.gz
Extract to the default directory (/home/*username*/BrOo.....
cd ~/BrOo (then press Tab key and Enter)
sudo dpkg -i *.deb

Then /opt/openoffice.org3/program/soffice is the command to run it.

You may need the langpacks too.  Hope that is correct!  Unfortunately, there is no Portugese subforum that I am aware of.

---

