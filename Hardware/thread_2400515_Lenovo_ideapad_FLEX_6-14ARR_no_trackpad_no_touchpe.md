---
title: "Lenovo ideapad FLEX 6-14ARR no trackpad no touch/pen no wifi"
date: 2018-09-06
forum: Hardware
---

### Post by slimekat on 2018-09-06
I recently picked up the Lenovo Flex 14 (AMD) here in Canada. It's a 2 in 1 convertable.

Installing ubuntu was simple, but wifi refused to work. It seems to be hardblocked and blacklisting "ideapad_laptop" temporarily solves the issue. I say temporarily because it disables many features of the device, like its auto rotate and trackpad disable for tent mode.

I've found posts about other lenovo laptops from 2014, where users were able to compile their own "ideapad_laptop" module and solve their wifi issue without having to disable other features.

I'm not sure how to go down that road, and I also would love some help with my touchpad, touchscreen and pen issues.

---

### Post by jeremy31 on 2018-09-06
Post results for ```
sudo dmidecode | grep -i version; uname -a
```
I might be able to help with the ideapad-laptop issue

---

### Post by slimekat on 2018-09-06
> **jeremy31 said:**
> Post results for ```
sudo dmidecode | grep -i version; uname -a
```
I might be able to help with the ideapad-laptop issue

results:

    Version: 8MCN25WW
    Version: Lenovo ideapad FLEX 6-14ARR
    Version: SDK0J40709 WIN
    Version: Lenovo ideapad FLEX 6-14ARR
    Version: AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx  
    String: Compiler Version: VC 9.0
Linux pepper 4.18.6-041806-generic #201809050847 SMP Wed Sep 5 08:49:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jeremy31 on 2018-09-06
I guess I can't help as I don't use the 4.18.6 kernel.  Actually file a bug report against package linux, see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078) for some help.  You might also have to file a bug at kernel.org as this is not fixed even in the newest Linux kernel source code

---

### Post by slimekat on 2018-09-06
I had this problem with 4.15 as well, I was just testing 4.18, i can boot into that and post the results

EDIT 4.15 results:

    Version: 8MCN25WW
    Version: Lenovo ideapad FLEX 6-14ARR
    Version: SDK0J40709 WIN
    Version: Lenovo ideapad FLEX 6-14ARR
    Version: AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx  
    String: Compiler Version: VC 9.0
Linux pepper 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jeremy31 on 2018-09-06
4.15 will be the same, but I do have source code for it.
```
cd /lib/modules/4.15.0-33-generic/kernel/drivers/platform/x86
sudo wget https://www.dropbox.com/s/nxu7b0lyj02bv4n/ideapad-laptop.ko
```

Delete the blacklist on ideapad-laptop, reboot, check UEFI/BIOS settings, make sure Secure Boot is disabled.  I think it will work

---

### Post by slimekat on 2018-09-06
Okay, successfully 
transferred, removed blacklist, rebooted, SecureBoot is disabled, but it isn't working.

---

### Post by jeremy31 on 2018-09-06
Post results for ```
uname -a; rfkill list; mokutil --sb-state
```

---

### Post by slimekat on 2018-09-06
```

Linux pepper 4.15.0-33-generic #36-Ubuntu SMPWed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
0:ideapad_wlan: Wireless LAN
Soft Blocked: no
Hard Blocked: yes
1: ideapad_bluetooth: Bluetooth
Soft Blocked: yes
Hard Blocked: yes
3: phy0:Wireless LAN
Soft Blocked: no
Hard blocked: no
4. hci0 Bluetooth
Soft blocked: yes
Hard blocked: no
SecureBoot disabled

```

---

### Post by jeremy31 on 2018-09-06
I wonder, what about ```
sudo dmidecode | grep -i vendor
```

---

### Post by slimekat on 2018-09-06
```

Vendor: LENOVO
Vendor Syndrome: Unknown
Vendor Syndrome: Unknown
Vendor Syndrome: Unknown

```

This looks weird to me, let me know.

---

### Post by jeremy31 on 2018-09-06
I would file a bug report as this might be a new change that the old fix doesn't work for.  They have a quirks table in ideapad-laptop.c and I added 
```
		.ident = "Lenovo ideapad FLEX 6-14ARR",
		.matches = {
			DMI_MATCH(DMI_SYS_VENDOR, "LENOVO"),
			DMI_MATCH(DMI_PRODUCT_VERSION, "Lenovo ideapad FLEX 6-14ARR"),
		},
```

But it doesn't seem to work as it did in the past

---

### Post by slimekat on 2018-09-06
Okay, can you direct me towards how best to report this? Launchpad itself is pretty confusing

---

### Post by slimekat on 2018-09-07
I was wondering what the major differences that can be seen between

 [my model]("https://wiki.archlinux.org/index.php/Lenovo_IdeaPad_flex_6")

and [URL="https://wiki.archlinux.org/index.php/Lenovo_IdeaPad_720s_(Ryzen)"]this model

[/URL]I know its on the Arch wiki, but it's a great resource on laptop hardware. I picked up this device because of its similarities to the 720s Ryzen which runs well it looks like.

---

### Post by gloriouseggroll on 2018-09-07
Hi, because this is a newer Ryzen APU laptop, you might actually need a newer kernel than 4.15. I don't think full APU support was added until 4.17 if I'm not mistaken.

quick way to update to the latest mainline kernel:
```
sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install ukuu
sudo ukuu --install-latest
```

---

### Post by slimekat on 2018-09-07
I've also tried 4.18.6, using UKUU

---

### Post by gloriouseggroll on 2018-09-07
As previously mentioned, I'm assuming Secure Boot is turned off in the BIOS?

this post says that was the solution:
[https://askubuntu.com/questions/1065312/lenovo-flex-6-14-wifi-driver](https://askubuntu.com/questions/1065312/lenovo-flex-6-14-wifi-driver)

here's an answer that might help with secure boot:
[https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by slimekat on 2018-09-07
> **gloriouseggroll said:**
> As previously mentioned, I'm assuming Secure Boot is turned off in the BIOS?

this post says that was the solution:
[https://askubuntu.com/questions/1065312/lenovo-flex-6-14-wifi-driver](https://askubuntu.com/questions/1065312/lenovo-flex-6-14-wifi-driver)

here's an answer that might help with secure boot:
[https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

Secure Boot is disabled, but I also wonder about trying to run the OS in Legacy Mode instead of UEFI? I havent tried that yet.

---

### Post by gloriouseggroll on 2018-09-07
legacy or UEFI should not make any difference
what's the output of this:

lspci -knn | grep Net -A2

---

### Post by jeremy31 on 2018-09-07
Can you post results for ```
cat /sys/class/dmi/id/product_version
```
Just to double check

---

### Post by slimekat on 2018-09-07
I'll post both of those once I am home and have access to the device

---

### Post by slimekat on 2018-09-07
> **jeremy31 said:**
> Can you post results for ```
cat /sys/class/dmi/id/product_version
```
Just to double check

Lenovo ideapad FLEX 6-14ARR

---

### Post by slimekat on 2018-09-07
> **gloriouseggroll said:**
> legacy or UEFI should not make any difference
what's the output of this:

lspci -knn | grep Net -A2

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
    Subsystem: Lenovo Device [17aa:b023]
    Kernel driver in use: r8822be

---

