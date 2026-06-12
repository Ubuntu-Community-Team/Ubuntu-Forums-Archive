---
title: "Ubuntu 15.10 with GeForce 6150"
date: 2015-12-30
forum: Hardware
---

### Post by rrrobles on 2015-12-30
I've installed 15.10 on a machine with GeForce 6150. It runs fine with proprietary nvidia driver on 11.10, but on 15.10 the installation defaults to the noveau driver.

I want the proprietary driver because is a huge performance gain.

So what I did:

1 - Activated the proprietary driver via proprietary drivers window. The driver activates like expected. After reboot and login, I got a black screen with a mouse cursor.

2 - Reverted to nouveu driver.

3 - Manually installed the nvidia driver package. Got the same results as step 1

4 - Reverted to nouveu again.

What could I try next?

---

### Post by tokyobadger on 2015-12-30
1. Which version of nvidia-driver did you select? I believe 304.xx is the latest that will work on that chipset

2. Can you tell us more about the hardware? 6150 seems to be onboard / integrated rather than discrete card

3. How did you switch from 11.10 to 15.10? Clean install or upgrade existing install?

---

### Post by rrrobles on 2016-01-01
> **tokyobadger said:**
> 1. Which version of nvidia-driver did you select? I believe 304.xx is the latest that will work on that chipset

2. Can you tell us more about the hardware? 6150 seems to be onboard / integrated rather than discrete card

3. How did you switch from 11.10 to 15.10? Clean install or upgrade existing install?

1 - 304.131;

2 - Yes, it's onboard - 00:05.0 VGA compatible controller: NVIDIA Corporation C51PV [GeForce 6150] (rev a2) - Mainboard ASUS M2NPV-VM

3 - Install from DVD into 11.10 partition without formatting - I think it counts as a upgrade.

---

### Post by tokyobadger on 2016-01-01
Thanks for the information. First thing you'll need to do is clean out all previous installs of nvidia drivers. See [this thread](http://ubuntuforums.org/showthread.php?t=2307693) Post #7 and #3 in particular.

Remove the manually installed nvidia drivers first (post #7), then clean up as in post #3 (skip the PPA as you can get 304 from the regular repository), run nvidia-xconfig (may not be required but doesn't hurt), edit /etc/default/grub, update grub and reboot.

---

### Post by mikewhatever on 2016-01-02
Geforce 6150 is too ancient for Ubuntu + Unity. After all it's about 12 years old, so I suspect Gnome Shell, Cinnamon and Unity will all be too much for it. Try something like Xubuntu or Lubuntu instead.

---

### Post by tokyobadger on 2016-01-02
> **mikewhatever said:**
> Geforce 6150 is too ancient for Ubuntu + Unity. After all it's about 12 years old, so I suspect Gnome Shell, Cinnamon and Unity will all be too much for it. Try something like Xubuntu or Lubuntu instead.
That's a distinct possibility but I believe it's important to troubleshoot by process of elimination one factor at a time. OP does not currently have a "clean slate" so that would be the first step IMO.

OP's platform is AM2 which supports relatively recent CPUs and IIRC up to 8G RAM, so the second step would be to confirm what the hardware is and what amount of RAM can be reserved for the nvidia chipset in BIOS; admittedly even with 512M and I think the motherboard only allows 256M, OP would most likely benefit from a "lighter" WM/DE.

Let's first see what a clean install of the 304 drivers gives us

---

