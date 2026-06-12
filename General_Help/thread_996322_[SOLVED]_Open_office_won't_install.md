---
title: "[SOLVED] Open office won't install"
date: 2008-11-28
forum: General Help
---

### Post by Mr.Kuchinawa on 2008-11-28
Ever since I added norwegian (bokmål and nynorsk) to the system (not in OO), I have not had Open office installed. It sounds surreal, but I have no other explanation. Anyhow, That's not really a problem since I can just install it from syntaptic,right? Apparently not,Add/remove tells me That there is a conflict that I should solve I synaptic. Please tell me what to do,I am totally dependent on OO.

The OS is Ubuntu 8.10

---

### Post by Sef on 2008-11-28
> Apparently not,Add/remove tells me That there is a conflict that I should solve I synaptic. Please tell me what to do,I am totally dependent on OO.Install it from Synaptic.   System > Adiministration > Synaptic Package Manager

It can resolve problems that Add/Remove cannot.

---

### Post by Mr.Kuchinawa on 2008-11-28
My mistake, I guess I wasn't clear enough. You see, when I e.g try to install open office writer from synaptic, first it tells me that a whole lot of things like openoffice.org-core and -common are to be removed (and nothing installed). Then it tells me that it has unresolvable dependencies, openoffice.org-core

I am utterly confused..

---

### Post by Mr.Kuchinawa on 2008-11-29
Sigh.. this is tiresome. Could anybody just tell med how to completely remove any trace of Open office and then reinstall it from scratch? That would be immensely appreciated.

---

### Post by desmane on 2008-11-29
does 

sudo apt-get update && sudo apt-get upgrade

work or do you get any errors?

---

### Post by lukjad on 2008-11-29
Open up the terminal and type:
```
sudo apt-get purge openoffice
```
It *might* work. Give it a try.

---

### Post by linux_tech on 2008-11-29
Have you tried using Add/Remove yet?
1) Applications->Add/Remove
2) On the top left side, click the drop down menu and select the Installed Applications option
3) search for OpenOffice
4) Uncheck any of checked items
5) Click Apply

OpenOffice should be uninstalled
then, to reinstall it:
1) Applications->Add/Remove
2) On the top left side, click the drop down menu and select All Available Applications 
3) search for OpenOffice
4) Check any OpenOffice programs you want 
5) Click Apply
Open Office should be installed

---

### Post by TeXtonyx on 2008-11-29
> **Mr.Kuchinawa said:**
> Sigh.. this is tiresome. Could anybody just tell med how to completely remove any trace of Open office and then reinstall it from scratch? That would be immensely appreciated.

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

---

### Post by Mr.Kuchinawa on 2008-11-29
Thanks guys. I followed the instructions on tectonic. Worked like a charm!

---

