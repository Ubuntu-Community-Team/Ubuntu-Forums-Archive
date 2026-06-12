---
title: "Need to reformat and reinstall - I think"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by LesterG802 on 2009-09-01
Hi-
I had loaded a version of Ubunu on an older laptop and it worked for awhile but now it does not boot properly. It found an error, but as I am so new to Linux, I am not sure how to proceed. I end up Ctl-D and then left with a blank screen. I have Ubuntu on a thumb drive and would like to format and reinstall off that usb drive. How do I do that? 
 
Thanks for any help!
 
Lester

---

### Post by earthpigg on 2009-09-01
it may still be possible to repair that install, but since it appears you'd rather just reinstall:

your motherboard will need to support booting from a thumb drive. you said it is an older laptop. ergo, it may or may *not* support this feature.

turn off the computer and insert the thumb drive.

when first you turn your computer on and it says 'press f2 to enter setup'? go ahead and press f2. or delete. or f12. whatever it says to push.

scroll through the menus and find 'boot priority' or 'boot order' or something similar. look for a USB entry, and bump it to the top. save changes and exit setup. your computer should now boot off of that thumb drive.

if there is no USB entry, then your motherboard probably does not support that feature. 

if your mobo cannot boot from USB, and the system has no functional cd drive, then let us know and we will give you a rundown on other options.

---

### Post by stlsaint on 2009-09-01
depending on just how old you system is i would recommend another version of ubuntu...maybe [DSL]("http://distrowatch.com/table.php?distribution=damnsmall") or [puppylinux]("http://distrowatch.com/table.php?distribution=puppy") these are different versions of ubuntu that are alot smaller and use less resources than jaunty.

---

