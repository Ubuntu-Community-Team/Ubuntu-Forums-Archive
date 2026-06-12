---
title: "many issues..."
date: 2008-12-13
forum: Hardware
---

### Post by Snappo on 2008-12-13
The latest kernel upgrade broke my USB, this means I can't use the net because my atheros won't work. I've been using Ubuntu for a good seven months now on my desktop and fiddling about with my laptop so I can use it here.

I get a PnP bios message before Ubuntu starts saying to reboot with PnP disabled. 
My battery information does not show.
Wifi does not show
Resolution wrong on login screen and boot (fixed boot)
Now I have to boot into an old kernel to post this message.

help me please :lolflag:

---

### Post by Snappo on 2008-12-14
I solved the kernel issue if anyone cares... but the other issues are still there. :KS

---

### Post by Snappo on 2008-12-14
I've been forced to boot windows as it will not boot with any USB device...

---

### Post by Snappo on 2008-12-15
bump :(

---

### Post by Snappo on 2008-12-16
bump

---

### Post by pataphysicianu on 2008-12-16
I'm guessing from your other posts you use a Packard Bell R1 series Easy Note (R1000-R1938 models), is this correct?

The Insyde Bios in these completely crap machines is extremely buggy

Is the atheros wireless internal, or a usb device you have plugged in?

If you have "acpi=off" as a boot option this will probably disable usb on this machine because of it's horribly irrevocably crappy bios. It's also possible the new kernel has hit some other buggy portion of this horribly bad bios.

Also, are you using Hardy or Intrepid?

---

### Post by Snappo on 2008-12-16
> **pataphysicianu said:**
> I'm guessing from your other posts you use a Packard Bell R1 series Easy Note (R1000-R1938 models), is this correct?

The Insyde Bios in these completely crap machines is extremely buggy

Is the atheros wireless internal, or a usb device you have plugged in?

If you have "acpi=off" as a boot option this will probably disable usb on this machine because of it's horribly irrevocably crappy bios. It's also possible the new kernel has hit some other buggy portion of this horribly bad bios.

Also, are you using Hardy or Intrepid?

woo a reply

I've never gotten the atheros wireless working so I use a usb, and I'm running Interpid.

Can I flash my bios with something else? that works. :lolflag:

---

### Post by pataphysicianu on 2008-12-16
> **Snappo said:**
> woo a reply

I've never gotten the atheros wireless working so I use a usb, and I'm running Interpid.

Can I flash my bios with something else? that works. :lolflag:

Unfortunately there is no good bios version for this machine, they are all buggy.

I'm assuming I was correct on guessing the model series, is that correct? could you tell me which model it is? thanks

Ok, knowing that atheros wireless you mentioned is indeed the internal one, some R1 series had atheros wireless some had no wireless at all, so I wasn't sure if you had one or not internally, that tells me more.

The internal Atheros will work if you have acpi=off as a boot option, but then your usb won't work, this is due to the buggy bios. 

Since your Atheros wireless wasn't working, I'm assuming maybe you don't have the acpi=off on boot, is this correct?

Are you running any boot option like noapic?

Also I'm assuming you solved the pnpbios fault by using the boot option pnpbios=off, is this correct?

---

### Post by Snappo on 2008-12-17
You seem to know more about my computer than I do. :lolflag:

It is indeed a r1005 (rather crappy) I'm going to try to boot with acpi and see if that helps. 

I've not even tried to disable anything, last time I done that my system wouldn't boot at all and I had to recover my files with the live CD, but I will backup and give it a try. :KS

---

### Post by Snappo on 2008-12-17
You seem to know more about my computer than I do. :lolflag:

It is indeed a r1005 (rather crappy) I'm going to try to boot with acpi=off and see if that helps. 

I've not even tried to disable anything, last time I done that my system wouldn't boot at all and I had to recover my files with the live CD, but I will backup and give it a try. :KS

---

### Post by Snappo on 2008-12-17
No luck with that, it wouldn't let me take a screenshot showing that the wireless is not showing in the network manager so this is the best I could get.

---

### Post by Snappo on 2008-12-18
Still no resolution. :(

---

### Post by Snappo on 2008-12-19
bump..

---

### Post by Snappo on 2008-12-24
bump

---

