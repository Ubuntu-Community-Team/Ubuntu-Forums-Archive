---
title: "USB optical mouse remains lit after shutdown"
date: 2010-02-06
forum: Hardware
---

### Post by el_manaba on 2010-02-06
I've been using Linux live CDs (I've tried dozens) for 4+ years, but this is the first time I've actually installed Linux on my home PC.  I'm running Ubuntu 9.10 (32 bit) and dual booting with WinXP.

My Logitech M-UR69 optical USB mouse stays on (the red light is on) after the system shuts down through Ubuntu.  I've noticed the same thing with all other live Linux CDs I've used with this system.  The problem does NOT occur when I shut the system down from WinXP, DOS, or BIOS setup.  The motherboard is an ASUS A7N8X-Deluxe with the latest BIOS revision, and both the mouse and the motherboard are 5+ years old.

Any ideas on what could cause this?  I've read several similar threads, but haven't found a solution.

---

### Post by efflandt on 2010-02-06
Are you sure that it is totally shutting down (power light off), or is it possibly going into suspend (power light blinking?).

It is possible that something related to acpi or apic is allowing your system to appear to shutdown, but not completely.  For an old PIII 550 I had a similar issue where the computer appeared to shutdown, disk spun down, but power supply remained on, although, it was using a PS/2 mouse, so I did not notice if USB still had power.  I had to use **lapic** as additional kernel command line parameter for it to shut down completely.

If a fresh install (or if 9.04 to 9.10 upgrade was updated to grub2) kernel parameters would be set in /etc/default/grub (the GRUB_CMDLINE_LINUX_DEFAULT line for regular boot and GRUB_CMDLINE_LINUX for recovery boot).  Then **sudo update-grub**.

---

### Post by el_manaba on 2010-02-06
Thanks, efflandt.  So, are you saying I should modify /etc/default/grub to read: GRUB_CMDLINE_LINUX_DEFAULT=lapic ?
And yes, it is a fresh install.

---

### Post by tgalati4 on 2010-02-07
Check the BIOS.  Sometimes there is a switch:  "Allow USB devices to wake".  This keeps power to the USB bus--such as a keyboard or mouse, to allow wake from suspend.

---

### Post by el_manaba on 2010-02-09
As far as I can tell, the system is shutting down completely.  The only light that stays on is the mouse.

I checked the BIOS.  There isn't an option to wake on USB device, only PS/2.  The only thing related to the USB besides the controller (it's enabled) is "USB Legacy Mouse Support" - [Enabled].

I noticed another strange thing that may be related.  I set the Power Management Preferences to put the PC in sleep mode after 1 hr.  It does - the computer appears to be off except the blinking system status LED.  Even the mouse turns off in this mode!  When I turn the system back on, I get a black screen and and the keyboard and mouse light up.  But I get no response by pushing keyboard and mouse buttons (when I press Caps Lock, the corresponding LED on the keyboard doesn't light up).  I have to resort to a hard kill.

Could this be a BIOS setting?  If so, why doesn't the system exhibit the same problems when running WinXP?

---

### Post by el_manaba on 2010-05-23
Let's try and revive this...

I upgraded to 10.04 hoping that perhaps this bug had been addressed - it hasn't.  Any thoughts?

---

### Post by cokekid on 2010-06-05
I got the same problem on an asus mobo but also the #lock light stays on on the usb keyboard ive went through my bios and cant find any thing at all. now if i unplug the mouse and keyboard and plug it back in, after it is shutdown, the lights dont turn back on. winxp had the same problem with this system the same thing happened.

---

### Post by el_manaba on 2010-06-05
Cokekid, you say your system exhibits the same behavior when Windoze shuts down?  Strange - as I mentioned above, that's not true of mine.  It's definitely a Linux-only problem; it happens with Knoppix, Fedora, and all flavors of Ubuntu, but not WinXP.

Can any Linux gurus out there shed a little light?

---

### Post by Lunay on 2010-08-02
Try this way to solve this problem:
Go to BIOS -> Power Management Setup ->S3 KB Wake-Up Function(Or Meaning similar options), Select "Disable". 
Hope this helps!

---

### Post by Gaygerbil on 2010-08-02
Unplug your mouse. <__<

---

### Post by kircher on 2010-08-11
I have the same or similar problem.

When I shutdown from Windows 7, everything shuts down.

When I shutdown from Ubuntu 10.04, USB devices remain powered. I have a USB WiFi adapter, a USB hard-drive and USB wireless keyboard/mouse combo. The WiFi adapter has a blue light which remains on, and the USB powered external hard-drive remains spinning.

I have been ignoring this and accepting it, but I'm getting tired of having to unplug the USB hard drive when I shut down.

In the BIOS Power Management options I have all the wake-up features disable, and I have the standbye mode set to S3. I have tested S1 and the problem is the same.

I recently updated my BIOS, and the problem remains.

Is there any information on this? Everything I have found is a dead end.

My system:

Motherboard - Gigabyte MA785GPMT-UD2H
CPU - AMD Phenom II X4 945
RAM - OCZ 4GB DDR3 1333MHz
Video - NVIDIA 9800GT
Drives - 1TB SATA, 320GB IDE, DVDRW SATA

---

### Post by Nostigex on 2010-09-10
I think this is a bug.

---

### Post by v1ad on 2010-09-10
can't be a bug, i'm betting on the bios, unless linux is not shutting it down properly, but i doubt that.

---

### Post by Caiburn on 2010-11-14
Try using Sleep Mode instead of shutting down. This works for me - when shutting down the USB power stays on, when going into sleep mode the power goes off.

EDIT: Not working anymore with 2.6.32-26-generic ... :(

--Caiburn

---

### Post by jazzcica on 2011-02-18
I have the same problem (and have had it "forever") on my desktop computer (AMD Athlon 64 X2 Dual Core Processor 4800+). Probably in common with others, it's not just the optical mouse, it's all my USB devices. 

The same desktop computer shuts down all USB devices perfectly when running Windows XP SP3.

My ASUS EeePC shuts down all the USB devices perfectly well, both when running Ubuntu *AND* when running Windows (XP SP3). 

Fiddling about with the BIOS isn't really an acceptable solution.

---

