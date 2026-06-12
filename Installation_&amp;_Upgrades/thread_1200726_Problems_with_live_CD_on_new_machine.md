---
title: "Problems with live CD on new machine"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Richard Kimber on 2009-06-30
I have a new AMD Phenom 2 x4 on an Asus 4GB M4A78 Pro board. The
chipset is AMD 780G / SB700.  I Googled this before buying the machine
and found statements that people had run linux satisfactorily with
it, and I understood that Asus was OK.

When I try to boot the machine from the 9.04 CD I get the main Ubuntu
menu OK, but when I try to run the CD live, I just get a black screen
with a blinking underscore cursor at the top.  I think the kernel has started to load and gets as far as:

io scheduler cfg registered (default)

and then hangs (I found this out by running the Suse 11.0 CD in safe mode.  I assume the same is happening with the Ubuntu CD.)

I have tried the various options offered like safe graphics mode,
ACPI=off, noapic, nolapic, but they don't solve it.

Any suggestions as to what else I might try (e.g. BIOS settings).

The board has built-in graphics (ATI-based, I think).  Is it likely that
this might be a problem?  Might adding a pci graphics card be the
solution? Or might I need a proprietary driver?

One other peculiarity with my setup is that my HDs are running off a
pci disk controller, but that shouldn't stop the live CD from running,
should it?

Does anyone else have this M/B + processor hardware?

---

### Post by robotjohn on 2009-06-30
Hi Richard.

I have the same motherboard and that is part of the problem. Sadly it seems that latest kernels are not compatible with the wonderful M4A78 Pro. I believe it is something with the SB700. I found this [http://kerneltrap.org/mailarchive/git-commits-head/2008/6/14/2122314](http://kerneltrap.org/mailarchive/git-commits-head/2008/6/14/2122314) this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392) and this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389192](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389192) that all talk about a bug with SB700 and SB600 and the latest kernal causing the harddrives to stop responding. I get the same errors they have on the console when I try and fail to boot 9.04. 

As a tempory workaround I have found installing 8.10 and then upgradeing to 9.04 works. Just be sure to select the old kernel at boot up. If anyone knows more about this problem I would love to hear it. Hopefully this problem is fixed in future kernals.

Since you are using a pcie controler for your harddrives mabey if you disabled the onboard sata controler it might work. I think I might go dig out a pata harddrive and try that myself.

John Berube

---

### Post by Richard Kimber on 2009-06-30
Hi:  Thanks very much for the information.  I tried the 8.10 CD, but got a message saying that I needed to enable the IOMMU option in the bios, but I can't find this.  Is it called something else in the M4A78 bios?

---

### Post by robotjohn on 2009-07-01
[FONT=Verdana][SIZE=2][COLOR=Black]well I found out that the built in harddrive controler has nothing to due with us booting 9.04 but it is just the kernel doesn't do well with our motherboard.

As to IOMMU I see that you found a workaround but are getting only up to io scheduler cfg registered (default) again. This is just a guess but i think it might be your pcie harddrive controller[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Black]. i would suggest trying the built in controller cause i can boot 8.10 and that [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Black]pcie harddrive controller [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Black]is our major difference in system setup.

[/COLOR][/SIZE][/FONT]

---

