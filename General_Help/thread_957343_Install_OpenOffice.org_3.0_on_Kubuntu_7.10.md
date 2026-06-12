---
title: "Install OpenOffice.org 3.0 on Kubuntu 7.10"
date: 2008-10-24
forum: General Help
---

### Post by o_swas on 2008-10-24
Hello,

I'm using Kubuntu 7.10 on my notebook.  I don't want to risk "breaking" it by upgrading to newer versions of Kubuntu.

It currently uses OpenOffice.org 2.3 which was either installed by default or I installed from Adept (I don't remember which).  The integration of OpenOffice.org is perfect as it shows up in the "Office" menu and everything.

I now need to upgrade to OpenOffice.org 3.0.  Assuming that these binaries are not in the "standard" Kubuntu repositories to which my installation is pointing, what is the best and easiest way to upgrade to OpenOffice 3.0?  

Thank you!!!

-Ryan

---

### Post by Liviu-Theodor on 2008-10-24
Try downloading it from [http://www.openoffice.org/]("http://www.openoffice.org/"). Look for the [FONT="Courier New"].deb[/FONT] file. And anyhow, if you wish to keep it up-to-date, you will have to upgrade your kubuntu to a newer version (I think next year), as it has only 18 month support from Canonical. With a LTS you can keep it for a longer time.

---

### Post by o_swas on 2008-10-24
So I take it that installing the .deb from openoffice.org will replace the existing 2.3 installation with 3.0, and retain the KDE integration and everything?

Thank you for your help!!!

---

### Post by scouser73 on 2008-10-24
You need to delete your existing OpenOffice installation first. Follow the instructions from this tutorial; [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

---

### Post by o_swas on 2008-10-24
> **scouser73 said:**
> You need to delete your existing OpenOffice installation first. Follow the instructions from this tutorial; [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

And these instructions will work for Kubuntu 7.10 also?  Just to make sure before I start hacking!

---

### Post by Liviu-Theodor on 2008-11-03
> **o_swas said:**
> And these instructions will work for Kubuntu 7.10 also?  Just to make sure before I start hacking!

I read the instructions there. If you want safety, I will say have a little patience until Canonical puts it in the ubuntu repositories (or at least until you don't have to remove also the older openoffice, and with it, the ubuntu-desktop metapackage). And seeing as it is not even in 8.10, I do not advice running it on 7.10.

---

