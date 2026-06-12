---
title: "Just installed Sabayon..."
date: 2007-04-07
forum: Gentoo and derivatives
---

### Post by floke on 2007-04-07
Have just installed Sabayon. Am writing from the LiveCD.
Am about to reboot....

<crossing over to the other side now>

(wish me luck!)

...

---

### Post by floke on 2007-04-07
Ok, so Sabayon pwned my Grub!!
All I have is an entry for Sabayon - no Feisty, and no Edgy.

Shazbat!

Still, I'm sure it can all be fixed so am not worried (yet!)

---

### Post by rsambuca on 2007-04-07
Yeah, I had to add my ubuntu stuff to the Sabayon grub menu.lst.

---

### Post by floke on 2007-04-07
Bloody rubbish!
I don't want the Sabayon (I'm only a guest OS on your machine) running the Grub show. I tried moving my full Grub (Feisty with loads of Kernels) into the Sabayon grub folder and renaming it menu.lst (adding Sabayon to it manually), but it didn't work. Pah! Am now installing a fresh Edgy over the Sabayon partition so I can reinstall the ubuntu Grub loader and be rid of the anaconda nonsense. Once there I can rescue my Feisty partition - which is what I really use anyway. Everything else is just backup,

Right now will be glad to be back in Ubuntu.

Currently 64% on the reinstall....

---

### Post by floke on 2007-04-07
Installation complete!

Hopefully see you back on the Ubuntu-side...

here goes...

---

### Post by yabbadabbadont on 2007-04-07
I wish I had seen this sooner... there was no reason to reinstall.  You just needed to reinstall grub and configure it to look for it's menu.lst file on your Ubuntu partition.  Then add sabayon to your Ubuntu menu.lst.

---

### Post by floke on 2007-04-07
Far too late....

also, to add insult to injury my entire Feisty partition is longer working properly.
Keep getti g message on boot that I need to install the 'apt-get' package - even though I obviously have it. Keeps saying that fsck has failed or something - but all my fsck's have been ok. My home dir. is also not mounted, even though its in fstab - I have to do it manually.

Thanks Sabash***  :confused:

---

### Post by igknighted on 2007-04-07
Sounds like you have met Gentoo's grub... its quite a bit different.  In fact, the config file is not even named menu.lst, but rather grub.conf.  If I had come across this earlier I would have warned you, you must manually add OS's during the install.  You can also edit grub if its misconfigured at boot by using the 'e' key to go to edit mode.

Basically, if grub is working fine, don't install a new version with a new OS, especially if you aren't sure you are going to keep it.  It is easy to add the Sabayon kernels to Ubuntu's grub (and vice versa, but again, why mess with something that works?), just look around for the syntax.

It's an unfortunate occurrence, but really very few distros recognize the others very well.  So if you plan on trying out more distros get used to messing with grub.  Its greek at first, but after a little bit it is actually very easy to follow and work with.  Porting your Ubuntu menu.lst was a good idea, the only thing you needed to do was change the path... /boot from Ubuntu's grub.conf would need to be renamed (hdo,#)/boot or /mountpoint/inSabayon/boot/.  Then it would have worked fine.

Please do not blame the distro.  I feel bad that this happened, but it is user error none the less.  Suse, PCLOS, Fedora... any of them could/would have done this as well.  Do some more homework on grub and this is easily avoided.

As for the feisty partition, lord only knows what happened... mine breaks all the time too, I doubt its related.

---

### Post by rsambuca on 2007-04-07
Steve, sorry you had such a hassle, but you really could have just reinstalled grub.  If you had posted your troubles before going through the reinstall, I am sure we could have helped you out.

Sabayon is a decent distro, so I don't think it is fair to blame it just because it is different from what you are used to.

---

### Post by floke on 2007-04-08
No that's fair enough. I was just annoyed at the time. It felt a bit like getting shot by one of your own side.

Feisty system partition is still wrecked though. On booting I get the message that there's no apt-get and it blanks to CLI. If I type reboot (or even shutdown) it then resumes booting and completes fine!

Am going to fresh install Feisty now...

---

### Post by rai4shu2 on 2007-04-08
I've been getting good at using grub and editing /etc/fstab thanks to all my testing out other distros.

Remember that in the latest Feisty, fstab uses UUID by default, which changes any time you format a partition. When you drop to root shell, you need to edit your fstab and change the partitions that were formatted to their new UUIDs.

---

