---
title: "Jaunty installer doesn't see my SATA HDD"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by chrisinspace on 2009-04-26
The Jaunty installer does not see my SATA hard drive.  When I get to the step where the partition manager runs, it comes back with no results.  There is just a blank menu.  If I start over the my external drive connected, it picks that up right away.

I had this same problem when installing Intrepid on this computer, but I found a solution (see previous [thread]("http://ubuntuforums.org/showthread.php?t=1010118")).  

Basically, if I added the all_generic_ide string to the boot options, it picked the drive up with no problems.  This isn't working with the Jaunty installer.  I have tried changing the hard drive mode to RAID, disabling ACPI in the bios, and hitting F6 and disabling ACPI in the installer setup.  There are other combinations of motherboard settings I haven't tried yet and I will continue to experiment, but I was wondering if anyone could offer any advice.  It is an Asus A8V-X Socket 939 board.

---

### Post by chrisinspace on 2009-04-27
I could really use some help with this issue.  Has anyone had similar problems?

---

### Post by chrisinspace on 2009-04-27
](*,) I don't mean to keep bumping my own thread (ok...yes, I do), but I'm getting really frustrated.  I have tried all of the F6 options (acpi=off, noapic, nolapic, edd=on) together, alone, and in combinations.  I have tried turning off ACPI 2.0 support, disabling ACPI APIC support, and changing the SATA IDE controller mode from 'SATA' to 'RAID' and to 'AHCI' in the BIOS settings.  I have updated the BIOS to the most recent version I can find on the Asus site.  Nothing has worked.  I have tried adding 'all-generic-ide' and 'all_generic_ide' as boot options.  

I'm out of ideas.  I don't know what else to try.  I've been all through the forums and searched through Google for hours.  I can't believe I'm the only one having this problem.  I'm just perplexed as to why the 'all_generic_ide' trick worked for Hardy and Intrepid, but now it doesn't.  :confused:

---

### Post by ronparent on 2009-04-28
Is your hard drive seen by intrepid? Do you intend to keep intrepid on the computer after installing jaunty?  If so, you could create a partition for jaunty while booted in intrepid, and then try to find it by selecting manual partitioning when offered your partitiong option during the jaunty install. Am I missing something here or what?

---

### Post by chrisinspace on 2009-04-28
> **ronparent said:**
> Is your hard drive seen by intrepid? Do you intend to keep intrepid on the computer after installing jaunty?  If so, you could create a partition for jaunty while booted in intrepid, and then try to find it by selecting manual partitioning when offered your partitiong option during the jaunty install. Am I missing something here or what?

Thank you so much for a reply.  I'm really at a loss here...

I have no plans to keep Intrepid.  I want to do a clean install of Jaunty on an ext4 partition.  

The problem is that the Jaunty installer doesn't see the hdd at all.  So, even if I create a partition in Intrepid, I don't think the Jaunty installer will see the disk and allow me to install there.  When I get to the partition manager in setup, it is totally blank and most of the options are greyed-out.  Do you know any tricks or work-arounds?

---

### Post by Jademalo on 2009-04-28
Hmm.. if you go into the setup, is your drive recognised? is your drive connected to the motherboard? and finally, try the GParted LiveCD. If it detects it on that, i cant help you, but your drive IS being recognised at least.. If it doesnt.. well i cant hep you either

---

### Post by chrisinspace on 2009-04-28
> **Jademalo said:**
> Hmm.. if you go into the setup, is your drive recognised? is your drive connected to the motherboard? and finally, try the GParted LiveCD. If it detects it on that, i cant help you, but your drive IS being recognised at least.. If it doesnt.. well i cant hep you either

I'll try gparted when I get home, but it is definitely detected in the BIOS setup menu.

---

### Post by dabl on 2009-04-28
Couple of suggestions:

1. In your computer's BIOS (aka "Setup") take a look at the SATA bus settings.  There are usually at least two -- "legacy IDE" and "AHCI".  Whichever it is set to, try the other one.

2. If you don't have Windows installed on that drive, then you can set the "boot" flag on the partition where you want to install Ubuntu.  You use GParted or Parted Magic to do that -- use a GParted Live CD or else make sure the drive is NOT mounted.  Some BIOS' seem to need to see that.

---

### Post by chrisinspace on 2009-04-28
> **dabl said:**
> Couple of suggestions:

1. In your computer's BIOS (aka "Setup") take a look at the SATA bus settings.  There are usually at least two -- "legacy IDE" and "AHCI".  Whichever it is set to, try the other one.

2. If you don't have Windows installed on that drive, then you can set the "boot" flag on the partition where you want to install Ubuntu.  You use GParted or Parted Magic to do that -- use a GParted Live CD or else make sure the drive is NOT mounted.  Some BIOS' seem to need to see that.

1. I have 'SATA', 'RAID', and 'AHCI' (and 'Disabled' but I think that would defeat the purpose).  I have tried all of the SATA bus settings with no success.  

2. Upon your and Jademalo's suggestion, downloading a Gparted Live .iso as I type this.

---

### Post by supererki on 2009-04-28
enable AHCI.
i had this problem with 8.04.

---

### Post by supererki on 2009-04-28
oh you tried and it didnt help. sry
try gparted as suggested by others...

---

### Post by magic976 on 2009-04-28
Just wanted to say that I was having the same problems last night.   I tried a few options also with no luck.  Will update my post with my specs when I get home.

---

### Post by shatterblast on 2009-04-28
Yes, AHCI is good for compatibility.  This has also been an issue with older versions of Windows when trying to install them onto SATA drives.  Also assuming the hard drive has already been formatted in some way, does the Ubuntu Live CD even recognize it?  You should be able to see it at least under:

Places -> Computer

You may have to match the hard drive size to determine if it's the correct one.

---

### Post by chrisinspace on 2009-04-29
Thanks to everyone for your advice.  I finally found the answer.  A user at LinuxQuestions.org pointed me in the right direction.  The solution can be found [here]("http://www.linuxquestions.org/questions/linux-desktop-74/installer-doesnt-see-my-sata-hdd-722259/").  I just had to add "pci=nomsi" (without quotes) to my boot parameters.

That's what I love about Linux.  I truly learn something almost every day.  Long live the community!

---

### Post by Lage on 2009-05-21
Okay, I really have no idea what pci=nomsi actually does, but it sure did help! I had the exact same problem as you, and almost exactly the same motherboard, an A8V-XE. It took me ages to find this thread, but I'm glad I did!

In fact, I triead a few different distributions' installer CD/DVDs (Ubuntu, Linux Mint, Sabayon, Mandriva) and the GParted live CD, but the only one that could find the attached hard drives was the Knoppix 5.1 Live CD!

So, many thanks! Let's just hope it will work after installation too! =)

---

### Post by chiefcrash on 2009-05-26
From the AHCI wikipedia page:

> 
[LIST]
[*]The AHCI controller does not work on AMD/ATI RS400-200, and RS480 [HBA]("http://en.wikipedia.org/wiki/Host_bus_adapter"); and Nvidia nForce 560 chipset when [MSI]("http://en.wikipedia.org/wiki/Message_Signaled_Interrupts") is enabled due to a hardware error. For AHCI to work, users must provide the "pci=nomsi" kernel boot parameter. With MSI disabled in this way, the PCIe bus can only act as a faster PCI bus with hotplug capabilities.
[*]The AHCI controller on AMD/ATI SB600 HBA can't do 64-bit DMA transfers. 64-bit addressing is optional in AHCI 1.1 and the chip claims it can do them, but, in reality, it can't so it is disabled. After that it will be forced to do 32-bit DMA transfers. Thus DMA transfers will occur in the lower 4 GB region of the memory, and bounce buffers must be used sometimes if there is more than 4 GB of RAM.
[*]**The VIA VT8251 South bridge suffers the same fate but it can be circumvented with the "pci=nomsi" option to force detection of the chip. This has been tested to work on 2.6.26, 2.6.24 and 2.6.20 [kernels]("http://en.wikipedia.org/wiki/Kernel_%28computing%29").**
[/LIST]
Now the AV8-X has a VT8251 southbridge, and AGP slots instead of PCIe.  So usually the pci=nomsi trick does the trick.  From the sounds of it, msi is a PCIe feature, and since the AV8-X lacks PCIe, i think this is where the problems start.  of course, that's just a SWAG...

However, i ran into random trouble with 8.10.  Using pci=nomsi, it'd install and run just fine.  It would see all my drives, everything worked, it was perfect.   But after a while, especially during heavy disk usage, the drives seem to disappear until reboot.  I eventually got frustrated and gave up trying to get it running on that box, but i'm getting ready to give 9.04 a try...

---

### Post by Lage on 2009-06-18
Oh, wow! In fact, the A8V-XE motherboard, which I have, *does* have PCIe instead of AGP. And my graphic card has an nVidia chip. That also explains another problem, namely why graphics are so terrifyingly slow on my machine, at least under Linux! The PCIe just acts as a PCI. Cool! Thanks for pointing that out!

---

### Post by Turkeyrider on 2009-10-21
Good news is: I'm into Ubuntu, know next to nothing about it, and want to get fluent. Bad news is: I'm into Ubuntu, know next to nothing about it, and want to get fluent PLUS I'm trying to install it on an inherited ASUS A8V-XE mobo-equipped PC. Talk about getting thrown into the deep end of the pool and told to swim to the edge as your first lesson... All I knew 4 days ago was create the CD, stick it in, and watch. Easier than Win XP. Now, after hours of searching, reading, learning new words and trying literally everything that's been suggested, I know this PC will remain a WIN XP SP3 machine. Nothing, and I mean nothing will get the live/install CD to get any clue as to the existence of 500 GBytes of SATA hard drive on the other side of the VIA VT8251 chipset. The mobo was free and I've picked up a lot Iwouldn't have if everything had been smooth as glass. But I just have to say that I'm amazed. This problem surfaced in 2006 and since then---right up to 9.04---the forums are still going round and round with pci=nomsi, AHCI vs. IDE, etc.  That's 3 years to get the right magic into the live CD.  The VT8251 doesn't "not work." Windows XP install can see that SATA hard drive with no human intervention no matter what BIOS settings I use.  I'll buy another mobo and still get into the fun. But I'll be real nervous. Are there ANY MORE chipsets I should know about before I pay real money for the next episode?  (Not rant; just a braindump. And yes... ! I DO feel much better now.)

---

### Post by donkyhotay on 2009-10-30
> **chrisinspace said:**
> Thanks to everyone for your advice.  I finally found the answer.  A user at LinuxQuestions.org pointed me in the right direction.  The solution can be found [here]("http://www.linuxquestions.org/questions/linux-desktop-74/installer-doesnt-see-my-sata-hdd-722259/").  I just had to add "pci=nomsi" (without quotes) to my boot parameters.

That's what I love about Linux.  I truly learn something almost every day.  Long live the community!

I had this problem with the official karmic installer (not the release candidate), first time it's ever happened to me and I've been installing ubuntu since dapper. Thanks for these posts and help.

---

