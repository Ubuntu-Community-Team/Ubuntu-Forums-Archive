---
title: "ATI Mobility Radeon 5470 support?"
date: 2010-04-30
forum: Hardware
---

### Post by Triple-H on 2010-04-30
Hi

I have an ASUS A42Jr laptop, and it has an ATI _MOBILITY _RADEON HD 5470 1 GB graphics card.
I tried installing Ubuntu 10.04 using WUBI, and it worked flawlessly and quickly. However, when I try to enable compiz effects, it tells me that it could not enable the effects. I think this is because my graphics card is not supported by default.
I tried installing the drivers using this guide:
[http://ubuntuforums.org/showthread.php?t=1430357](http://ubuntuforums.org/showthread.php?t=1430357)
But it did not work. I basically tried 10-1 and 10-4, and both packages did not solve the problem. After some reboots, I got the watermark, but compiz still did not work, and graphics became slower. Scrolling started to lag too much and dragging windows is very slow. So I simply un-installed Ubtuntu and will do another fresh install.
However, I would like to know if my graphics card is supported by the newest Ubuntu, because I really like Compiz and I would like to get it working on my laptop.

Thank you for your time.

---

### Post by hai2lp on 2010-05-01
I got exactly same problem ....
But if i use Ubuntu karmic 9.10 it's work nicely and no problem...

anyone got this luck , please post soon...
:(

---

### Post by Triple-H on 2010-05-01
I want to use it on the new version of Ubuntu, I really need solution for this problem :(

---

### Post by pumax on 2010-05-02
@hai2lp: What did you do in order to make it works on 9.10? Is 3D  acceleration enabled on your system? compiz?

---

### Post by hai2lp on 2010-05-03
[@pumax]("http://ubuntuforums.org/member.php?u=1065358")
Surely it's work fine with Ubuntu 9.10 Karmic edition
Do apt-get update and upgrade first 
And exactly follow the step on crypto post   [http://ubuntuforums.org/showthread.php?t=1430357](http://ubuntuforums.org/showthread.php?t=1430357)
All visual capability are working including compiz too...

But the bad thing is after i try on Ubuntu 10.04 LTS compiz still did  not work, and graphics became slower. Scrolling started  to lag too much and dragging windows is very slow

---

### Post by pumax on 2010-05-03
I read somewhere that graphics works fine with the fglrx driver from the ubuntu lucid repo. (there is already mobiltiy radeon support integrated). Alternativly you can use the open source ati driver (automaticlly loaded  upon first ubuntu 10.04 start). The driver has HD 5xxx support, but no  accelarations. That means Desktop work and videos works fine until you  not use effects.
Is not true?

---

### Post by Triple-H on 2010-05-03
Yes, things work fine as long as you don't try to install the driver yourself [I think so] but I can't run Compiz. It's a shame because I would like to use my 1 Gb graphics card :(

---

### Post by pumax on 2010-05-03
Maybe I'm not understanding you....:)
Why should you install driver yourself if things work fine after installing ubuntu 10.04 and fglrx driver from repo?
I mean...you don't need use crypto procedure. You should install ubuntu and the install fglrx in order to have 3D acceletation and, of course, compiz. 
I have no tested what I'm saying you, so I might have made a mistake on procedure*.*

---

### Post by Triple-H on 2010-05-08
Good news!

I un-installed Ubuntu a week ago. Yesterday, I re-installed it.

Today, it showed a message that I needed to activate some drivers [the amd/ati drivers] and I hit "ok".
It downloaded some files, then requested a reboot.

After reboot, Compiz was fully functional, and I realized that Ubuntu finally identified my Mobility 5470 graphics card!

Ubuntu rocks!

---

### Post by hai2lp on 2010-05-08
Are u sure Triple-H ???

Eventually after a week i'm waiting for this ,,,,

I don't know whats wrong with ubuntu 10.04 , why they not using the same setting for this ATI 5470 coz it's work nicely on karmic 9.10 ,,,

So did u just do activate on hardware drivers ? that's it ?
No other setting or configuration ? 

Aight' then let me try

:guitar:

---

### Post by Triple-H on 2010-05-09
As I said earlier, I did a fresh install, and on the next day, it said I have to allow it to activate some ati drivers, I hit OK, waited a bit. Then it requested a reboot. After reboot, Compiz was fully functional, and Hedgewars game worked very smoothly [it did not work before activating the drivers]

I hope it works for you too.

---

### Post by warking on 2010-05-29
Hi triple-h,
Is your graphic card ATI Mobility HD5470 with 1G GDDR integrated?

I am wondering if I should buy a DELL studio 15 with that graphic card
I would like to install ubuntu as my working system.

---

### Post by Triple-H on 2010-05-29
Hi

I'm in a hurry, so here are the specs of my laptop:
[http://www.asus.com/product.aspx?P_ID=CHUAkgEZmzf52Pai](http://www.asus.com/product.aspx?P_ID=CHUAkgEZmzf52Pai)

you will find the VGA somewhere in the page

Good luck

---

