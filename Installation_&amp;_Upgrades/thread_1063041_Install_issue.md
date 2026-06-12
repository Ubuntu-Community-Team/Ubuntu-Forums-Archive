---
title: "Install issue"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by esullivan on 2009-02-07
I am installing 8.10, it installs fine.  When I reboot after the install, it asks to log in.  After that the screen goes black with just the mouse, which I can move around.  I did leave it for 15 mins.

I pushed and held the power button to restart, when it comes back up, the screen is the orange\tan Ubuntu color with the mouse.  Again I am move the mouse but never get to the desktop.

I know a little about Linux but not a lot.

Thanks

---

### Post by mono-jo on 2009-02-07
i had the same problem i just reinstalled

---

### Post by esullivan on 2009-02-07
> **mono-jo said:**
> i had the same problem i just reinstalled

I tried that.  Re-installed again, same thing.

---

### Post by alkybird on 2009-02-07
I have the same problem with a fresh install on my wife's old Dell inspiron 1100. I tried reinstalling but it didn't help. I also tried the live CD version to see if maybe an install was getting botched but her laptop is old enough to apparently not be able to run ubuntu. I will try Xubuntu next and hope for the best.

---

### Post by esullivan on 2009-02-07
> **alkybird said:**
> I have the same problem with a fresh install on my wife's old Dell inspiron 1100. I tried reinstalling but it didn't help. I also tried the live CD version to see if maybe an install was getting botched but her laptop is old enough to apparently not be able to run ubuntu. I will try Xubuntu next and hope for the best.

As long as the hardware meets the minimum Linux should run, I would think

---

### Post by alkybird on 2009-02-07
From what I read it should be ok. P4 2.6, 512mb ram, intel integrated gpu (this might be my killer as it only uses 8mb shared ram), 40gb HD. The gpu and ram are what make me think that xubuntu might be better but I will see. Running another install right now while I download X.

---

### Post by esullivan on 2009-02-07
As per [http://ubuntuforums.org/showthread.php?t=984296](http://ubuntuforums.org/showthread.php?t=984296)

THIS WORKED.


Try rebooting into recovery mode but instead of running xfix choose the root terminal option.

type the following command.

Code:

sudo apt-get remove compiz

Then type:

Code:

sudo apt-get remove compiz-core

Now type: exit to leave terminal then choose the resume option.

Hope this works!

---

