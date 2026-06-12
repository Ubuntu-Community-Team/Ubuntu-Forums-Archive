---
title: "After Bios update, no linux will boot"
date: 2022-03-01
forum: Hardware
---

### Post by michael-vrobles on 2022-03-01
I am now leaning towards a hardware problem, any advise is appreciated..

Gigabyte Z590 Vision D
I9 11900K
3 Nvme SSD's - one Western Digital, one Sandisc, one Samsung
RTX 3090
TPM Enabled > this device doesn't have a TPM chip, so it's emulated
PTT Disabled/Enabled doesn't matter
Secure boot currently disabled but enabled doesn't matter
No sata discs, sata controller disabled, ethernet controller disabled


I've had ubuntu 20 working for a month or two now and I updated my bios, after the bios update ubuntu refuses to boot from the working install. Here's where it gets interesting...
**Live usb's don't work either!**

I have tried ubuntu 22, 21, 20, 18, linux mint, and endeaveros. Endeaveros did manage to load once, but never again after that. I can get to the boot menu, but when I try to load a kernel/image it freezes.

If I try to launch recovery mode it hangs at "loading initlal ramdisk"

Relevant details:

I had windows 11 installed on first and third ssd. First was a real install, third was a virtual install. The first will boot windows but gives an error about "security settings changed, please reset pin" but then requires a network connection and claims there's no connection, even when the connection manager shows connected. Windows on the third ssd is how I'm typing this, which is very strange as this ssd was passed through to qemu and the install done virtually.

Windows usb installer boots fine.

Here's all of the changes from the bios:

Update CPU microcode version 0x34

Add Intel Adaptive Boost Technology support for Core i9-11900K & Core i9-11900KF processors

Add DDR4 5000/5066/5133/5333MHz support

Change default status of Intel® Platform Trust Technology (Intel® PTT) to Enabled for addressing basic Windows 11 requirements ([https://support.microsoft.com/windows/1fd5a332-360d-4f46-a1e7-ae6b0c90645c](https://support.microsoft.com/windows/1fd5a332-360d-4f46-a1e7-ae6b0c90645c))

Major vulnerabilities updates, customers are strongly encouraged to update to this release at the earliest.
Credits to "Assaf Carlsbad and Itai Liba from SentinelOne"


Introduce capsule BIOS support starting this version.
Customers will NOT be able to reverse to previous BIOS version due to major vulnerabilities concerns.



Improve the compatibility of non-K CPU with CXMT / Unic memory

Due to the capsule bios thing, I don't believe I can downgrade my bios, though I haven't tried

---

### Post by TheFu on 2022-03-01
I don't know, but very often a BIOS update will completely wipe all the custom BIOS settings, so things don't work anymore. If you have a backup of the BIOS settings, restore those. Not all BIOSes support external backups of their settings, so you may need to work your way through again.  Off the top of my head, check that the UEFI vs. Legacy BIOS boot settings are correct.  If your system has an SSD, especially NVMe, you may need to update the firmware for that device to be compatible with the new BIOS.

Most BIOS systems don't support downgrading without a very strong risk of bricking the motherboard. Do that only if the manufacturer has clear instructions.

The fact that Ubuntu install ISOs aren't working, it very concerning. Do you have an nvidia GPU?

---

### Post by michael-vrobles on 2022-03-01
I have restored the bios settings, but it didn't work, so I tried toggling pretty much everything. My next step is to remove each nvme and see if a usb boots alone. It's just a huge pain to get to the ssd's on this motherboard as they're under a heatsink. Before, only UEFI was enabled, I'm certain of that because above 4g decoding only works with csm disabled. I may look into updating the firmware on the nvme(s) if the system boots with them removed.

I agree, my biggest !!! is the fact that no linux will work at all even when running live. Yes, nvidia rtx 3090 gpu, I have tried enabling the onboard graphics but it still didn't boot.

---

### Post by TheFu on 2022-03-01
Have you looked up the nvidia work-arounds and tried all of those? There are a bunch, as I recall. 3090 is pretty new and costs more than all 8 of my computers combined.

Also, that's a very new CPU. Is the kernel new enough to support it?  At least 5.11.x, perhaps even a newer version to get all the new stuff. I have Ryzens and don't keep up with Intel CPUs. For Ryzens with an integrated GPU, 5.10.x was required for the iGPU to work except in VESA mode. I think Intel doesn't have that level of dependency. I'm just throwing out guesses now.  I waited 3 yrs after the first Ryzen was released before I got one. I wanted all the issues to have been solved BEFORE. I was on the bleeding edge in the 1990s and never plan to do that again.

---

### Post by michael-vrobles on 2022-03-01
I did, recovery mode should work as it doesn't load any drivers, if you open up the grub config it has "nomodeset" which is the usual nvidia fix. It may be new, but it was working just fine before the new bios update.. and also, with the gpu unplugged, linux still doesn't boot.

Like I said, it ran just fine before the new bios, that's why I believe the issue to be something to do with a new option that linux doesn't understand yet that wasn't previously there. I believe I am using the newest kernel that comes with ubuntu 21, but also I tried to boot up jammy jellyfish which is 22 which should definitely have the newest kernel, and that won't boot either.

---

### Post by oldfred on 2022-03-01
Most newer UEFI have settings to turn off or disable drives. So you do not have to directly remove a NVMe drive.

Many SATA or NVMe SSDs need firmware update. Something in UEFI may then expect NVMe to have latest firmware.
My Samsung NVMe has a bootable ISO you download to update firmware. It only has one version.
You can check firmware versions - f/w rev, (if you can get into Ubuntu).

Do not look at Magican, just look at firmware and available ISO by model.
[https://semiconductor.samsung.com/consumer-storage/support/tools/](https://semiconductor.samsung.com/consumer-storage/support/tools/)

sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
sudo nvme list


```
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     S4P2NF0M514514L      Samsung SSD 970 EVO Plus 500GB           1         134.14  GB / 500.11  GB    512   B +  0 B   2B2QEXM7

```

---

### Post by michael-vrobles on 2022-03-01
I tried to boot with no nvme drive (removed all 3 drives) off of a usb disc and no dice. I get to the grub menu, try to launch recovery mode, and nothing.
Attempted both with internal graphics and gpu unplugged and with gpu plugged in.
I noticed windows fast boot was enabled so I disabled this (after reinstalling the drives) and it still refused to boot.
I tried with both secure boot on and off. With secure boot on, it hangs at "initial ramdisk... efi stub" and with secure boot off it just hangs at "initial ramdisk".

I am just astounded. Perhaps windows has lock on the pc and I can try reinstalling fresh and then try booting ubuntu. Like I mentioned, I'm using the windows virtual machine drive, as the original windows install wouldn't work.

---

### Post by oldfred on 2022-03-01
Are you booting with Safe Graphics & when installing choose to include proprietary drivers.
You have nVidia RTX 3090 which requires those settings at minimum.
If changing to Intel graphics, you may have another UEFI setting for which graphics to use. Check your manual.
Also check UEFI fast boot setting. That changes options on other settings as well. IGFX   setting
You may have other setting, my system is z170 so multiple generations older, but still has a lot of settings to review.         
 

---

### Post by michael-vrobles on 2022-03-01
> **oldfred said:**
> Are you booting with Safe Graphics & when installing choose to include proprietary drivers.
You have nVidia RTX 3090 which requires those settings at minimum.

 
It does not boot with safe graphics on live usb or recovery on my ssd install.

> **oldfred said:**
> 
If changing to Intel graphics, you may have another UEFI setting for which graphics to use. Check your manual.
Also check UEFI fast boot setting. That changes options on other settings as well. IGFX   setting
You may have other setting, my system is z170 so multiple generations older, but still has a lot of settings to review.         
 
Yes, my motherboard has 3 graphics options. Integrated graphics = "Auto", "Enabled", "Disabled". My original ubuntu install was "Disabled", and it booted from livecd and ssd just fine. After the most recent bios update, no change of Auto/Enabled/Disabled will allow any linux based operating system to boot.

I've also toggled the "Fast Boot" setting, and gone through the options there. The options are related to Sata/VGA/USB/Network/AC power loss checks.

---

### Post by Yellow Pasque on 2022-03-02
> **michael-vrobles said:**
> Here's all of the changes from the bios:
...
Add Intel Adaptive Boost Technology support for Core i9-11900K & Core i9-11900KF processors


Have you tried turning that off? Maybe Linux does not play well with it.

---

### Post by michael-vrobles on 2022-03-02
Indeed, I just tried. There's two settings:

Intel(R) Turbo Boost Technology
(Note)Allows you to determine whether to enable the Intel® CPU Turbo Boost technology. Auto lets the BIOSautomatically configure this setting. (Default: Auto)
Intel(R) Turbo Boost Max Technology 3.0 (Note)Enables or disables Intel® Turbo Boost Max Technology 3.0. Intel® Turbo Boost Max Technology 3.0 allowsthe system to identify the processor's best performance core and lets you manually direct the most criticalworkloads to it. You can even adjust the frequency of each core individually for performance optimization.(Default: Enabled)

I already had the second option set to disabled as I thought it may be an issue, I changed the first option from "auto" to "disabled" and no difference. Ubuntu does not boot from usb or ssd install, either in regular or safe graphics or recovery mode.

I've opened up a ticket with gigabyte.

---

### Post by oldfred on 2022-03-02
I might try 22.04 even though not yet released.
I keep 20.04 as main working install, but have another / partition with 22.04 and with my system it works.
Since it has newer kernel & drivers, it may work.
You still have nVidia and have to use Safe Boot or nomodeset. Or try without nVidia and just Intel video.

---

### Post by michael-vrobles on 2022-03-03
After pulling out 2/3 drives, and reinstalling windows, and disabling onboard graphics, I managed to boot ubuntu.. ONCE. After rebooting windows it wouldn't do it again. This leads me to believe there's an issue with secure boot, graphics, and my ssd's. What a perfect storm.

I've been trying to reset the secure boot keys in my bios, a few times, just playing with the settings.

---

### Post by oldfred on 2022-03-03
If Windows did an update, it may have reset some things.
It often turns fast start up back on.
And Windows may run an UEFI update which resets some UEFI settings.

Can you boot directly from UEFI boot menu? And get grub menu and try recovery mode?

---

### Post by michael-vrobles on 2022-03-03
Yes I can, I can load up grub just fine, it's something between grub and ubuntu. Or grub and fedora. Or grub and arch..

I can't even install windows 10, windows 11 will though.

---

### Post by oldfred on 2022-03-03
If after grub menu, then most often video drive, but could be other driver issue.
With nVidia you need Safe Boot. Of if you did not install nVidia driver, you need nomodeset or the recovery mode (which has nomodeset) to boot to command line or low quality graphics, so you can install nVidia driver. Some very new Intel chips with video may need boot parameters, if not using nVidia.

Remove quiet splash so you can see boot process, that often tells where it stops (but often several lines above where it stops posting).
Use e at grub menu and on linux line delete quiet splash and add nomodeset.

---

### Post by oldfred on 2022-03-03
I do not have link to the older tests.
Comparison of newer Intel chips with ASUS STRIX Z690-E GAMING WIFI motherboard.
[https://www.phoronix.com/scan.php?page=article&item=uhd-graphics-770&num=1](https://www.phoronix.com/scan.php?page=article&item=uhd-graphics-770&num=1)
Not sure how similar this Gigabyte board is:
[https://openbenchmarking.org/result/2110257-TJ-I511600KS29](https://openbenchmarking.org/result/2110257-TJ-I511600KS29)

---

### Post by michael-vrobles on 2022-03-03
That is an interesting read, the second link is very similar to my build. It seems they are using their own compiled kernel, with the microcode set to 0x40. When I look at my bios updates, it only lists microcode 0x34. Either way, I've spent 5 hours today, combined with over 20 other hours trying to reset secure boot keys, disable it, switch to onboard graphics, use one ssd, use a different one, I've toggled every bios setting in any combination I can think of, done hours of research on how to get this to work. Frankly I'm over it and just going to wait for gigabyte to respond to my ticket. This has to be some sort of bios issue as nothing is repeatable.

---

### Post by Doug S on 2022-03-04
Earlier on this thread:

> **michael-vrobles said:**
> Introduce capsule BIOS support starting this version.
Customers will NOT be able to reverse to previous BIOS version due to major vulnerabilities concerns.


That a user can not go back to the previous BIOS goes against the most basic rule of systems design. Always provide the ability to back out of a change, if for no other reason than to verify the source of the problem.

I had what turned out to be a BIOS problem recently (much less severe than yours), [and couldn't go back to an earlier version either.]("https://lore.kernel.org/linux-pm/1b2be990d5c31f62d9ce33aa2eb2530708d5607a.camel@linux.intel.com/") With language issues and such it took extraordinary effort just to get ASUS to even agree there was an issue. Half a year later, and I am still on a test version of BIOS they gave me.

Hope you get sorted out.

---

### Post by michael-vrobles on 2022-03-04
> **Doug S said:**
> Earlier on this thread:



That a user can not go back to the previous BIOS goes against the most basic rule of systems design. Always provide the ability to back out of a change, if for no other reason than to verify the source of the problem.

I had what turned out to be a BIOS problem recently (much less severe than yours), [and couldn't go back to an earlier version either.]("https://lore.kernel.org/linux-pm/1b2be990d5c31f62d9ce33aa2eb2530708d5607a.camel@linux.intel.com/") With language issues and such it took extraordinary effort just to get ASUS to even agree there was an issue. Half a year later, and I am still on a test version of BIOS they gave me.

Hope you get sorted out.

After contacting gigabyte support, I was actually able to downgrade, and guess what, UBUNTU BOOTS! With all of the default settings. They said go to hell on any linux support though. I am going to flash the bios's one by one to see which is the problem.

Update: Everything up until the most recent bios boots, go figure. I told them they should look into what changed and fix it. The bios changelog lists "[COLOR=#434343][FONT=inherit]Improve the compatibility of non-K CPU with CXMT / Unic memory"

Interesting enough, I have a K cpu, so this shouldn't even affect me[/FONT][/COLOR]

---

### Post by Al_Capino on 2022-06-28
I'm also using a Gigabyte Z590 Vision D, but mine is running an Intel Core i9 11900T.
After upgrading to the F8b firmware I was not able to run Unraid anymore. (I know, its not Ubuntu)

After flashing it back to F7, the system would boot back up without any problem.
I think there is some kind of problem in the Bios.

---

### Post by Thiago Camargo on 2023-02-26
Hello,

I'm experiencing the same issue with my Gigabyte Vision D Z590 and 11th Gen CPU if using BIOS version +F7. Ubuntu (20.04) runs fine with F6. However, when I upgrade to BIOS F7 or F8, Ubuntu fails to boot (including Live CD), and this problem persists even after resetting all settings to default. I've tried other Linux distributions, including Ubuntu 22.04 (Linux 5.15), but they all fail to boot. I've noticed some strange messages on `dmesg` during normal operations (even idle) with F6.

I've contacted Gigabyte for support, and they advised me to downgrade back to F6. However, this involves disassembling the hardware and leaving only the CPU (and RAM, if necessary), removing all other components, and connecting a flash drive with the firmware using a specific file name and port. It's frustrating that the Vision D firmware is so challenging to work with, despite the motherboard having an excellent PCI-e layout that can easily accommodate up to 3 GPUs.

Another issue with Vision D is its problematic RAM profiles, which only seem to work with 2 GPUs. That's why I tried to upgrade the BIOS, but everything fell apart.

I'll try again with Ubuntu 22.04 and Linux 5.19 (already available) to see if it works with latest firmware, fast RAM profile, and 3 GPUs.

I'm down to open more issues on Gigabyte, until they fix this. Perhaps we should open the same issue over and over again! lol

Worth mentioning that the RAM I'm using is not listed on their document: [https://download.gigabyte.com/FileList/Memory/mb_memory_z590-vision-d.pdf?v=966b56e96e47b03c8504ad4b385d58e8](https://download.gigabyte.com/FileList/Memory/mb_memory_z590-vision-d.pdf?v=966b56e96e47b03c8504ad4b385d58e8) - Which I'll replace and test again.

---

### Post by Thiago Camargo on 2023-03-25
It works now! I upgraded mine to F8f, Ubuntu 22.04.2 with Linux 5.19.

---

