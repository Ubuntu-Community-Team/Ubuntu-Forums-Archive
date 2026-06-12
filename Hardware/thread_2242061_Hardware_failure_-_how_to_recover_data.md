---
title: "Hardware failure - how to recover data"
date: 2014-08-30
forum: Hardware
---

### Post by marklovescoffee on 2014-08-30
Hi everyone,

Just tonight my laptop has encountered a serious problem and will not boot. I dual boot Windows and Ubuntu and neither works, so I figure it is a hardware issue. I could use a little help in figuring out what's causing the problem and how to fix it, or at least find a way to save my files.

Here's what I know so far, what I've attempted and what options might be available to fix it.

Tried booting both windows and Ubuntu. Windows gets a blue screen before getting to the login screen and restarts automatically, so I can't read the error. Ubuntu gets to the login screen, but shortly after the laptop just shuts down.

For the last weeks or so I've been getting a "battery has suffered a critical failure" warning at the BIOS. Tried removing it, makes no difference.

Also I know my power supply doesn't charge the laptop (gives it power but won't charge the battery). However, I doubt it's the problem because if I leave the computer on GRUB or the BIOS it won't shut down.

Tried running fsck and repairing the bootloader from Ubuntu recovery mode. Both crashed during the process. Fsck indicated my disks were clean before crashing.

I almost ran the windows recovery tools, but hesitated, thinking they would damage my Ubuntu partition or bootloader. Am I right fearing this or should this be safe to try?

Any idea what might have happened? I would love to save the computer until I go home in January, but if not, that's fine as long as I can back up my files. Is there any way I night be able to do this?

Also, I CAN boot into a command line from GRUB. Are there any commands I can run that might shed some light on what failed? I'd rather not unscrew the laptop unless I've backed up data and am pretty certain which part is faulty.

Any insight you can offer would help me tremendously. Thanks in advance for your help.

- Mark

---

### Post by weatherman2 on 2014-08-30
There could be a number of things going on here.  A failing hard drive is one possibility.  Therefore, you should stop trying to fix the computer and focus on recovering your data if you care about not losing it.

The easiest way to get data off a suspect computer is to remove the hard drive and attach it to another computer.  This is easy to do with a USB hard drive adapter or enclosure.  You simply connect the drive to another desktop or laptop via USB cable and it appears as an external hard drive there.  (Not sure how you would do this with a tablet or a phone - so use another laptop or desktop computer.)

You can buy a USB hard drive adapter or enclosure for $20 USD or less.  I have paid $5 USD for cheap 2.5" USB SATA hard drive enclosures in some cases.  If you have access to a desktop computer, you could use a SATA data cable and connect the drive internally (with power off) without using the USB route and not buying anything expensive.
 
The only trick usually is removing the hard drive from your laptop.  Sometimes this is easy, sometimes difficult, depending on the design of your laptop.  On the typical laptop, you remove a couple of screws from the bottom or side of the laptop to remove a panel, then pop out the drive, which may be attached to a mounting bracket.  Sometimes, removing a laptop hard drive is difficult if the drive is buried under the keyboard.   If you can find a service manual for your laptop, it should tell you exactly how to remove it.

Once you've made a copy of your data (it sounds like you have no recent backup?), then you can focus on trying to fix the problem.

---

### Post by Mark Phelps on 2014-08-30
First thing I would try is booting from Ubuntu install media and seeing if the the PC still crashes running from a DVD or USB stick.  My guess is that it will still run, indicating that the problem is most likely a seriously failing hard drive.  To recover Windows stuff from such a drive, you need another working PC (to which to connect the drive), you need to install Windows data recovery apps on the other PC, and use those to recover data.

---

### Post by weatherman2 on 2014-08-30
As for the possible problems your laptop may have: the battery message may or may not be relevant.  Laptop batteries can and do fail over time, and if this laptop is a few years old that may be normal and have nothing to do with your current problem.  I suppose if your laptop has some sort of charging or electrical problem it could be related.

The hard drive itself could be failing.  Removing it as I suggest above takes everything else out of the equation.  You could also try booting Linux via USB and checking the S.M.A.R.T. status of the drive and see if there have been any failures.  In Ubuntu, you can try smartctl (part of the "smartmontools" package you can install) or GSmartControl (gui interface to smartctl, which is terminal-based).  There are other Linux discs like Parted Magic.  I think there's still a free version of that floating around, the latest is not free to download any longer.   It has "Disk Health" (GSmartControl) built in, to check S.M.A.R.T.

Your laptop could also be experiencing some sort of electrical or charging problem as mentioned above.  If the charger can't charge the battery anymore and can't power the laptop adequately, then whenever the CPU needs to do any work, it could draw too much power and cause a failure - such as when you try to boot.

Or it could be a problem with the RAM.  If you have your Ubuntu boot USB or disc, start it and in the beginning, hit "Esc" and choose "Test Memory" (Memtest) from the menu and see if there are any red error lines after a few minutes.  RAM does go bad occasionally in computers, but it can still "kind of work" and let the computer start to boot but then fail soon after as you've described.

Or it could be an overheating problem.  Laptops have heat sinks that draw the heat off of the CPU and other internal chips (that can get hot), and a fan blows over the heat sink to keep it cool and blows out of the laptop.  The outlet the fan blows through can get clogged with dirt and dust over time - very common with laptops that are more than a few years old - and the laptop won't be able to cool properly and it can overheat and shut down in the worst cases.  The fan can also fail.  Excessive heat is bad for any electronics that weren't designed for it, and it can cause damage to the motherboard components over time.

Overheating isn't likely your issue unless the problem gets worse the longer the laptop has been on but works OK when you first turn it on.   But if it hasn't been cooling properly for a while, some components could have been damaged.

---

