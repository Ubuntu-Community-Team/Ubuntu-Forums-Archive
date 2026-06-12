---
title: "installation problems amd athlon xp"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Unkuiri on 2009-04-14
Hi, I have a problem installing ubuntu on my amd athlon xp (soltek motherboard) 1,2GHz and 512 MB RAM...When I try to install in normal graphic installation it doesn't even pass the account name/password window, but when I use safe graphics mode it passes all this installation fases, I select 100% Ubuntu on disk, but after it passes nearly 50% of the installation it blocks...:(...
What can I do to clean install Ubuntu on my computer?...:(

PS:When I start live cd in safe graphics mode it works fine most of the time but even here sometimes it crashes...:(...

thanks in advance...
keep the great work...

---

### Post by spcwingo on 2009-04-14
It's probably something to do with your vid card.  Try the alternate CD located here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Unkuiri on 2009-04-15
Thanks for the reply, I'll try this alternative installation and tell here the results...

---

### Post by Unkuiri on 2009-04-18
Hi, the disc you indicated does not solve my problem, anytime it blocks at 6% in installation of software...:(...I think the problem might be in the hard drive...:(...what can I do?

---

### Post by jzalomon on 2009-04-18
I totally agree with the video card been the motive of the wrong installation, are you using the motherboard vid or another video card??..just remember graphics is your issue!

---

### Post by Unkuiri on 2009-04-18
I'm using another vid card, not in-board... it's an ati radeon 256MB, I don't know for now what model it is because there is no way to see it, because no operrative system is installed...
Can you help me solving this problem?I've tried various versions of ubuntu without success...:(...and I really like to use it...:(

---

### Post by cheme420420 on 2009-04-18
When I turn on my PC it displays "Nvidia Gefore 5200. Version 4.56.3433.5 Ram 128 MB but only for a split second.  Watch the screen the next time you turn on your PC and see if it tells you any information.  Is there any on board video option?  If not do you have a older video card you could try?  Can you run from a Live CD at all?

---

### Post by jzalomon on 2009-04-18
I myself have and AMD Athlon xp and have and Nvidia card, i'm using ubuntu 8.10 and runs nicely, didnt havee to install any drivers or anything that windows asks all the time, so i didnt have the problems you are facing, my opinion is that you use the onboard vid card, take off the Nvidia and try to install ubuntu, see what happens...once ubuntu is installed get on again with the Nvidia card and try to run it

---

### Post by Unkuiri on 2009-04-18
I've tried to enter live cd in normal graphic mode and it enters normally but when I navigate the menus it crashes and shutdown the screen...i tried safe graphic mode live cd and it worked really fine...but I still can't install...

---

### Post by chrisstewart on 2009-04-18
I believe 6 percent is just after the partitioning stage where I have had a few similar problems when working on customer desktop pcs and in each case it was mismatched ram or faulty ram that memtest 86 detected. Also live cd's booted up and worked about 80 percent of the time but would lock up under high load. Try using memtest on the live cd and see what your results are.

Chris

---

### Post by Unkuiri on 2009-04-19
Yeah you're right it fails...:(...what can I do then?...:(

---

### Post by spcwingo on 2009-04-19
Oops, I missed the part about your RAM failing the check.  I would suggest pulling all of them out except for one then rerunning the test to pinpoint which module has failed (if not both/all).  After that remove the installed one, replace with the other one, and rerun the test.  If you have more than 2 modules just repeat until all have been checked...just remember to check them one at a time.  Once you find out which one/ones are bad, just replace them.  I would highly suggest matching them to avoid further trouble.

---

### Post by Unkuiri on 2009-04-19
Before all, thanks for your help...I tried with a memory that does not give any error but still blocking on the software installation not at 6% but at 27%...:(...does anyone have an idea of what can I do?

---

### Post by chrisstewart on 2009-04-19
I would say to try a new CD-ROM or potentially re-burn the disc at a lower speed, Is the unit just locking up or giving read errors , Are there any capacitors on the motherboard that look swollen or puffy???

---

### Post by Unkuiri on 2009-04-19
The unit just locks up, doesn't emit any sound nor opens, I have three units and tried them all without better results...I don't see any capacitors swallen or puffy but some have a little rust in the metal surface...

---

### Post by chrisstewart on 2009-04-19
when you mean three units are you referring to cd-rom drives??? or three different computer systems.

(Metal Rust?) Normally swollen caps or partially failing caps will have a rust like matter that seeps out of them you could use your nail / or screw driver and remove it but if that is the case I would say your motherboard is showing signs of failure... What kind of board are you playing with I have a extensive list of IBM and HP boards that where common with this problem in the first generation P4 cpus

---

### Post by spcwingo on 2009-04-19
I would recommend trying the alternate installation CD if it refuses to install from the live CD.  It can be found here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

If that doesn't work try this...I had one machine that Ubuntu refused to install to initially from either the live CD or alternate CD.  Here's what I did to get it installed.  First I downloaded the mini CD image here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Burned it as an image and booted from it.  (Note: Just be sure that you are connected to the internet before booting from the disk...I recommend by ethernet)  At the boot prompt enter "cli", press enter, and follow the on screen instructions.  After installation is finished reboot when prompted.  Upon reboot log in via the cli (command line interface).  Just note that when you type your password you won't see any *s.  From there type these commands:

```
sudo apt-get install ubuntu-desktop
```(replace this with whatever desktop you would like installed: ubuntu-desktop, kubuntu-desktop, xubuntu-desktop)

After that enter this command:

```
sudo apt-get clean && sudo reboot
```

This will clear the apt-cache and should reboot straight into your new desktop.  Let us know if this get it installed for you.

---

### Post by Unkuiri on 2009-04-19
I'm referring to cd-rom drives, I've tried them all...
Yes, I think it's it some kind of rust-like matter...i'm using a soltek board...Is there anything I can do? or the only solution is buy another motherboard?...:(

---

### Post by chrisstewart on 2009-04-19
Soltek SL-75DRV5 is common to this problem...

---

### Post by Unkuiri on 2009-04-19
it worked for me spcwingo...:)...now i'm sending the reply from my ubuntu system that works greatly...thanks very much you all...:)..(i'm still worried about my motherboard)

---

