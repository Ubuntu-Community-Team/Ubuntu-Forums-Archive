---
title: "Uninstall fresh Ubuntu 7.10 on laptop"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by wisedrunkard on 2009-10-02
I recently installed Ubuntu 7.10 on a friends laptop, hoping to upgrade to 8.04.  I'm very familiar with Hardy Heron and was hoping to submerge my friend into the Linux world.

However, after installing 7.10, I've had no success in upgrading to 8.04.  A direct download through update manager leaves the screen hanging on bootup and my burned cd of ubuntu 8.04 isn't recognized by the OS (although my official ubuntu 7.10 cd is)

So I'm stuck with an operating system that doesn't recognize burned CDs and won't install Hardy Heron correctly through update manager.  How can I upgrade from 7.10 or return to vista (i have a vista cd and a legit key written on the laptop, although the system isn't recognizing it)?

---

### Post by slakkie on 2009-10-02
You can upgrade from 7.10 by the guide shown in my signature. Have you tried that?

---

### Post by wisedrunkard on 2009-10-02
I will try to follow your directions.  Thanks for the help.  I'll let you know how it goes.

---

### Post by snowpine on 2009-10-02
7.10 has reached its "end of life" and is no longer supported, that's why you can't upgrade.

If the computer won't recognize either the 8.04 or Vista CD (if I understand you correctly) that is a hint there might be a hardware problem with the drive.

The following method is totally unofficial but has worked for me in the past. 

```
gksu gedit /etc/apt/sources.list
```

Use the find/replace feature to change every instance of "gutsy" to "hardy". Save the file and quit out of gedit.

```
sudo apt-get update && sudo do-release-upgrade
```

I hope that helps. :)

---

### Post by wisedrunkard on 2009-10-02
No luck in following the guide in your signature slakkie.  Is there another way to upgrade to 8.04?

---

### Post by slakkie on 2009-10-03
> **wisedrunkard said:**
> No luck in following the guide in your signature slakkie.  Is there another way to upgrade to 8.04?

What went wrong?

---

### Post by theozzlives on 2009-10-03
I would just burn the ISO and do a fresh install. Remember to check the MD5SUM.

---

