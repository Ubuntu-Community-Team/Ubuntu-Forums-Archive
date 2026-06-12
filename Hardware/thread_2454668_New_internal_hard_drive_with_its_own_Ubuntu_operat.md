---
title: "New internal hard drive with its own Ubuntu operating system"
date: 2020-12-03
forum: Hardware
---

### Post by joe.ess on 2020-12-03
I have an existing internal hard drive with an Ubuntu operating system. I am about to install another, new internal hard drive with its own Ubuntu operating system. With my new internal hard drive to house the second Ubuntu installation and with each drive having its own bootloader, BIOS will determine which one of the two gets to run. (I know it seems a bit cumbersome).

I&#8217;m not sure I want a master-slave relationship between the two drives. It would be a bonus to be able to mount & unmount the other drive in the opposite operating system to transfer documents.

QUESTION: Don&#8217;t I want to set the internal hard drive jumper settings such that each drive is a stand-alone drive, idea being that it would hopefully let the BIOS make the decision as to which to load?                   
                   I believe the hard drive jumper settings choices are: "Master or single drive" OR "Drive is slave".

Any direction would be greatly appreciated.

---

### Post by Bashing-om on 2020-12-03
joe.ess; Hello - Welcome to the forum.

I too multi-boot on multi-drives.
My solution is the enable booting in bios for any drive ( grub installed to the MBR of each drive) and to disable "30_os-prober" in the secondary systems. Then I can boot any system from the primary grub boot menu, and the secondary systems do not update to the primary and cause any conflicts. From bios selection to boot any of the secondary systems.

In your secondary system, if you choose this solution:
```

sudo chmod -x /etc/grub.d/30_os-prober

```
and update-grub to propagate the change: Secondary first and then the primary.
```

sudo update-grub

```

now member cavsfan has a handy dandy tutorial on enhancing and controlling the grub boot:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
That you will find of interest.

[INDENT][INDENT]many paths
[INDENT][INDENT]to one end
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tea for one on 2020-12-04
> **joe.ess said:**
> I have an existing internal hard drive with an Ubuntu operating system. I am about to install another, new internal hard drive with its own Ubuntu operating system. With my new internal hard drive to house the second Ubuntu installation and with each drive having its own bootloader, BIOS will determine which one of the two gets to run. (I know it seems a bit cumbersome).

When you mention BIOS, I hope that you mean **UEFI**? There are many distinct advantages with UEFI and [COLOR="#0000FF"]CelticWarrior[/COLOR] added some nice detail in post 4 of this thread:-

[https://ubuntuforums.org/showthread.php?t=2454615](https://ubuntuforums.org/showthread.php?t=2454615)

Check that you are in UEFI mode (either as installed or live session):-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"

```
Separate OS on each drive is perfect
Boot each system independently via UEFI boot screen is ideal (not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have EFI partition
Each drive should have grub
Ensure that you have different UUIDs for each OS
De-activate, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

Sharing the data is then very easy via your File manager

---

### Post by joe.ess on 2020-12-04
tea for one -

I forgot to mention...

Though both drives have their own, ordinary GRUB, what if I don't have UEFI BIOS?

---

### Post by tea for one on 2020-12-04
> what if I don't have UEFI BIOS?

Are you unsure about the firmware on your PC?

I haven't used Legacy BIOS for a long time but post 2 contains the information required.

> Though both drives have their own, ordinary GRUB

It sounds like you have already installed an OS on each drive, is that correct?

---

### Post by oldfred on 2020-12-04
You also mention jumpers on drives?
That was over 15 years ago or more before BIOS had cable select. Back then I had trouble seeing the little jumper pins. You then used the newer 80 conductor cable for cable select and BIOS controlled which drive booted. And you still used the jumper pins to change to cable select.  Did I mention I really hated those little jumper pins. 

I hated those old PATA drives and converted to SATA drives in 2006 when they became just a few dollars more than PATA drives.

With SATA UEFI/BIOS controls boot order and configuration.
All systems since about 2012 are UEFI as Microsoft required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives when Windows 8 was released. Even Windows 7 installer was updated to allow UEFI installs, but most Windows 7 installs were BIOS with MBR (msdos) partitioning.

---

### Post by joe.ess on 2020-12-04
Thank you kindly for the responses.

oldfred - I checked and this computer was purchased Sept. 2012 and definitely was legacy BIOS, no UEFI. UEFI is not an option.

I should also mention that the Seagate drive will not arrive here for another week or two, so no operating system was installed yet - This is in the planning.

It appears I was in error about jumper pins. I don't think this has jumpers.

tea for one - are you saying that post 2 by Bashing-om about DISABLING "30_os-prober" is the required info?

(If that's the case, I will have to get a little clarification so that I'm more comfortable that I know what I'm doing).

---

### Post by tea for one on 2020-12-04
> **joe.ess said:**
> tea for one - are you saying that post 2 by Bashing-om about DISABLING "30_os-prober" is the required info?

No, it's not required unless, as [COLOR="#0000FF"]Bashing-om[/COLOR] states, you want one OS to be your **primary **OS which consistently controls grub.

If I remember correctly, in older Legacy/BIOS systems, the last installed OS will control grub.

Lastly, there is a fair chance that your PC purchased in 2012 (assuming it was new at the time) is also UEFI.

What is the make/model of the PC?

---

### Post by joe.ess on 2020-12-04
Inspiron 660s from September 2012; right around the protocol cutoff.

I'd rather not mess with editing GRUBs if I don't have to, so if the newly-arriving drive's Ubuntu installation O.S. will control GRUB (Being the latest operating system), that would be a "not broke, so don't fix it" to me.

---

