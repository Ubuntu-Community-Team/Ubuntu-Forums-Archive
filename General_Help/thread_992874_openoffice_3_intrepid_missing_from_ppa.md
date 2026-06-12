---
title: "openoffice 3 intrepid missing from ppa"
date: 2008-11-25
forum: General Help
---

### Post by lean on 2008-11-25
Hi,
if you look at the url below, you can see that openoffice 3 is not available for intrepid. Does anyone know why that is? Has it moved?

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by Ubuntist on 2008-11-25
OO.o wasn't ready in time, but it can be installed by changing your software sources.  I don't have the relevant thread handy, but search the forum a bit and you'll find it easily.

---

### Post by lean on 2008-11-25
Okay, I understand it is not in the official repository, but why is is missing from PPA?

---

### Post by Skripka on 2008-11-25
> **lean said:**
> Okay, I understand it is not in the official repository, but why is is missing from PPA?

It isn't.


[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by TeXtonyx on 2008-11-25
> **lean said:**
> Hi,
if you look at the url below, you can see that openoffice 3 is not available for intrepid. Does anyone know why that is? Has it moved?

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)


Display sources.list entries for: The Intrepid Ibex

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main 

deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main 

------------------------------------

It looks available to me, there was a drop-down box that was
set to jaunty, but you could pick Intrepid or Hardy from it.
Maybe they just fixed it. The above is a copy&paste of your url.

---

### Post by Michael Kofler on 2008-11-25
I can confirm the problems of lean. 

[http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages)

is empty (as is the amd-64 version). 'Last modified' says Nov. 25nd 2008, so I guess this problem is rather new.

I tried to install the jaunty packages on intrepid, but this fails on an unsolvable dependency (librdf0 >= 1.0.8).

---

### Post by mn.matrix on 2008-11-26
I am also having same problem. I had installed using following repositories 

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

after I  installed Intrepid on November 1st week. Today, I removed openoffice* by mistake and tried to reinstall it. Then found out it is missing at that repository for Intrepid. 

deb package from openoffice.org is not working properly with intrepid on my machine. 

Please help, if anyone have any suggestions how to get openoffice 3.0 install on Intrepid?

---

### Post by mlapaglia on 2008-11-26
same here, attempting install on 64bit intrepid. the ppa is empty. maybe they are updating it?

---

### Post by spectre51 on 2008-11-26
Thats what I was thinking maybe an update.  This worked 2 weeks ago but now its a no go.  Will try again in a couple days see if it is cleared up.

---

### Post by omns on 2008-11-26
grrr, just when I started a new install :mad:

Free beer nuts for anyone who finds them again :)

---

### Post by frankleeee on 2008-11-26
I installed 00o3 with Ubuntu Tweak but it was the ppa link that ended up in the software sources 3rd party list, you might checkit out to see if it works.

---

### Post by Justin Trouble on 2008-11-26
The admins of the OpenOffice.org 3.0 PPA say the packages were buggy and crashed when openoffice.org-gnome was installed. They will be reuploaded when the bug has been resolved.

---

### Post by loell on 2008-11-26
justin beat me :D

---

### Post by peakshysteria on 2008-11-26
Haven't tried this myself, but Tombuntu has what appears to be a nice howto:

[Install OpenOffice 3.0 in Ubuntu 8.04 and 8.10]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

Really looking forward to 3.0 myself. But for now I'll wait it of :)

---

### Post by lean on 2008-11-26
*"The admins of the OpenOffice.org 3.0 PPA say the packages were buggy and crashed when openoffice.org-gnome was installed. They will be reuploaded when the bug has been resolved."*

Where do you find this information? On some mailing list, or by private mail?

---

### Post by kjano on 2008-11-26
> **lean said:**
> *"The admins of the OpenOffice.org 3.0 PPA say the packages were buggy and crashed when openoffice.org-gnome was installed. They will be reuploaded when the bug has been resolved."*

Where do you find this information? On some mailing list, or by private mail?

--> [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by philinux on 2008-11-26
[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

The link above just needs reading. It was posted in post #1

---

### Post by xeros on 2008-11-28
Is there a mirror for these packages?
I've installed some of them and I'd like to install some more (I don't need openoffice.org-gnome in kubuntu) and integrate them on remastered dvd.

---

### Post by Pastito on 2008-11-30
Still wating the reupload!!:confused:

---

### Post by Leu8 on 2008-12-03
Where can I get the old OOo3 packages? They could have reuploaded the previous ones.

---

### Post by dkruythoff on 2008-12-03
> **Leu8 said:**
> Where can I get the old OOo3 packages? They could have reuploaded the previous ones.

Guess I'll just quote the message behind philinux's link, since some don't care to read.
> The packages were buggy and crashed when openoffice.org-gnome was installed, they will be reuploaded when the bug has been resolved.

---

### Post by Leu8 on 2008-12-03
That was a misunderstanding. I know that the **new** packages were buggy, but the previous ones on ppa were ok. So maybe someone still has the previous packages and it is possible to get them.

---

### Post by Skripka on 2008-12-03
> **Leu8 said:**
> That was a misunderstanding. I know that the **new** packages were buggy, but the previous ones on ppa were ok. So maybe someone still has the previous packages and it is possible to get them.

You have to go to the OOo website, and download the BIG .deb archive (~150MB), and then install yourself:

Remove all trace of OOo2.... extract the tar, navigate to the folder containing the debs:

```

sudo dpkg -i *.deb

```

There will then be one deb left hiding in a subfolder that also needs installed.


BAM.  You have OOo3.  That is the only way to get it on *buntu.

---

