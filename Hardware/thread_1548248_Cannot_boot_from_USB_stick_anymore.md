---
title: "Cannot boot from USB stick anymore"
date: 2010-08-08
forum: Hardware
---

### Post by x-shaney-x on 2010-08-08
Ok, this isn't actually an ubuntu specific problem but I figured it's as good a place as any to ask for help.

The problem:  I suddenly cannot boot from a USB stick.

I have 3 sticks of various sizes and mostly use them for burning iso's to to test various distros.
This has been working fine on this computer since I got it - an HP G62 around a month old.

So anyway, the computer has 2 ways to boot from USB:
1.  Go into BIOS and change boot priority
2.  Press ESC on startup to get various boot options, including selecting the boot device.

Suddenly last night, after burning another iso I tried booting it but whichever method I use the USB stick isn't detected on boot at all, not listed as a boot device in the boot menu and changing the boot priority in BIOS it just goes straight to grub.

So I have tried burning to the other 2 sticks and the same happens.

With all 3 sticks they show up as normal if I plug them in at the desktop and I can write to them normally in windows or linux.

Checked my BIOS settings (even though I haven't changed anything else) and everything seems fine, just to be sure I loaded the default settings.

Does anyone have any idea what could be going off here?

---

### Post by clrg on 2010-08-08
Your source distro file most likely doesn't contain an MBR. (Also, you don't burn. You only copy it to the flash memory. Burning is an optical process when writing data to a CD/DVD.)

---

### Post by C.S.Cameron on 2010-08-08
That happened to my laptop a while ago.
I added a flash drive option to my grub menu and that works even better because I can leave the flash drive plugged in and still get a choice of what to boot.

---

### Post by x-shaney-x on 2010-08-08
@ clrg
No it's not that, I burned (as I call it) using both gtk software creator and unetbootin.

Have since tried again on maverick because I know both apps are a bit problematic on lucid.
I must stress usb sticks WERE booting fine before last night.

@ C.S.Cameron
Yes I have tried that too (using both 1,0 and 1,1 etc) which also worked before but no longer.

If it was one drive I would assume it was just dying off since one of them has been heavily used but 3 drives all stopping working at the same time is slightly unusual I would say.

---

