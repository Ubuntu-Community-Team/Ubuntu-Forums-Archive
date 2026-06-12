---
title: "can install kubuntu but not ubuntu 64bit"
date: 2008-09-11
forum: General Help
---

### Post by swisscow on 2008-09-11
As it says, I can install Kubuntu 32bit (and Crunchbang 32 bit) but not Ubuntu (Gnome) 32 bit. It freezes on loading the live cd. Have forced it to load with various boot parameters but then the install crashes out.

64 bit all variants are fine but just a little confused as to why I can't install the stock 32 bit Gnome Ubuntu.

Have burnt 2 Ubuntu discs and md5summed them so that's not the problem

Any ideas?

---

### Post by swisscow on 2008-09-12
bumping

---

### Post by EmanresuusernamE on 2008-09-12
Seems like a bit of a waste to put a 32 bit-only version of a program on a 64 bit machine.  Why do you want to install the 32 bit version if the 64 bit version works just fine?

Perhapse some of the optomizations of the 32 bit version are incompatible with 64 bit processors.  As Kubuntu is a stripped down version of Ubuntu, that may be the reason that it works and Ubuntu does not.

---

### Post by swisscow on 2008-09-12
Thanks for the reply

Yes, it's more a matter of interest rather than cry for help, though Skype in 64bit with web cam is not good, and as I live abroad from my family I would like to use Skype to keep in touch- but I can manage with the phone for the time being

As to Kubuntu being a stripped down version of Ubuntu, I wasn't aware of this. I thought it was Ubuntu without Gnome but with Kde.

So are you saying that install Kubuntu then gnome Ubuntu on top (32bit) then I will be stuffed again?

---

### Post by EmanresuusernamE on 2008-09-12
#-o Oppps, I'm thinking of Xubuntu, not Kubuntu.  My bad.  Kubuntu is Ubuntu with KDE instead of Gnome.

---

### Post by swisscow on 2008-09-12
No worries, thanks anyway

---

### Post by tekky on 2008-09-12
Well, I see that you want to put XUbuntu on a 64bit processor.  I still don't think that the 64bit is the way to be unless you're actually interested in any 64 bit applications.  So, the options that you're using is a 64bit proc, and what errors are you receiving?  It just freezes? or... A lil more information and I'd be glad to trouble shoot you through this.

---

### Post by swisscow on 2008-09-12
No, I don't want to put Xubuntu on, I want to put 32bit Ubuntu on so I can Skype my folks. As I said in the original post, other versions of Ubuntu, Kubuntu and Crunchbang 32 bit go on fine. The live cd of Gnome Ubuntu on the other hand freezes on boot.

I can force the live cd to boot with boot parameters but then on install I have a corrupt and non-functioning system.

I have tried 2 32bit gnome Ubuntu, both with the same results. Both have been md5summed and are ok.

---

### Post by EmanresuusernamE on 2008-09-12
Have you tried VirtualBox?  You can install Ubuntu 32 bit in a virtual machine, and then run Skype off of it.

---

### Post by swisscow on 2008-09-12
Now that's a good idea. I use vmware rather than virtualbox but idea is the same

Doesn't clear up the mystery but thanks!

---

### Post by EmanresuusernamE on 2008-09-12
Where does normal 32bit Ubuntu stop working at anyways?

---

### Post by swisscow on 2008-09-12
With the livcd on boot, as the loading bar goes across the screen about one third of the way. 

If I turn the acpi off with boot options it loads, but the install is worthless

---

### Post by EmanresuusernamE on 2008-09-12
Personally, if ACPI is messing with the boot, then I'd play with the BIOS settings to see if that helps..... But it would probably just be best to install a virtual machine and go from there.  IMO, go with the 64 bit version of your choice.  You paid for 64 bit hardware, might as well get what you paid for.

---

### Post by swisscow on 2008-09-12
Probably right. Everything else with 64bit is fine, so it's no biggy.

Though I'd still be interested to know why Gnome Ubuntu  stuffs up and not the KDE version

---

### Post by EmanresuusernamE on 2008-09-12
[QUOTE=Linus Torvalds]"I personally just encourage people to switch to KDE."[/QUOTE]
Hmmm, perhaps because Linus hates Gnome and encourages KDE.  :roll:

---

