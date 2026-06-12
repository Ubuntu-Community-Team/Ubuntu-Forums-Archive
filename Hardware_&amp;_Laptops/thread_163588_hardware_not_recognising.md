---
title: "hardware not recognising"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by troyDoogle7 on 2006-04-21
Hi All 

PLease can you help me to find out which hardware hasn't been installed/recognised by ubuntu.  My usbs don't seem to work and I am trying to find out if they have been recognised.  In windows there was a question mark next to not installed hardware.  Does ubuntu do the same thing?

Please help!

---

### Post by bscbrit on 2006-04-21
type (or cut and paste) the following command in a terminal

sudo lshw >~/myhardware.txt

A list of all of your hardware will now be contained in 

/home/[username]/myhardware.txt

---

### Post by troyDoogle7 on 2006-04-21
Thanks for the help, 
I just did that and it mentions usb under the bios capabilities but no where else.

Is there a way to get it to recognise the usb.  I know that it was working under hoary, what could be going wrong?  Did they take out usb 1.0 drivers?

---

### Post by bscbrit on 2006-04-21
The fact that the BIOS is usb capable does not mean that anything is connected to it, or that the BIOS has had the USB enabled.

If both Windows and Ubuntu are having a problem finding your usb devices there is probably something wrong with the hardware configuration.

When the computer boots, it usually lets you enter the BIOS by pressing a specific key (sometimes Esc, sometimes Del or perhaps F1 or F2.)  This option is usually only available for a few seconds immediately the computer is restarting.  If you are confident that you know what you are doing, enter the BIOS configuration and check that the USB is actually enabled on your computer.  Some BIOS do not do this as default.  If it is not enabled, then enable it.  Be careful when making changes in the BIOS.  Changing the USB setting is usually safe, but do not change anything else unless you know EXACTLY what it will achieve.  You can stop your computer from booting if you make the wrong selection.

If you are not confident that you can do this, have you got a friend or someone else who might be able to help you?

---

### Post by troyDoogle7 on 2006-04-22
Hi Mate, The problem is that it recognises fine in windows but not unbuntu! 

I was wondering if there was a way to force ubuntu to redetech usbs or perhaps to update drivers for usbs

---

