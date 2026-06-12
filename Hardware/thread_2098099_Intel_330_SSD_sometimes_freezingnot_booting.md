---
title: "Intel 330 SSD sometimes freezing/not booting"
date: 2012-12-25
forum: Hardware
---

### Post by JayWalker256 on 2012-12-25
Hey guys, I haven't had much luck searching for a solution so hopefully someone can help me.

I have a 240gb Intel 330 SSD and for the first few weeks all was well, but after a while I started getting occasional freezes and sometimes it wont boot at all. I'm running Ubuntu 12.04 64-bit, but I installed Linux Mint 14 along side and get the same problems. 

What's weird is that the GRUB boot selection menu always comes up, but sometimes after selecting an OS it will freeze a few seconds in to the boot process, and the HDD activity light will just stay on infinitely.

I tried booting into recovery mode (where it froze) and get this info, maybe it will be of some help:

[[IMG]http://www.imgjoe.com/thumbs/201212251324.jpg[/IMG]]("http://www.imgjoe.com/?v=201212251324.jpg")
If I try to go to my tty (with ctrl+alt+F2) and log in when the drive freezes after booting and using a while, I get this same message.

There's another message I get (same symptoms) when I boot regularly. I'll post that picture shortly if I can replicate it.

I don't know if it's a bug with the SSD (it is a sandforce controller) or if Ubuntu is trying to do something the SSD doesn't like....

My laptop is an HP DV6227CL. It's about 6 years old and only running a Sata 1 interface, but I doubt that has much to do with it.

---

### Post by Pjotr123 on 2012-12-25
Unsure if this helps, but if not, it won't hurt either:

- Make sure that your motherboard runs on the latest BIOS for it. HP has an updated BIOS available:
> 
BIOS (&#8207;1)
WinFlash for HP Notebook System BIOS (for Notebooks with AMD Processors) - Microsoft Windows/Vista-Based &#9658;
2010-04-06 , Version:F.43, 3.13M (&#8207;Previous versions available)
- Ensure that your SSD has the latest firmware:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18363](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=18363)

- Treat your SSD well in Ubuntu:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

In  particular: run a manual TRIM command on all Ubuntu partitions except the swap.

---

### Post by ahallubuntu on 2012-12-25
I have an Intel 330 SSD in a server running Ubuntu 12.04 LTS and it works just fine (it's been running 24/7 for several months now).  So it's clearly compatible with this version of Ubuntu.  I didn't have to do anything special to make it work.

I'd probably want to rule out hardware issues: test the RAM, make sure the CPU isn't overheating, etc.  You can also check the S.M.A.R.T. status of the SSD - using GSmartControl in Ubuntu or using the Parted Magic Linux CD.

---

### Post by oldfred on 2012-12-25
Do you have AHCI set in BIOS, or else you do have to run manual trim as suggested by Pjotr123.

I had not turned on trim (discard setting) in fstab and ran fstrim about a month after installing:
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed


       [https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)


test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by JayWalker256 on 2012-12-26
@Pjotr123: I'll install win7 on a spare partition when I can and update the bios to see if that helps. Will be a few days. My SSD does have the latest firmware and I've also recently run trim. Trimming did not fix either issue, but did speed some things up slightly.

@ahallubuntu: Ran memtest, did get some errors so I swapped ram and now errors are gone, but SSD still freezes and sometimes fails to boot. CPU isn't overheating, usually between 30-50 C. Nothing unusual. SMART reports no issues with the SSD. 

@oldfred: I have no options to configure the sata controller in bios. Discard option didn't change anything. Trim is available and enabled.

Here is a picture of the message I get sometimes when the SSD fails to boot:

[[IMG]http://www.imgjoe.com/thumbs/201212261627.jpg[/IMG]]("http://www.imgjoe.com/?v=201212261627.jpg")

I can usually just restart the machine and it boots, but these issues are still incredibly annoying. I will update my bios and test the SSD in my desktop to see if I can replicate the issue there when I go home in a few days.

---

### Post by JayWalker256 on 2012-12-26
Updated BIOS, still same problems.

---

