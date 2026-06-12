---
title: "Dual boot or not?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by ex-windowuser on 2009-10-22
I was wondering what is the benefit of having a dual boot computer besides falling back to Windows (or other OS) in an emergency.  Since we can use VirtualBox to run other OS, is it better to run a computer all Ubuntu or not.  But is there a benefit, if any to just install Ubuntu?  Be nice pls., I'm a newbie.

---

### Post by earthpigg on 2009-10-22
hi,

four options.

1) WUBI install. good for test driving ubuntu on a windows computer, otherwise not so great.

2) WINE in ubuntu to run windows apps. not reliable, but the best option for 3d video games.

3) dual boot. best of both worlds, but can't have both running at the same time.

4) XP in the [proprietary version of VBox]("http://www.virtualbox.org/wiki/Linux_Downloads"). if your system has the RAM and you don't play 3d video games in windows, this is the best solution. you can use the proprietary version gratis if you are a home user.

4a) XP in the OSE version of vbox in the ubuntu repositories. this has limited functionality, but works fine for many. things like the CD drive, USB, and guest additions (for mouse pointer integration, folder sharing, etc) either don't work, or don't work quite as well.... this is Sun Microsystem's business model, of course :D

edit:

if you currently have vbox OSE installed and want to move to the proprietary version, uninstall vbox OSE, restart your computer, then install the proprietary virtualbox.

virtualbox is an exception to a lot of general rules about ubuntu.... normally, one doesn't need to restart to install/remove software. normally, one should stick to the ubuntu repositories and not download stuff from websites. etc.

---

### Post by linux4life88 on 2009-10-22
I personally hate dual booting. I don't really have a great reason why, basically it is just personal preference. I would try dual booting and virtualizing and see which you like better. That is really the only way to know.

---

### Post by pricetech on 2009-10-22
Virtualization gets my vote.  I've done both and Virtualization works best for me.

I used the Vbox OSE from the repos without a problem.  I'm not a gamer though, so I can't say how it behaves gaming.

---

### Post by ex-windowuser on 2009-10-22
Thanks for the input guys.  This really helps me from deciding on doing a dual boot on a certain laptop that I saw on sale at BestBuy that already has Win7.  It's a Sony that plays BluRay with an Nvidia graphics card.  So I am not sure if I will have any problems loading Ubuntu.

---

### Post by earthpigg on 2009-10-22
ask the folks at best buy if the machine comes with a standard win7 install disc. insist that it should if the answer is no.

if you can get ahold of one, that will make virtualization much easier.

---

### Post by milensinan on 2009-10-22
well, i have 2 laptops and one of them has 2 OSs; ubuntu and XP. and i'm truly happy with this config. they don't bother each other and usually when i need causal stuffs i use xp and when i want to enjoy some linux i switch to ubuntu. and slowly i learn the linux stuff. why 2 OSs is because i am a newbie just like you so it's impossible for us to use just linux. would have a lot of problems (until we learn it more properly).
and after that pleasure i installed SUSE to my second laptop (SUSE + Vista).
my recommendation for you is to make dual-boot. painless. ciao : )

---

### Post by Mark Phelps on 2009-10-23
> **earthpigg said:**
> ask the folks at best buy if the machine comes with a standard win7 install disc. insist that it should if the answer is no.

You're kidding, right??  These days, you're lucky to even get a Recovery Disk with a new PC.  Plus, now that 7 has the built-in ability to generate and burn its own Recovery Disk, I wouldn't be surprised if vendors stop supplying disks altogether!

Not saying it's a bad suggestion, just saying NOT to get your hopes up.

> if you can get ahold of one, that will make virtualization much easier.

And with this trend toward NOT supplying disks at all, using VB in the future is going to be a lot harder to do; thus, forcing folks into dual-booting instead of virtualization.

---

### Post by pricetech on 2009-10-23
> **earthpigg said:**
> ask the folks at best buy if the machine comes with a standard win7 install disc. insist that it should if the answer is no.

I'd take that a step further;  If it doesn't have the install media, don't buy it.

---

### Post by earthpigg on 2009-10-23
> **pricetech said:**
> I'd take that a step further;  If it doesn't have the install media, don't buy it.

i would myself, as well, but my list of "i will buy a computer with windows when ______" is rather long :D

---

### Post by FireStorm102389 on 2009-10-24
alright man, from 1 newbie to another, i've learned a lot so far just getting into linux and I preffer linux over any operating systemI would say stick with linux, its fast and a hell of a lot safer, keep ur windows in a VM in virtualbox since if anything happens like u get a virus, ur whole comp isn't ******...btw, i had a dualboot aswell, my honest opinion, setting it up is a pain in the *** unless u have windows and use WUBI, but if windows screws up, pretty much everything screws up, stick with linux and windows VM

---

### Post by Camilia on 2009-10-25
I had dual boot up and opening pages was getting slower and slower. Possibly because my memory was just minimum to do it. I thinking of doing it again for I have some 
CDs that I can't read with ubuntu.

---

