---
title: "Packard Bell easynote MH53"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by GreatSlovakia on 2008-01-18
I recently acquired a new laptop for my younger brother namely the Backard Bell Easynote MH35 and when booting ubuntu in any way (tried Wubi as well) it stops on the loading please wait or the loading bar freezes. So what can I try now... I just need some way to determine the problem itself or at least an error message, from that point I will most likely be able to do the rest myself.

So, where can I find a documentation about what happens during the Loading... Please wait part...

Update: Like in [http://ubuntuforums.org/showthread.php?t=247703](http://ubuntuforums.org/showthread.php?t=247703) it hangs at the mounting file system, but I do not get any error messages.

---

### Post by jeffus_il on 2008-01-18
When you boot there is a program called grub which appears for a few seconds, type "e" when it appears, add nosplash to the end of the line, type "b" to boot, with some luck you may see the error(s).

---

### Post by GreatSlovakia on 2008-01-18
Well I tried some more things, and I now got an error which isn't really helping a lot: usbcore: registered new device driver usb. I wondered whether there is a way to disable the usb's from the boot options.

---

### Post by jeffus_il on 2008-01-18
> **GreatSlovakia said:**
> Well I tried some more things, and I now got an error which isn't really helping a lot: usbcore: registered new device driver usb. I wondered whether there is a way to disable the usb's from the boot options.

That doesn't really look like an error, Is that the last output before the machine freezes?
You could disable the usb in bios temporarily, but I don't know if it will help.

---

### Post by GreatSlovakia on 2008-01-18
Yes, you are right it is the last outputted message... And I have been spitting through the bios, but I am unable to find any option in the bios to disable the usb-ports... any advice...

---

### Post by jeffus_il on 2008-01-18
Is your problem a LiveCd booting problem, or have you already done the installation?

---

### Post by GreatSlovakia on 2008-01-18
Its a liveCD problem, but happens as well through the wubi alternate cd boot. (Tried it in the beginning both with the ubuntu and the kubuntu live cd)

Note: The wubi installer uses the 7.04 version

---

### Post by jeffus_il on 2008-01-18
It's reasonable to assume that the LiveCd doesn't like something about your hardware, you should look at boot parameters given to the kernel thru the grub menu, like acpi and so-on. maybe checkout bios settings, definitely restore your bios defaults, consider looking at PCI interrupts ...

---

### Post by italiano on 2008-02-14
> **GreatSlovakia said:**
> I recently acquired a new laptop for my younger brother namely the Backard Bell Easynote MH35 and when booting ubuntu in any way (tried Wubi as well) it stops on the loading please wait or the loading bar freezes. So what can I try now... I just need some way to determine the problem itself or at least an error message, from that point I will most likely be able to do the rest myself.

So, where can I find a documentation about what happens during the Loading... Please wait part...

Update: Like in [http://ubuntuforums.org/showthread.php?t=247703](http://ubuntuforums.org/showthread.php?t=247703) it hangs at the mounting file system, but I do not get any error messages.

I've had the same problem on the same laptop... I've solved it by adding 

noapic nolapic acpi=off

at the boot option of the live cd.. (just press f6)

It didn't recognized the soundcard, the lan card and the video card, but it worked...

Yesterday I've updated the bios and the lan card support from the packard bell site.. and I've found that the lan card started working

I also compiled from source the ALSA 1.0.16 and it recognized the soundcard.. 

The only problem I have today is the resolution of the screen (1280x768 when it should be 1280x800)..

Hope it helps...

---

### Post by cichlid on 2008-02-17
Hi All, I am having also installation problems with Packard Bell MH35 (-U-031). I have tried all soulutions above. Has anyone a working solution for the freezing screen mentioned above. It would be greatly appreciated as i am an ubuntu user for two years and now forced to use vista on this laptop. Thanks in advance !

---

### Post by mikewynn on 2008-04-17
Hi,

For Windows  Xp user, you can visit this site for drivers:

[http://www.wynnbot.com/index.php?pr=Drivers_Download](http://www.wynnbot.com/index.php?pr=Drivers_Download)

Good Luck
MikeWynn

---

