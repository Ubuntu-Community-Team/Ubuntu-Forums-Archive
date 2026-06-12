---
title: "Jaunty Acer 5516"
date: 2009-07-04
forum: Hardware
---

### Post by HarshReality on 2009-07-04
Recently acquired a Aspire 5516 as a 'road box' with Vista home x32 (*yuck*).  Since Im running Jaunty on my desktop I figured I'd throw it out as a secondary OS (first boot option though :P) on the laptop.

Here's my boggle.. 8.04 boots and goes into live. 9.04 does not. Tried safe mode.. tried noacpi.. nothing. Beyond the boot screen the kernel will simply not load.

Suggestions?

Spec: [http://us.acer.com/acer-v2/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=62400&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=447&ctx1.att21k=1&CRC=3591499304](http://us.acer.com/acer-v2/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=62400&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=447&ctx1.att21k=1&CRC=3591499304)

---

### Post by HarshReality on 2009-07-04
Resolved.. defective media (ordered CDs).

---

### Post by reed_v on 2009-07-06
I bought this computer over the weekend at Staples for $299.  I'm trying to decide if I should keep it.  Are you satisfied with the performance with 8.04 or 9.04?  Any comments about general performance with Windows?  Thank you!

Reed

---

### Post by HarshReality on 2009-07-06
In terms of linux, its quite good. SDCards read.. wireless was out of the box. The only issue I had was with the hard LAN and there is information about that all over to compile the driver. As the wireless is Broadcomm it not compatible with backtrack (so wardriving isnt really an option). But it doesnt stall in the least. 

Windows.. just for grins before I did a linux install I did a restore a few times. Seems with each restore the windows side got 'quirks'. For example, when going into Vista home the audio was originally clear and smooth yet after a few restores it started to chop on startup.

A few things to note.. and hold in mind Im no linux god..
I resized the partition (Vista) and freed up @ 50G and installed ubuntu there (9.04). THe boot options gave me linux, vista as well as the restore partition :)

On uninstall of linux (grub removal) I simply booted a Vista DVD and chose repair. At the command prompt typed:
'Bootrec.exe /FixMbr' and then rebooted. Here is the quirk.. if you do this you wont have access to the restore partition directly(at startup pressing Alt+F10). However it does come with Acers eMaint. package which can access the partition from within Vista. If you run that and tell it to restore C completely then once its done you can press Alt+F10 at startup to access the automated restore functions again. Then just drop the linux partition from within Vista

Cant tell you why unless its a bootsector thing.. but that is what it took.

Overall for what it is its a damn beefly lil laptop!

Anything I can help with drop me a PM and I'll answer what I can :)

*Upon reading this over I suppose I could have chosen the restore partition from grub and got the same results as going through the DVD and what not.. will have to try that later today.

---

### Post by FoAlBo on 2009-07-06
I too picked up a 5516.  Its for a friend and want to install Ubuntu over the factory installed Vista.  My concern is the NIC not working when installing 9.04 without manual intervention.  My friend is not computer literate and if a future kernel upgrade breaks the NIC I'll have to go visit the laptop (30 miles) away to get it working again.  I suppose I could create a script that runs the commands to fix the NIC when it breaks or return the laptop and look for another that is supported by 9.04.  Any suggestions?

---

### Post by HarshReality on 2009-07-07
One would think if it were installed as a module in the kernel that during the upgrade process it would be recompiled (like the nvidia driver) but as I said Im not really that good at kernel compilation so I cant really speculate.. however the idea of a script does seem appealing.

---

### Post by FoAlBo on 2009-07-07
thanks for the response.  I'll discuss it with him.  I'll put an icon on the desktop for the script so in case it does stop working it will be an easy fix.  Although I worked on Unix systems prior for the past 10 years its been a Windoze world.  I really think Ubuntu is great.

---

### Post by BruceG on 2009-10-07
I just bought one of these (model AS5516-5112 to be precise) and also have problems with the networking.

I have upgraded to the latest stable kernel, which includes the atl1c driver for the wired ethernet card.  It boots and works fine initially, both the wired and wireless networks (wireless needs the backports modules).  However after downloading about 90MB the wired network completely stalls out.  No further traffic is received (even pings) until I unload and reload the atl1c module.

Is there anything I can try to get this to work better?

---

