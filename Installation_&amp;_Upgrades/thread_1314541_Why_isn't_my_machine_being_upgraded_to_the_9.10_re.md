---
title: "Why isn't my machine being upgraded to the 9.10 release?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by sonicbs on 2009-11-04
Hello,

I have been using Karmic since the Beta release (and loving it!). I keep updating my machine with the Update Manager and I was successfully upgraded from the Beta to the Release Candidate, but from there on, I was not upgraded to the final release. I keep getting updates, but I didn't go through a "distribution upgrade" as I usually do. Another thing is that my grub menu displays "Development Branch" next to the 9.10 entry - this leads me to believe I am still running the RC version and not the final one.

Is there any way to be sure what version I am running? If I am correct, can someone help me understand why my machine doesn't upgrade to the final release?

Thank you for the help!

---

### Post by howefield on 2009-11-04
If you were running the RC and taking all the updates, you should now be running the finished release.

What is the output of typing the following into a terminal ?

```
cat /etc/lsb-release
```

Does it say development branch in there ?

---

### Post by mxc1090 on 2009-11-04
Have you tried this in the terminal?:
```
sudo update manager -d
```

Sorry, can't be of much help.

---

### Post by wojox on 2009-11-04
Try:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by sonicbs on 2009-11-04
> **howefield said:**
> If you were running the RC and taking all the updates, you should now be running the finished release.

What is the output of typing the following into a terminal ?

```
cat /etc/lsb-release
```

Does it say development branch in there ?

This is the output I get from running the above command:
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

So, am I running the final release?! If so, sorry for wasting people's time, and thanks for this helpful command.

---

### Post by howefield on 2009-11-04
> **sonicbs said:**
> So, am I running the final release?!

I get exactly the same output with a clean install of 9.10.

If you follow also the advice from wojox, that'll make sure you have everything but I'm sure you already have.,

---

### Post by coffeecat on 2009-11-04
I'm posting from my Karmic laptop install which I first installed on July 22nd from a daily snapshot ISO just **before** Alpha3 was released. So, originally it was a sort of Alpha 2¾. It's fully upgraded and steady as a rock - a tribute to the Ubuntu devs. So I consider I'm running the final and have no intention of re-installing.

I get the same "cat /etc/lsb-release" output as you but, interestingly, my grub menu no longer shows "Development Branch", if it ever did - tbh I can't remember.

Are you running the latest 2.6.31-14 kernel?

---

### Post by howefield on 2009-11-04
> **coffeecat said:**
> I get the same "cat /etc/lsb-release" output as you but, interestingly, my grub menu no longer shows "Development Branch", if it ever did - tbh I can't remember.

Are you running the latest 2.6.31-14 kernel?

I imply from sonicbs first post, that he clean installed the Karmic Beta, which labelled the grub menu as a Development Branch, and grub itself won't update unless he does a clean install with 9.10, so he is stuck with it, barring a clean install of 9.10. Or a manual updating of grub which probably isn't worth the bother.

---

