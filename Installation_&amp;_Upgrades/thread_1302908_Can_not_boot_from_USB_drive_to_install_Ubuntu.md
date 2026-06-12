---
title: "Can not boot from USB drive to install Ubuntu"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by cody7002002 on 2009-10-27
I'm running ubuntu on an Eeepc 1000HE and I've tried creating a USB startup disk from three different usb flash drives using the "USB startup disk creator" in ubuntu but none of them will boot upon startup. I've gone into the settings and changed the boot order so that the usb drive will boot first but even after doing that, it won't boot.

Is there something else I need to do? Is there another way I can make it boot?

---

### Post by lukeiamyourfather on 2009-10-27
Usually with a USB flash drive you have to explicitly tell the system to boot from it at startup, the BIOS options for booting order will usually not recognize a USB flash drive correctly. When it boots there's a key for selecting a boot device, not sure what it is on that system but probably one of the function keys. The flash drive should show up in the boot device selection and select it there. Cheers!

---

### Post by cody7002002 on 2009-10-27
Thanks for that but I need some more specific information

---

### Post by lukeiamyourfather on 2009-10-27
> **cody7002002 said:**
> Thanks for that but I need some more specific information

Check your manual for what key to press when booting to get the boot device selection prompt. Its different for each system. If you don't have the manual then check the Asus site for the PDF version of the manual. Cheers!

---

### Post by Muskegman on 2009-10-27
It should say "USB KEY" somewhere in the BIOS boot options, select that for booting from the USB flash drive

---

### Post by yvinogradov on 2009-10-27
> **lukeiamyourfather said:**
> Check your manual for what key to press when booting to get the boot device selection prompt. Its different for each system. If you don't have the manual then check the Asus site for the PDF version of the manual. Cheers!

I think it's the ESC key - press it and keep your finger on it till the menu comes up.

---

