---
title: "Compiz stopped working with upgrade to Precise (Mobility radeon 7000)"
date: 2012-09-15
forum: Hardware
---

### Post by opus1 on 2012-09-15
I upgraded a Dell C610 from Ubuntu Lucid to Xubuntu Precise.  Compiz worked just fine under Lucid, but I can't seem to get it to work under Precise.  I didn't think to check what driver I was using under Lucid.

I downloaded a script called compiz-check which said "The vesa driver is not capable of running Compiz, you need to install the proper driver for your graphics card."

The AMD support site doesn't list Mobility 7000 in it's driver list.  There's a HD 7000, but I'm not sure that's the same.  

I went to the how to at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), and tried to install the fglrx driver, but all that did was clobber my login screen.

So, is Compiz not possible with my hardware under Precise?  Why the difference between Lucid and Precise?  Maybe I was using a proprietary driver?

Oh, and lspci | grep VGA gives:
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV100 LY [Mobility Radeon 7000] [1002:4c59]

---

### Post by opus1 on 2012-09-22
**** BUMP *****

Anyone?  Seriously?  I'm completely at a loss here.

---

### Post by QIII on 2012-09-22
What do you mean by "clobber my login screen"?

That looks like a "legacy" card, by the way, and the current ATI driver will not work.

The legacy driver will not work with X post 2008.  You'll need to use the default Radeon driver and we'll have to sort out why Compiz isn't working.

---

### Post by opus1 on 2012-09-22
QIII:  Thanks for the reply!

Sorry, I guess "clobber" wasn't very descriptive. I have an encrypted LVM disk setup and when in installed the fglx driver, the pretty blue screen prompting me for a password to unlock the disk turned in to a terminal based password prompt.  It doesn't really matter to me, but I thought it was curious behavior worth reporting.  Removing the fglx driver has returned the "enter password" screen back to normal.

Doing an lspci -k gives me:
```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV100 LY [Mobility Radeon 7000]
	Subsystem: Dell Device 00e3
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb

```

So it seems that I am using the radeon driver, yet I ran the compiz-check script again and it still thinks I'm using vesa.

This is a pretty old laptop, so I'm not suprised it's a legacy card. If you could let me know what info to post or troubleshooting to run, I'll do it.  In the meantime, I'll keep searching the forums.  Thanks!

---

