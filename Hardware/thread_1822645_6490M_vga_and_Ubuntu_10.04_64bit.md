---
title: "6490M vga and Ubuntu 10.04 64bit"
date: 2011-08-10
forum: Hardware
---

### Post by Pigkappa on 2011-08-10
I have an ATI 6490M vga on my HP pavilion dv7 notebook. I've installed Ubuntu 10.04 64 bit on it.

I can't get it to work properly; I'm stuck with the 1024x768 resolution and found no driver automatically installed.

I downloaded some packages from the synaptic package manager and I can now see the "ATI Catalyst Control Center" button in the preferences, but I receive an error when I try to open it. It says that no ATI driver is installed, or an ATI driver is installed but it's not working and I need to configure it using the "anticonfig" (whatever it is). I can't quote the errore because it isn't in English.

Please help me :popcorn:.

---

### Post by Pigkappa on 2011-08-11
Can anybody help please? :(

---

### Post by mimima on 2011-08-30
In my case I use Ubuntu 11 and I have an ATI 6490M. I found that there's no way to use Ubuntu and ATI6490 in sandy bridge (maybe I' m wrong).  The integrated Intel video card is automatically installed by Ubuntu 11, but I can't use the proprietary driver from ATI (same error).

For the moment I don't install anymore the ATI driver (I had to remove it after I couldn't get any video). I use only the Intel which is good enough to run Unity. (++ the ATI is disabled)

++ eventually try this: GRUB_CMDLINE_LINUX_DEFAULT="text splash nomodeset i915.modeset=1 radeon.modeset=0"

---

