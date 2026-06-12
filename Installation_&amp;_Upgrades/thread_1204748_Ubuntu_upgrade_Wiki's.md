---
title: "Ubuntu upgrade Wiki's"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by mikodo on 2009-07-05
Hello everyone,

New to Linux and Ubunutu since April 2009. I am presently running Ubuntu 8.04 and loving the whole scene. I will eventually be upgrading and probably will continue with LTS again. I need to start reading up on what preparations I need to do, to make the transition of personal data like my home folder and applications I regularly use and want, to allow me to easily and safely transfer.

Can you folks recommend Wiki's and other sites that address these questions in upgrades?

Approaching 04:00 and I need to get to bed. I'll leave this post out there, and check on it another time. 

Thank you

---

### Post by Sef on 2009-07-05
> I will eventually be upgrading and probably will continue with LTS again. I need to start reading up on what preparations I need to do, to make the transition of personal data like my home folder and applications I regularly use and want, to allow me to easily and safely transfer.

1) Uninstall any proprietary drivers and all PPAs.   That should increase the chances that all will go well.  

2) Back up your data because there are no 100% guaranatees that all will go well.

---

### Post by mikodo on 2009-07-05
> **Sef said:**
> 1) Uninstall any proprietary drivers and all PPAs.   That should increase the chances that all will go well.  

2) Back up your data because there are no 100% guaranatees that all will go well.


Thanks again, Sef. 

To be clearer, I am already running Ubuntu 8.04.2 with updates and will eventually upgrade to the new Ubuntu LTS 10.4; probably 10.4.2, when it is ready. With this, is there anything else I should do in preparation? 

Second question:

What transition process is recommended as being easiest and safest by people of limited knowledge as myself as a Newbie?

Where can I read up on accepted upgrade procedures?

Thank you

---

### Post by mikodo on 2009-07-06
Anyone?

Thanks

---

### Post by darolu on 2009-07-06
The easiest and safest way is to let it upgrade via network, it works automatic.
What you may lose this way are some applications and some applications preferences as new versions of programs will be available. Little tip: If you don't already have your /home on a separate partition, you may want to do it.

You can also use the Alternate CD to safely upgrade, works similar to network upgrade.

This is a link with instructions to network upgrade to 9.04, the process will be very similar (if not exactly the same) to jump from LTS to LTS.

[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29)

If you want to network upgrade to "normal releases" from LTS this link is what you need:

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

I hope this helps.

---

### Post by mikodo on 2009-07-06
> **darolu said:**
> The easiest and safest way is to let it upgrade via network, it works automatic.
What you may lose this way are some applications and some applications preferences as new versions of programs will be available. Little tip: If you don't already have your /home on a separate partition, you may want to do it.

You can also use the Alternate CD to safely upgrade, works similar to network upgrade.

This is a link with instructions to network upgrade to 9.04, the process will be very similar (if not exactly the same) to jump from LTS to LTS.

[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20%28Recommended%29)

If you want to network upgrade to "normal releases" from LTS this link is what you need:

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

I hope this helps.

Hey now, this is the stuff I need to read to prepare myself for my first Ubuntu Distro upgrade! Your advice on putting my home folder on a separate partition is well taken, as I have seen the same advice given to others in this forum. I will certainly do this before upgrading.

Thank you darolu!

mikodo

---

### Post by mikodo on 2009-07-06
Well of course I have another question now. Reading the links above, it gives advice on how to upgrade for both Ubuntu and Kubuntu. I use both (Kubuntu for a app specific to it). Can I upgrade both or will I loose the Kubuntu when upgrading the Ubuntu first, or should I put Kubuntu on a separate partition first before beginning the upgrades.

Thanks

---

### Post by earthpigg on 2009-07-06
> **mikodo said:**
> Well of course I have another question now. Reading the links above, it gives advice on how to upgrade for both Ubuntu and Kubuntu. I use both (Kubuntu for a app specific to it). Can I upgrade both or will I loose the Kubuntu when upgrading the Ubuntu first, or should I put Kubuntu on a separate partition first before beginning the upgrades.

Thanks

kubuntu and ubuntu are both just software packages. specifically, you have the ubuntu-desktop package installed, and the kubuntu-desktop package installed.

both *should* upgrade just fine and remain functional.

(the question about putting kubuntu on a separate partition does not apply -- its just another software package, *not* a separate OS :P )


edit: also, it _**is**_ possible to run KDE apps inside Gnome. just start it, and it should run fine.

(kubuntu = ubuntu with KDE desktop environment. ubuntu = ubuntu with Gnome desktop environment.

---

### Post by mikodo on 2009-07-06
> **earthpigg said:**
> kubuntu and ubuntu are both just software packages. specifically, you have the ubuntu-desktop package installed, and the kubuntu-desktop package installed.

both *should* upgrade just fine and remain functional.

(the question about putting kubuntu on a separate partition does not apply -- its just another software package, *not* a separate OS :P )


edit: also, it _**is**_ possible to run KDE apps inside Gnome. just start it, and it should run fine.

(kubuntu = ubuntu with KDE desktop environment. ubuntu = ubuntu with Gnome desktop environment.

That answers the last question I have for this thread.

Thanks earthpigg!

---

