---
title: "Upgrade Freeze"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by guppygould on 2009-10-27
Hey all, I've just tried to update to the 9.10 beta. Everytime I press the 'upgrade' button in update-manager it freezes and I have to 'force quit' it. Is there any other way I can upgrade?

I'd really like to try the beta now as most of the bugs have probably been ironed out and the servers will be taking a hammering when the final release is out in a few days.

Any suggestions?

Thanks,

-Leo

---

### Post by jheaton5 on 2009-10-27
[See this thread]("http://ubuntuforums.org/showthread.php?t=1302538")

---

### Post by guppygould on 2009-10-27
> **jheaton5 said:**
> [See this thread]("http://ubuntuforums.org/showthread.php?t=1302538")

Cheers for the reply. I looked at those instructions you posted; do I need to change every 'jaunty' in the sources file to 'karmic'?

Thanks,

-Leo

---

### Post by adalal on 2009-10-27
> **guppygould said:**
> Cheers for the reply. I looked at those instructions you posted; do I need to change every 'jaunty' in the sources file to 'karmic'?

Thanks,

-Leo

I dont really think you have to change every repository address. Most of them should automatically change to karmic. However, you should have a look after the upgrade, and probably replace the two or three repos that haven't changed.

---

### Post by slakkie on 2009-10-27
> **guppygould said:**
> Cheers for the reply. I looked at those instructions you posted; do I need to change every 'jaunty' in the sources file to 'karmic'?

Thanks,

-Leo

Hi, do it the official Ubuntu way:

```

sudo aptitude install update-manager-core
sudo do-release-upgrade -d

```

---

### Post by jheaton5 on 2009-10-27
> **guppygould said:**
> Cheers for the reply. I looked at those instructions you posted; do I need to change every 'jaunty' in the sources file to 'karmic'?

Thanks,

-Leo

Yes. In gedit ^h opens a find and replace dialogue box.

---

### Post by jheaton5 on 2009-10-27
> **slakkie said:**
> Hi, do it the official Ubuntu way:

```

sudo aptitude install update-manager-core
sudo do-release-upgrade -d

```

Good process unless something breaks in the process.  Where does he begin to fix it?

---

### Post by slakkie on 2009-10-27
> **jheaton5 said:**
> Good process unless something breaks in the process.  Where does he begin to fix it?

Same way he does it via your manual way. From the author of update-manager: "It is the same, but do-release-upgrade has more logs."

So you would have more info for troubleshooting. Perhaps compare your way with do-release-upgrade. Check /var/log/dist-upgrade.

---

### Post by guppygould on 2009-10-27
> **jheaton5 said:**
> Yes. In gedit ^h opens a find and replace dialogue box.

I followed the process you gave and it has updated and installed a lot of stuff but I'm still in Jaunty. Any ideas?

---

### Post by jheaton5 on 2009-10-27
> **guppygould said:**
> I followed the process you gave and it has updated and installed a lot of stuff but I'm still in Jaunty. Any ideas?

Did you remember to change your /etc/apt/sources from Jaunty to Karmic?

---

### Post by guppygould on 2009-10-27
> **jheaton5 said:**
> Did you remember to change your /etc/apt/sources from Jaunty to Karmic?

Yeah, everything is 'karmic' now in that file.

I tried the other method that was listed in this thread, but it just hangs on 'checking for updates'

I don't know if this is anything related or not.

---

### Post by jheaton5 on 2009-10-27
So tell us what it's doing.  Are you booted into Jaunty? Post the result of ```
$ uname -a
```
Post your /boot/grub/menu.lst file.

---

### Post by guppygould on 2009-10-27
> **jheaton5 said:**
> So tell us what it's doing.  Are you booted into Jaunty? Post the result of ```
$ uname -a
```
Post your /boot/grub/menu.lst file.

I've just sorted it out. I left my computer searching for updates for about 50 minutes and it found it eventually. I've just booted into Karmic for the first time. 

Thankyou for the help.

-Leo

---

