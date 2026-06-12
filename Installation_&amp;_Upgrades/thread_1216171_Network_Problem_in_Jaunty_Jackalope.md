---
title: "Network Problem in Jaunty Jackalope"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by johnnylitson on 2009-07-18
Hi,

I recently installed Ubuntu 9.04 Jaunty Jackalope implementing my friend's suggestion and it is certainly the best OS ever. I do not know anything about Linux and i could install it with ease which is truly wonderful. The whole installation process took only 15 minutes :).

However my only problem is about the Network configuration :(.  If I go to
"System --> Administration --> Update Manager" and update the system,the Wired Network Connection gets disabled. That's not the only case too, the Wired network also gets disabled on every alternative startup of the system. I tried to figure out what the problem was (even though I am Linux illiterate) but alas i could not find out what the problem was. 

Can you guys please help me out over here:confused:. I need Internet and I.P configuration to be enabled.

Thanks a lot in advance guys.

---

### Post by Bucky Ball on 2009-07-18
Try:

System->Admin->Synaptics Package Manager

Search for and install 

ubuntu-restricted-extras

---

### Post by johnnylitson on 2009-07-18
Thanks Bucky,

But, I could not find any "ubuntu-restricted-extras" in the synaptic package manager... :(

And I even cannot change the permissions of the system files, Why is that so??

---

### Post by coffeecat on 2009-07-18
> **johnnylitson said:**
> However my only problem is about the Network configuration :(.  If I go to
"System --> Administration --> Update Manager" and update the system,the Wired Network Connection gets disabled. That's not the only case too, the Wired network also gets disabled on every alternative startup of the system. I tried to figure out what the problem was (even though I am Linux illiterate) but alas i could not find out what the problem was. 

This is very puzzling. Normally, a wired networking connection is very stable. Offhand I cannot think of how a system update can disable networking (except for a buggy update - but there hasn't been one that bad recently) or why networking would work only on alternate boots.

Please provide more information. Describe your networking setup: internet connection type, modem type, exactly how you connect the computer to the router (if you have one), whether you have router(s) and ethernet switch(es), whether you have other machines on the network, etc.

Have you been changing any hardware between bootups? Could this have affected networking? How are you re-enabling networking when it gets disabled?

> **johnnylitson said:**
> I could not find any "ubuntu-restricted-extras" in the synaptic package manager... 

I don't understand why Bucky Ball recommended you to install ubuntu-restricted-extras. That's a meta-package which pulls in a load of useful multimedia stuff, microsoft core fonts, JAVA runtime and flash. If you can find it, it's well worth installing, but I can't see how it could help your networking problem. However... if you can't find it in Synaptic, something's not right. Open Synaptic, go to Settings > Repositories and under the 'Ubuntu Software' tab make sure that the 'Software restricted by copyright (Multiverse)' box is ticked. Close the little window and click on 'Reload' (making sure your networking is re-enabled). Now look for 'ubuntu-restricted-extras'. Is it there?

> **johnnylitson said:**
> And I even cannot change the permissions of the system files, Why is that so??

Why are you wanting to change the permissions of the system files? **Don't**. You are new to Linux. You could do untold damage like this if you don't know what you are doing. Have you already been tinkering about in the system? If so, this could be why you are experiencing networking problems.

---

