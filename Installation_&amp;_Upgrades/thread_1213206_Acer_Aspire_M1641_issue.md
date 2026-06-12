---
title: "Acer Aspire M1641 issue"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by eheyl on 2009-07-14
I've got a 9.04 Ubuntu live CD. I threw it into the drive and rebooted. I got a motherboard bug "try booting with the -noapic command" I then tried with 8.04 and got the same thing. I tried installing under windows and restarted. SAme thing. PRoblem is I'm not sure WHAT it is or how to fix it. My specs:

3GB RAM
2.5 GHZ processor
Vista 32 bit home premium.
640 GB HDD

Can someone help, or has anyone come up against this issue? I'd really like to give the new OS a try...

EDIT:

Ok, here's the error: 
MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with APIC=debug and send a report. Then try booting with noapic.

So how do I do what it is suggesting? I'm booting from the live CD

---

### Post by zgembo on 2009-07-18
Here is how I fixed this problem:

Go to BIOS settings by pressing DEL while the system is booting
On the BIOS menu go to ADVANCED tab
On the ADVANCED menu screen go to INSTALLER OS SELECT
Under Installer OS Select there is WIndows by default
Hit Enter and change it to OTHERS
Hit F10 tey to save new settings and exit BIOS setup

Enjoy!!!:D 

There are several other topics regarding this bug but I cannot find them now so if administrator can join these topics in one and mark it as solved would be very nice.
Thanks in advance.

---

### Post by eheyl on 2009-07-18
Ok, question for you: When I install from teh ubuntu CD I choose for it to install side by side, but then it only seems to give me the bare minimum (2gb) to install and I can't update or install anything else. I have 2 320 GB hard drives, both are windows partitions (vist 32) help?

---

### Post by zgembo on 2009-07-18
I bought my computer recently and have only Vista on it, for now. What I have tried was LiveCD. Before I made that change in BIOS Live CD couldn't boot, instead I used to get that "bug 8254" message. Now CD boots without problem and next step is to install Ubuntu8. After that I will be able to tell you more.

---

### Post by eheyl on 2009-07-18
> **zgembo said:**
> I bought my computer recently and have only Vista on it, for now. What I have tried was LiveCD. Before I made that change in BIOS Live CD couldn't boot, instead I used to get that "bug 8254" message. Now CD boots without problem and next step is to install Ubuntu8. After that I will be able to tell you more.

Ok it is installed, but with that darn 2GB issue I mentioned.. Whats next?:popcorn:

---

### Post by zgembo on 2009-07-18
Let me understand...You have two partitions and they are both Windows partitions (NTFS)? In that case you need to make space for Linux partition (Ext3) - probably best way is to reduce one of them - disc D which is NTFS. Than during the installation you can format it to Ext3 and install your Ubuntu on it. If it's already installed you can resize your Ubuntu paartition and that shuold be it. 
Does it help you?

---

