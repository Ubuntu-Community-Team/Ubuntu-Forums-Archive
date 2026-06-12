---
title: "Loading Ubuntu and Package install problems"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by ro88o on 2005-12-20
Ok so I installed Ubuntu and everything seemed to go fine. I took out the installation CD when it told me and it rebooted to do its 'package install' thing.

Part way (I think most of the way) through the package installation I got some crazy errors which ended with:

[B]603.806018 Code: ff 0e 55 48 etc.
...
603.830687 <7> Losing some ticks... checking if CPU frequency changed.
603.835816 Kernel panic - not syncing. Aiee, killing interrupt handler![/B]

The computer froze and after a couple minutes I ended up pressing the reset button. Ubuntu was booted again and it warned me some packages may not have been installed properly but I pressed ok and it went onto the command prompt login screen.. then froze :???: I rebooted again and got to the same screen but this time managed to login in correctly.

Now how do I get into Ubuntu from the command prompt I'm left at ? And secondly could the errors I got at package install have caused any major problems ? (If so should I re-install and how would I prevent that same thing happening?)

Hope somebody is able to help me - thanks in advance.

ro88o

---

### Post by az on 2005-12-20
1.  Was the computer working properly previously?  This seems like a hardware problem.  You ca boot into memtest to tesat your memory (let it run for a while - it does many different test. If you get no errors after a few minutes, assume that is not the problem.  Although some memory issues can only be revealed after 15 hours of tesating (or so)

2.  From the command line, login and type

sudo apt-get -f install

and then

sudo apt-get install ubuntu-desktop

---

### Post by ro88o on 2005-12-20
> Was the computer working properly previously?
My XP Pro was working fine, and so was my Fedora Core 2 before I deleted the partition. I'll run memtest anyway and see what it throws up.

> 
sudo apt-get -f install
sudo apt-get install ubuntu-desktop
Thanks alot I'll give those a go :D

---

### Post by infoburner on 2005-12-20
did you checksum the install image after you downloaded it? getting impatient and skipping that has bitten me before.

---

### Post by ro88o on 2005-12-21
I tried to use this command:
sudo apt-get -f install

But got an error about having to install dpkg so I tried that (something like sudo dpkg --configure -a) and kept getting problems about missing fonts or something :???: the process eventually froze before completion so I reset and tried again - same thing happened :mad: 

I think I'll just wait for the CDs to be posted to me and try a full re-install unless anyone's got any bright ideas :) ?

Thanks for your help so far,
ro88o

---

### Post by KimG on 2005-12-21
I am new to Ubuntu and am still experimenting with setting up my PC.
My recently downloaded Breezy has some strange text in some of the
help files ( ie. blah, blah, blah ), and I am wondering if I should go with
the official CD. But first, how can I do a checksum test on my downloaded
version?

Thanks

Kim

---

