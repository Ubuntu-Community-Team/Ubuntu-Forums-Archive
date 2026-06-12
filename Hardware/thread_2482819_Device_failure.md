---
title: "Device failure"
date: 2023-01-11
forum: Hardware
---

### Post by Phil Binner on 2023-01-11
An old machine went wrong while updating the XUbuntu software. At first I thought this was the cause so I went for a software reload, but there seems to be a hardware problem.  I don't know what other people think, But my experience is that two or more unrelated errors seem to happen regularly. 

I changed the hard drive and went for a clean install of XUbuntu 22.10.  It says:

error: invalid magic number
error: you need to load the kernel first.

It's possible I made an error setting up the boot disk, so I tried with an old Ubuntu 18.4.1 .  This got further,  getting to show the setup logo, but it then failed with the message:

[    0.104470] ACPI: \_SB_PC10.SBRG.ASOC: Device cannot be configured due to a frequency mismatch.

I tried 2 different hard drives, and I removed the memory sticks one at a time. No change.

Does that message give me a clue as to which device is failing.

Thanks in advance for your help.

---

### Post by TheFu on 2023-01-12
If you can boot into a "Try Ubuntu" flash drive environment, then you can run lots of information gathering tools and some system testing tools like smartctl and look at system temperatures provided but the "sensors" package.

If the same issue appears when booted from the flash drive, that means it isn't the SATA controller or cabling.  Could be the PSU or a tiny electrical fault hidden in the motherboard.

Just some other things to check out.

---

### Post by Phil Binner on 2023-01-17
Hi

Sorry if I appear to have been ignoring your help.  Extenuating circumstances I'm afraid.

I have finally managed to create a bootable USB, and while it does not show the same error, it still won't load.  What it does now is get to the text screen to request what to do first, and the top option is try or install xubuntu.  I select this and the screen goes black for a few seconds, then I get a message to press any key to continue.  Pressing a key just takes it back to the initial menu.  I suspect this is the same error, just without the error message.

Just occasionally, however, if I allow it to try to boot the updated software it succeeds, albeit in a manner that is temporary and not fully usable. Also, at any time I can get into the bios.

Is it possible that the software update will also have updated any of the Motherboard drivers.  The problem did start at the same time, though I know this is not conclusive.  The motherboard is an Asus Sabretooth X58, with an I7 processor.  I suspect all the firmware is still available from ASUS, though I would not know what to do with it.

I'm going to be away for a few days again now, so so If I do not respond immediately then please do not imagine I am ignoring you.  Your help is vastly appreciated.

Regards

Phil Binner

---

### Post by Phil Binner on 2023-01-21
I now have trial Ubuntu running from a flash drive.  The background screen is not right, just a bunch of interference lines, but the dock shows on the left and it responds.  What kind of tests can I perform now.

---

### Post by Phil Binner on 2023-01-21
I managed to get Ubuntu loaded onto a gash hard drive.  It is very slow and the video is distorted, but I'm fairly happy that the problem is in the video card. I just need to replace that and I suspect all will be well.

---

