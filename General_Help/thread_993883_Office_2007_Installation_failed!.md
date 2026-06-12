---
title: "Office 2007 Installation failed!"
date: 2008-11-26
forum: General Help
---

### Post by iampriteshdesai on 2008-11-26
I have done a fresh installation of Ubuntu Ibex. I have installed latest version of Wine. Now I tried to install MS Office 2007 useing tis tutorial:[http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/](http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/)
Office now gets installed properly but still when I click on the icons to open them I get "Starting Word" and then it crashes.
Plz help me. What is going wrong?
I love Office 2007

---

### Post by TFX360 on 2008-11-26
Install OpenOffice 3. It has Office 2007 (xlsx, docx) support. Wine just isn't stable enough AFAIK.

---

### Post by iampriteshdesai on 2008-11-26
Holy cow, 
I said I want to install MS Office not OOo

---

### Post by rpainter on 2008-11-26
> **iampriteshdesai said:**
> Holy cow, 
I said I want to install MS Office not OOo

INstall VirtualBox with windows XP. Install Office 2007 in there.

---

### Post by kanikilu on 2008-11-26
> **rpainter said:**
> INstall VirtualBox with windows XP. Install Office 2007 in there.

Seconded. It's a pain, I know, but I've found several critical apps that either do not install, do not run, or do not run well under WINE, so virtualization is my only option (short of dual-booting). It works surprisingly well, though, I have XP SP3 and Vista Enterprise both running smoothly under VBox.

Alternatively, you can purchase [CrossOver](http://www.codeweavers.com/products/cxlinux/) from CodeWeavers that supposedly supports Office 2007. Don't take my word for it, though, I haven't used it...just going off what their site says.

---

### Post by Therion on 2008-11-26
+1 on Virtual Box.  Used it for a long time because - like many others - sometimes I've just got to have access to MS Office.  
OO is great, up to a point, but it's not a full blown MS Office clone yet.

VMWare, which I'm using now in place of Virtual Box, is some truly superb (DirectX support!!) virtualization software as well.

---

### Post by porteclefs on 2008-11-26
+1 on VMWare. OO is dope. granted 'calc' is no excel...

---

### Post by iampriteshdesai on 2008-11-26
I actually have crossover (picked it up when it was free during the lame duck thing).
Currently trying to install via it. Thanks for the tip. How much mb is VMware? or virtual box? in size. and how much ram will they eat?
What is the point of using Ubuntu if you are running XP at the same time?

---

### Post by kanikilu on 2008-11-26
> **iampriteshdesai said:**
> I actually have crossover (picked it up when it was free during the lame duck thing).
Currently trying to install via it. Thanks for the tip. How much mb is VMware? or virtual box? in size. and how much ram will they eat?
What is the point of using Ubuntu if you are running XP at the same time?

System resources is one thing you'll definitely need to use something like VBox. A fully patched XP with Office will take about ~4GB of disk space, and I currently give it 768MB of RAM whenever I run it, but 512 worked ok.

As for why, well, to each is own. But in my case, I manage both Linux and Windows servers, so I use Ubuntu as my host OS, because I prefer it and it makes some things easier, and I virtualize XP so I can run things like AD admin tools (that won't run on WINE) and some other utilites.

The main thing is that I can save a snapshot of my XP session and just launch it whenever I need it instead of suffering with Windows full-time ;-)

---

### Post by Therion on 2008-11-26
> **kanikilu said:**
> System resources is one thing you'll definitely need to use something like VBox. 
I concur.  I give my VM's 1GB of RAM but you can get away with less.  Dont' drop below 512MB though.

Why both?  Because Calc is no Excel (sorry, it just isn't) and at times I simply have to have access to MS Publisher.  
Further, the only options, *other* than virtualization, to accomplish this are: 

1. Wine (which IMO is just not an option) or,
2. Dual booting an XP install.  

And dual-booting, JUST to access Excel and/or Publisher, sucks hard.  IMO.

---

### Post by TFX360 on 2008-11-26
Google Docs?

---

### Post by alinuxfan on 2008-11-26
> **iampriteshdesai said:**
> 
What is the point of using Ubuntu if you are running XP at the same time?

My favorite part is that Windows is an app under Ubuntu and I can kill it :p

Adam

:lolflag:

---

