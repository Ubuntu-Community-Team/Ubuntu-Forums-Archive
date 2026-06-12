---
title: "Lost Touchpad"
date: 2014-12-30
forum: Hardware
---

### Post by asearle on 2014-12-30
Hi Everyone,

I installed Lubuntu on a laptop yesterday and was happy that all hardware was recognised and worked immediately (Bravo Ubuntu!).  This included the touchpad with all scrolling features (Bravo again!).  However, later in the evening the touchpad started to become erractic (including "locking up" for short periods).

Then, when I started the laptop this morning, the touchpad was dead and I reverted to using the mouse.  This was strange as I hadn't installed anything (including updates) which might have messed it up.

I then booted with the original live-DVD expecting to be able to use the touchpad but it was still dead. This made me think that the problem was hardware.

My next step was to get the computer-shop where I had bought the laptop to test the touchpad with a Windows live-DVD ... and it worked!  This tells me that the problem is not in the BIOS.

Now this has me completely confused:  How can it be that the touchpad worked once with the Lubuntu live-DVD and now it doesn't ... but it does work with a Windows live-DVD?

Does anyone have a tip for me?  Or should I maybe simply wait until a Lubuntu update corrects the problem?

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by tgalati4 on 2014-12-30
I would reseat the ribbon cable on the touchpad.  Clean around the edges with a corner of a business card.  Use some tape to pull out stuff in the corners.  Don't use water or alcohol--keep it dry.

It's possible that the electronics that drive the touchpad have developed a fault.  Rebooting into Windows gives the chips time to cool and work again.  It's possible that you can duplicate this behavior by shutting down for 10 minutes and then booting Ubuntu.  If the touchpad works and then stops, then try the same in Windows.  If it works for several hours while in Windows, then it might be a software problem.

Look in your log files for any input errors:

```
dmesg | tail -100
more /var/log/Xorg.0.log

```

Touchpads can get zapped with static electricity--especially in winter.

---

### Post by asearle on 2014-12-30
I have tried booting with all the live-DVDs that I could find in my cupboard but the touchpad remains stubburnly absent  :-/

I then went back to the shop (the laptop is very new) and we tested again with a Windows (8.1) live-DVD.  The touchpad worked fine and was recognised as "Microsoft PS/2 Mouse".

As it is I think that I will give up and work with an external mouse for a few weeks and see if any (L)Ubuntu updates fix the problem.  I am optimistic that they will.

But I have noticed that, with Lubuntu, the keyboard shortcuts don't seem to be active.  This is a bit irritating because if, at any time, I forget to take a mouse, I will not be able to use the laptop at all.  So it would be interesting to know if there is a way to switch on keyboard shortcuts:  This would help me in an emergency.

I'll post a message when the problem is solved.

Regards and thanks for the tips,
Alan

---

### Post by asearle on 2014-12-31
Keyboard shortcuts can be used with "Alt-F1".

Here is an explanatory link ...

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

---

### Post by flaymond on 2014-12-31
Do you install Lubuntu using UEFI?

---

### Post by asearle on 2015-01-04
It's a new laptop and, yes, I believe based on UEFI.  I've looked in the BIOS and "EFI" is mentioned but I'm not sure how to check exactly.

Today I reset the BIOS (or EFI?) to factory defaults but the touchpad is still not available.

One thing I did (I believe) before the touchpad disapeared was to open "Input Methods" but I believe I closed without saving anything.

The strange thing here is that the problem occurs with Linux boots (various live DVDs) but not with a Windows live DVD.  Does this mean that Linux has written something to the firmware?

Anyway, I find it so strange that the touchpad worked initially but doesn't work now.

Maybe an update will fix the problem (?)

Many thanks for any tips.

Yours,
Alan

---

