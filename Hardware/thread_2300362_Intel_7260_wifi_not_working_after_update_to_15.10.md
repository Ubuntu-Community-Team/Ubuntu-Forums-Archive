---
title: "Intel 7260 wifi not working after update to 15.10"
date: 2015-10-25
forum: Hardware
---

### Post by Thomas_Costigliola on 2015-10-25
It looks like the firmware is failing to load. This is on a Dell m3800. I noticed some dell packages related to firmware loading were removed during the upgrade, e.g., dell-dup. Any idea how to get it working again?

```
tc@euclid:~$ dmesg | grep iwl
[    8.163016] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    8.179412] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[    8.180625] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
[    8.189908] iwlwifi 0000:06:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    8.211240] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.211319] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    8.211592] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[   12.428924] iwlwifi 0000:06:00.0: Failed to run INIT ucode: -110
[   12.428964] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled

```

---

### Post by perezw on 2015-10-27
Hi,

I have the same issue.
Looks like it is actually loading the firmware .13 ( as .14 and .15 are missing).
Check:
ls -l /lib/firmware/*7260*

To solve it, you can download the drivers from here:
[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)

Where for the 7260 and 15.10 (Kernel 4.2+) is this: 
[https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-15.227938.0.tgz)

Then, as the Readme.txt file points, you need to copy the file iwlwifi-7260-15.ucode to /lib/firmware
Example:
(from the extracted directory)
sudo cp iwlwifi-7260-15.ucode /lib/firmware/.

Now you should have the firmware available
check:
ls -l /lib/firmware/*7260*

So it will load the latest firmware on next boot.

Cheers,

---

### Post by Thomas_Costigliola on 2015-10-28
Thanks, that worked. Although with .15 it seems like there are random failures. On some boots wifi comes up other times it doesn't. Have you had the same problem? .14 seems to be working for now.

---

### Post by ndeubert on 2015-11-02
I have the same laptop and the same problem after upgrading. Copying the .15 firmware in there fixed it for me. Thanks for posting. Is there just not a package for this file yet?

---

### Post by Thomas_Costigliola on 2015-11-03
Hi, ndeubert, are you experiencing random failures when rebooting? For me sometimes the firmware fails to load and I have to reboot again to get it to work.

---

### Post by ndeubert on 2015-11-03
Yes actually I am too. I guess I'll go back to .14 too

---

