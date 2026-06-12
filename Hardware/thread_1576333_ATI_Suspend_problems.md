---
title: "ATI Suspend problems"
date: 2010-09-17
forum: Hardware
---

### Post by trippedn on 2010-09-17
Hi there!

Running 10.04 with an ATI HD3400 (fglrx / proprietary drivers) on a Toshiba Satelite m300 laptop. My primary issue is that laptop suspend does not work... sometimes.

On initial boot, suspend works. I can resume from suspend after that. With initial boot, suspend will work on battery, on AC, or while going to suspend and disconnecting AC.

After resuming from suspend, I can *usually* suspend again, but rarely can I suspend a 3rd or 4th time.

When a suspend fails, what occurs is that the screen turns black but it is still backlit. I cannot switch to any VT and the laptop is hardlocked.

What I would like to know is how to further diagnose suspend problems or maybe someone has a solution?

Thanks for your help!

---

### Post by trippedn on 2010-09-21
Hopeful bump (and subscribe)

---

### Post by giancarlo76 on 2010-09-24
The only way I found to make suspend work with my crappy ati xpress 200m is to disable KMS:
```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

```

For other info: [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")

Hope this helps!

---

### Post by trippedn on 2010-09-29
> **giancarlo76 said:**
> The only way I found to make suspend work with my crappy ati xpress 200m is to disable KMS:
```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

```

For other info: [https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting")

Hope this helps!

Hi!

Thanks for the suggestion but fglrx (in its current state) doesn't support KMS yet.

---

### Post by trippedn on 2010-09-29
Well I attempted fiddling with the BIOS settings to see if there was any thing in there that might help.

I tried different settings with the Sleep N' Charge crap. I also disabled the wake from sleep from keyboard and LAN.

Neither of these had an effect. I'll see if there is anything else I can do.

---

### Post by trippedn on 2010-09-29
ALT+SysReq+REISUB does not work either.

---

### Post by trippedn on 2010-11-07
> **trippedn said:**
> Hi there!

Running 10.04 with an ATI HD3400 (fglrx / proprietary drivers) on a Toshiba Satelite m300 laptop. My primary issue is that laptop suspend does not work... sometimes.

On initial boot, suspend works. I can resume from suspend after that. With initial boot, suspend will work on battery, on AC, or while going to suspend and disconnecting AC.

After resuming from suspend, I can *usually* suspend again, but rarely can I suspend a 3rd or 4th time.

When a suspend fails, what occurs is that the screen turns black but it is still backlit. I cannot switch to any VT and the laptop is hardlocked.

What I would like to know is how to further diagnose suspend problems or maybe someone has a solution?

Thanks for your help!

Discovered the problem and the fix!

I had a lot of messages about HPET in the kernel log. I tried disabling HPET and now I have suspend abilities all the time with no hanging!

To disable HPET on Ubuntu 10.04:

[LIST=1]
[*]Edit /etc/default/grub
[*]Find GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT and add "hpet=disable" to the list
[*]Execute: `sudo update-grub`
[/LIST]

Good luck!

---

