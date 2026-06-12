---
title: "Can't install ubuntu 9.04 please help"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by xTDee on 2009-07-18
Hi, I'm running ubuntu 9.04 on my desktop pc, never had any issues installing it or any other distro. I also have an old IBM thinkpad A20 laptop which was running windows 2000 I tried installing ubuntu 9.04 via live cd and it did not work but I was able to install debian. I don't much care for debian and would like to get ubuntu on here I recently tried the alternate install and now i can't even boot from a cd? What should I do? Can I get ubuntu using terminal or is there a way to install directly without using cd?

---

### Post by adamitj on 2009-07-18
What exactly means "it did not work"?

Did you saw any error messages? What's the computer behavior? Where is the problem itself?

---

### Post by xTDee on 2009-07-18
There were no error messages, when I would restart my computer it would not recognize my cd. So I assumed it was an error with the cd so I ordered one from canonical and it was the same. But it worked with my debian disk so I'm not sure why it wouldn't work with ubuntu. I never even get the screen with the ubuntu logo saying install or check for defects or recover.

---

### Post by adamitj on 2009-07-18
Wow... I never saw this before... but I have some assumptions for errors of this type:

1- Check out if you got an ISO or a CD for an architecture different from yours. I mean, check if you're not using a 64-bit version into a 32-bit only compatible processor;
2- Try another boot CD into your drive. As you said, you tried Debian disc and it worked, so I don't think it is a drive or media issue;
3- Disable temporally the APIC and ACPI modes in your BIOS setup, it any of these options are available. They should give you some issues with notebooks from HP, Toshiba and Acer (by my own expertise). Why not with an IBM?
4- This should be a joke, but I had some problems when trying to install Ubuntu 9.04 in a disc drive with too many partitions and when they are re-created many-many times (something like 20 resize, remove and create partition operations). This allowed to MS Windows Vista to run perfectly, but I was unable to install Ubuntu until I booted with an MS Windows Vista install disc and dropped all existent partitions.

NOTE: Please check out the items above in order of appearance, and be sure to maintain a backup of all your important data before work with partition operations.

---

### Post by anthos_hero on 2009-07-18
It's a long shot, but try installing off a live flash drive (eg, using unetbootin).

---

### Post by xTDee on 2009-07-19
Okay I checked my cd it's the correct version for my laptop and I tried my debian disk again and it's not booting that disk either. It's showing it as a mounted volume on my desktop but when I reboot it doesn't boot it even when I specify to boot from the cd r drive. I don't remember my bios password and I've tried all the backdoor passwords I can find so I can't disable the ACPI and APIC modes. I don't think I should have too many partitions since Debian is the only operating system on the computer. I also tried unetbootin but my USB drives are too old there not the 2.0 I guess. Any other suggestions?

---

### Post by adamitj on 2009-07-20
Well... if your Debian disk don't work anymore, you might be facing some CD-ROM drive problem.

The easiest way to install Ubuntu from a USB flash drive is to boot in any other computer with Ubuntu 9.04 live CD, then point to menu "System", "Administration", "Create USB boot disk" (I don't remember if the menu name is exactly this since my installation is in Brazilian Portuguese, but is something very close to this).

Then you just need to point to the CD-ROM or another Ubuntu ISO file and plug a USB flash drive with at least 800 MB free before start the process. After all, reboot the computer with pendrive plugged in, and if your computer boots from USB the grub menu from CD will appear.

If you want to remove BIOS password, you need to open the notebook case (unscrewing from bottom side) and search for a battery. Once you found it, remove it temporally and turn the computer on. Then turn it off and put the battery on the same place, the same way.

I should advise you that this action can end with your product warranty. The best option is to ask some hardware specialist to do it.

After all... I think the USB option from live CD is the better choice for you. Try it first.

---

