---
title: "Ubuntu still not ready for Atom?"
date: 2008-07-25
forum: Hardware
---

### Post by madu on 2008-07-25
Hi,

I want to have an Atom setup for a small home server.. mainly for power considerations.. 
Googling shows that there are still issues with Atom and Ubuntu.. I think the newer kernals have problems..

Is there a guranteed way to install Ubuntu on Atom...?
Or we have to have till Ubuntu Remix comes out?

Thank you.

---

### Post by prshah on 2008-07-25
> **madu said:**
> 
I want to have an Atom setup for a small home server.. 
Googling shows that there are still issues with Atom and Ubuntu..

I've set up Ubuntu 8.04.1 on an Intel Atom with no issues at all; [8.04 didn't work (initramfs)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239602"), but .1 just sailed through.

Sound, network, graphics, everything is just fine and dandy.

It's been only about a week though...

---

### Post by tamoneya on 2008-07-25
> **prshah said:**
> I've set up Ubuntu 8.04.1 on an Intel Atom with no issues at all; 8.04 didn't work (initramfs), but .1 just sailed through.

Sound, network, graphics, everything is just fine and dandy.

It's been only about a week though...

I have been thinking about making an atom box as a server as well.  I was curious though what case is that.  The atom boards that I have looked at are all mini-itx but all the mini-itx compatible cases are really tiny (I want to put in several harddrives).  That case seems to have plenty of space for my needs.

---

### Post by prshah on 2008-07-25
> **tamoneya said:**
> I have been thinking about making an atom box as a server as well.  I was curious though what case is that.  The atom boards that I have looked at are all mini-itx but all the mini-itx compatible cases are really tiny (I want to put in several harddrives).  That case seems to have plenty of space for my needs.

Actually I'm horribly embarrassed to mention this; It's a standard ATX case (4 x 5.25" bays, 2 x floppy/zip bays, etc). The customer I'd made it for wanted a cheap system and mini-itx cases are (stupidly, and absurdly) more expensive. Nearly twice what an ordinary case costs. Sigh. I dream of a MacMini kind of thingy... sadly no one pays me for it and my own computer(s) are chugging along smoothly without a hint of failure...

---

### Post by tamoneya on 2008-07-25
> **prshah said:**
> Actually I'm horribly embarrassed to mention this; It's a standard ATX case (4 x 5.25" bays, 2 x floppy/zip bays, etc). The customer I'd made it for wanted a cheap system and mini-itx cases are (stupidly, and absurdly) more expensive. Nearly twice what an ordinary case costs. Sigh. I dream of a MacMini kind of thingy... sadly no one pays me for it and my own computer(s) are chugging along smoothly without a hint of failure...

i can see that it is full atx.  I was looking for more specifics.  Most atx cases I have looked at dont have the ability to place the stand offs correctly for mini-itx.

---

### Post by prshah on 2008-07-25
> **tamoneya said:**
> i can see that it is full atx.  I was looking for more specifics.  Most atx cases I have looked at dont have the ability to place the stand offs correctly for mini-itx.

No real specs as such; just picked up the cheapest but one case I could find. Do the standoffs really not align? I've never faced this problem. I also got a proper IO shield with the board, without which I couldn't have installed the board without leaving a gaping hole in the back.

btw, it has only one IDE port, 2 SATA ports and a single PCI expansion slot; you'll have to plan your hard drives accordingly.

---

### Post by madu on 2008-07-25
Thanks prshah.
Good to know it went smmothly.. could you kindly tell the model of the motherboard you are using..?

I'm also looking for a MAc mini type case.. the Eee box comes with really tiny, Wii-looking case... unfortunately couldnt find any yet..

Thanks for the info guys.

---

### Post by prshah on 2008-07-26
> **madu said:**
> 
Good to know it went smmothly.. could you kindly tell the model of the motherboard you are using..?


Intel D945GCLF

---

### Post by anontrol on 2008-08-10
I've been working with an Intel D945GCLF board trying to get a general feeling for how well Ubuntu works with it.  I'm running 2GB of RAM and 32GB transcend SSD with an Aterhos based PCI wireless card (not using the wireless for general network access).

My initial assesment was that Ubuntu + firefox = unusable.  I would get grey "I'm busy go away" screens that seemed to be associated with disk writes.  I went through the standard disk activity minimization tweeks with no improvment.  In addition the wireless card was not recognized.  I moved to Opera to continue my assesment, but still ran in to frequent grey screens because of disk activity.

On a whim, I decided to upgrade the BIOS (looks like Intel has gotten smart and is distributing their BIOS upgrade as bootable .iso images... nice).  Anyway, that help a little (boot up was faster and certain types of disk access no longer produce grey screens) and my wireless hardware was finally recognized; however, I still get occassional grey screens every couple of minutes when there seems to be a huge block of disk activity (file system journaling?).  Firefox is still pretty much unusable.

My recomendation would be to first upgrade the BIOS, then try some disk access tweeks:  [http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/](http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/) .  If that doesn't get the system usable, then I'd recomend looking at moving away from a journaling filesystem (but I haven't tried that yet as my system is now relatively usable under Opera).

You'd think Intel/Ubuntu would get more involved, but it's obvious that they're not particularly serious about making sure their lower end stuff is super usable.  In 12 to 18 months, these Atom based systems are going to be everywhere...

---

### Post by pmulgaonkar on 2008-08-21
I too have a D945GCLF Atom board running Ubunty 8.04.1 working and extremely stable. 20GB IDE hard drive. Ubuntu etc. takes about 4GB currently. Wireless PCI board from AirLink 802.11g [http://www.airlink101.com/products/awlh3028.php](http://www.airlink101.com/products/awlh3028.php) running under NDISWRAPPER. 

Works great.

---

