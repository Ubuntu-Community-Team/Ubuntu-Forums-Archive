---
title: "Xubuntu 7.04 won't Power-off my Laptop!"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by CodyZ on 2007-09-20
Hey there!  I recently installed Xubuntu 7.04 on my Toshiba 3110ct laptop, and I couldn't be happier with it other than when I select "shutdown" it doesn't actually power-off my machine.  The computer exits X, and shows the reverse splash screen but the power stays on and I have to manually hit the power switch to shut off the laptop.  Previous to xubuntu I had XP on there and  it would shut the machine off all the way, so I know it can be done.

Does anyone have any ideas?  I would really appreciate it, thanks!

---

### Post by lisati on 2007-09-20
I haven't had a "shut down" problem on my Toshiba laptop - I had no sound to start with. The solution I found included installing all the updates to the system.

---

### Post by ajgreeny on 2007-09-20
For some time a while ago I had the same problem with my desktop running ubuntu with **kubuntu-desktop** added on top, and using kubuntu mostly.  I seem to have solved the problem by removing the **ubuntu usplash**, and all the **evolution** packages which I never used, together with the **ubuntu-desktop** package.  It performs faultlessly now.  You may or may not get any clues as to where to try answers from this, but I thought it worth passing on the info.

---

### Post by roxy99 on 2007-09-20
I have the same problem with my Thinkpad A21m.  Its no big deal, the shutdown succeed to close all services except the splash screen XUbuntu remains and I have to physically hit the switch at that point.  Its seems to be a common problem that I can live with.  

The only danger is if you forget to hit the swich and in haste pack the laptop in the bag with power running, then you could overheat and damage the laptop.  So be careful.

---

### Post by jongkind on 2007-09-20
If possible an upgrade of your BIOS might solve this issue.

---

### Post by CodyZ on 2007-09-20
> **ajgreeny said:**
> For some time a while ago I had the same problem with my desktop running ubuntu with **kubuntu-desktop** added on top, and using kubuntu mostly.  I seem to have solved the problem by removing the **ubuntu usplash**, and all the **evolution** packages which I never used, together with the **ubuntu-desktop** package.  It performs faultlessly now.  You may or may not get any clues as to where to try answers from this, but I thought it worth passing on the info.

Yeah, I'm not sure where I'd start to do that.  I'm sort of new with linux.

---

### Post by CodyZ on 2007-09-20
> **roxy99 said:**
> I have the same problem with my Thinkpad A21m.  Its no big deal, the shutdown succeed to close all services except the splash screen XUbuntu remains and I have to physically hit the switch at that point.  Its seems to be a common problem that I can live with.  

The only danger is if you forget to hit the swich and in haste pack the laptop in the bag with power running, then you could overheat and damage the laptop.  So be careful.


I know it's not a huge problem, but I'd still like to fix it.  It worked fine with Windows XP, so I know it's just a matter of getting the right hardware drivers or something to get it to work with linux.  I don't think I should have to sacrifice some of my machine's functionality just because I switched to linux.

---

### Post by roxy99 on 2007-09-21
If you do figure it out please post back your solution to others.  Personally from experience I know that when I try to fix minor issues often times I end up breaking something else.  Especially being a new user with Linux I don't want to take chances.  FWIW though I think its got to be either the bios or the kernal doesn't support your laptops power down.  Everyone's laptop is different so YMMV.  You also need to realize that sometimes not every driver for every piece of hardware exists for Linux as it does for Windows.  Eg:  My dial-up modem is built into my laptop and in windows is plug and play detected, drivers and all.  In Linux, there is not compatible driver I can find.  There may be someone who provided a fix somewhere but I haven't found it and I could find it if I dig enough.  Hoewver, I'm using broadband internet so who cares.  I decided its not worth fixing.

Linuxes achilles heel has always been driver support and not having as easy an installation as windows.  When you do get everything working its very rewarding to have a secure and stable system and no worries about viruses and spyware.

---

### Post by CodyZ on 2007-09-21
> **roxy99 said:**
> If you do figure it out please post back your solution to others.  Personally from experience I know that when I try to fix minor issues often times I end up breaking something else.  Especially being a new user with Linux I don't want to take chances.  FWIW though I think its got to be either the bios or the kernal doesn't support your laptops power down.  Everyone's laptop is different so YMMV.  You also need to realize that sometimes not every driver for every piece of hardware exists for Linux as it does for Windows.  Eg:  My dial-up modem is built into my laptop and in windows is plug and play detected, drivers and all.  In Linux, there is not compatible driver I can find.  There may be someone who provided a fix somewhere but I haven't found it and I could find it if I dig enough.  Hoewver, I'm using broadband internet so who cares.  I decided its not worth fixing.

Linuxes achilles heel has always been driver support and not having as easy an installation as windows.  When you do get everything working its very rewarding to have a secure and stable system and no worries about viruses and spyware.

As soon as I find a solution, I will post it.  In the meantime though, how can it be a bios issue if the laptop powered down correctly with windows?  If it is a bios or kernel issue, what are the steps to take to resolve it?

Thanks!

---

### Post by roxy99 on 2007-10-12
> **CodyZ said:**
> As soon as I find a solution, I will post it.  In the meantime though, how can it be a bios issue if the laptop powered down correctly with windows?  If it is a bios or kernel issue, what are the steps to take to resolve it?

Thanks!

The BIOS is the gateway to your PC's hardware between whatever OS is installed and communicating the features of your  hardware to your OS.  So while there may be nothing wrong with your BIOS and powerdown,  Linux is not using it right now.  I am newb so I have no answers for you unfortunately.

---

### Post by CodyZ on 2007-10-14
> **roxy99 said:**
> The BIOS is the gateway to your PC's hardware between whatever OS is installed and communicating the features of your  hardware to your OS.  So while there may be nothing wrong with your BIOS and powerdown,  Linux is not using it right now.  I am newb so I have no answers for you unfortunately.

Exactly, so how do I get linux to use my bios properly, like windows was?

-C

---

### Post by DonQuichote on 2007-10-14
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=22041](http://ubuntuforums.org/showthread.php?t=22041) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Shutting down is managed by a BIOS section called ACPI. You should be able to find it in your BIOS. If you cannot find it (like on my HP Omnibook XE3), you have a very old BIOS. The first thing to do is looking for an upgrade of it.

If there is no upgrade (like for my laptop), you may still force linux to use it. This is explained in:

[http://ubuntuforums.org/showthread.php?t=22041](http://ubuntuforums.org/showthread.php?t=22041)

For me, it has solved 2 problems:
1. My laptop now shuts down when I tell it to,
2. If it is low on battery, the BIOS no longer tries its crappy way of storing the memory to disk, which it cannot do reliably anyway.

*YOUR* BIOS might do a good job in backing up data on low power. In that case, it can be better to live with the manual switching off...

Good luck!

---

### Post by scrooge_74 on 2007-10-14
Check for powersaved been installed, there is also a package for managing acpi features for toshiba, look it up in synaptic, i think is call toshset.

This is the link for the app,

[http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html)

---

### Post by CodyZ on 2007-10-14
> **DonQuichote said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=22041](http://ubuntuforums.org/showthread.php?t=22041) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Shutting down is managed by a BIOS section called ACPI. You should be able to find it in your BIOS. If you cannot find it (like on my HP Omnibook XE3), you have a very old BIOS. The first thing to do is looking for an upgrade of it.

If there is no upgrade (like for my laptop), you may still force linux to use it. This is explained in:

[http://ubuntuforums.org/showthread.php?t=22041](http://ubuntuforums.org/showthread.php?t=22041)

For me, it has solved 2 problems:
1. My laptop now shuts down when I tell it to,
2. If it is low on battery, the BIOS no longer tries its crappy way of storing the memory to disk, which it cannot do reliably anyway.

*YOUR* BIOS might do a good job in backing up data on low power. In that case, it can be better to live with the manual switching off...

Good luck!

I tried adding acpi=force to the 2 lines in the menu.lst file as instructed in that post.  It had no effect on my shutdown, I'm wondering it I put them in the correct lines.  I just did them in the lines that looked the most similar, but they were labeled "title."  I am running xubuntu, so maybe my menu.lst is slightly different?

---

### Post by scrooge_74 on 2007-10-15
Post where you put them, they should go in a line like this

kernel		/boot/vmlinuz-2.6.21-2-686 root=/dev/hda1 ro pci=routeirq

(your may be a lot different), but should start with kernel

---

### Post by CodyZ on 2007-10-15
> **scrooge_74 said:**
> Post where you put them, they should go in a line like this

kernel		/boot/vmlinuz-2.6.21-2-686 root=/dev/hda1 ro pci=routeirq

(your may be a lot different), but should start with kernel

That totally worked!  Thank You!  Cool quote btw.

---

