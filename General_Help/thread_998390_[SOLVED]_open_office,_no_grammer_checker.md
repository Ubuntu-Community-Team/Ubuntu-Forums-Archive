---
title: "[SOLVED] open office, no grammer checker?"
date: 2008-11-30
forum: General Help
---

### Post by fillintheblank on 2008-11-30
IS there a grammar checker for open office?

---

### Post by OrangeCrate on 2008-11-30
> **fillintheblank said:**
> IS there a grammar checker for open office?

There is not one in 2.4, which is our current release. I believe I read in a recent thread that there is one for OOo 3.0. Can't seem to find the thread right now, or I'd give you the link.

---

### Post by fillintheblank on 2008-11-30
I tried to install OOo 3 but I couldn't get it. How do I go about doing it?

---

### Post by fillintheblank on 2008-11-30
I think I found a grammar checker for OO 2.4 Its called "language tool 0.9.2"
Any thoughts on that?

---

### Post by OrangeCrate on 2008-11-30
> **fillintheblank said:**
> I think I found a grammar checker for OO 2.4 Its called "language tool 0.9.2"
Any thoughts on that?

Sorry, I've never used it.

Regarding installing 3.0, there are a myriad of recent threads on the forums discussing that. Just search for it, and pick the way you'd like to do it. Apparently there are several options.

As it stands right now, the upgrade is a non-starter for me. I only use Writer (a lot), and read spreadsheets (lots and lots), so it's not imperative for me to upgrade before it shows up in the repositories.

I've read two opinions regarding whether we'll get it soon. The first group think that it'll be backported to Intrepid, and the other group think we'll have to wait for Jaunty. I don't know which is true.

---

### Post by TeXtonyx on 2008-11-30
There is only one way that I see working now, which worked for me.

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)
First, remove your existing version of OpenOffice.org:

sudo apt-get remove openoffice*.*
steps ...

With that done you should have just one thing left to do: Install the
desktop integration package. That should be in the DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

I've read that sudo dpkg -i -R may be a better syntax.

Her is another website that makes a similar recommendation,

-------------------------------

[http://www.rebelzero.com/ubuntu/inst...hardy-heron/27](http://www.rebelzero.com/ubuntu/inst...hardy-heron/27)

[http://www.rebelzero.com/ubuntu/](http://www.rebelzero.com/ubuntu/) [copy and paste into one line]
installing-ooo-300-onto-hardy-heron/27

"If you already have OpenOffice.org 2.4.1 installed through Ubuntu&#8217;s
repos, you will need to remove it. One of the 3.0.0 packages (debian
menus) has a conflict with one of the 2.4.1 packages,
openoffice.org-core. Removing openoffice.org-core will also remove OO.o
2.4.1 from your computer. Remove OO.o 2.4.1 by using apt-get at the
command line:

sudo apt-get remove openoffice.org-core

You&#8217;ll see apt-get prompt you for removing the other 2.4.1 packages as well.
Just hit enter and apt-get will do the rest. Proceed to Step 3b.

-------------------------------------------------

Grammar checker try,
[http://www.lockergnome.com/linux/2007/07/26/grammar-check-for-open-office/](http://www.lockergnome.com/linux/2007/07/26/grammar-check-for-open-office/)

---

### Post by oldos2er on 2008-11-30
> **fillintheblank said:**
> I tried to install OOo 3 but I couldn't get it. How do I go about doing it?

 See [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/) 

 From within a document, hit F7.

---

### Post by Arup on 2008-11-30
For Grammar checker use Language Tool extension which works out even better than the MS Office grammar checker.

---

