---
title: "Acer 5315 will not boot past splash unless AC power is plugged in."
date: 2008-10-02
forum: Hardware
---

### Post by madnev on 2008-10-02
No clue.  Ubuntu 8.04. Will POST and boot to the Ubuntu "knight rider" left to right, right to left loading bar etc but when the left to right progress bar comes up - it freezes, the CAPS LOCK light flashes and it has to be hard reset.  

Absolutely no issues when on AC power.  No issues when running battery power after boot.  

Kind of defeats the purpose of a laptop if you can't start on battery power.  Even more annoying since we lost power here due to Hurricane Ike.

---

### Post by nixscripter on 2008-10-03
Boot up again, except hit Cntl-Alt-F1 and see what messages come up. There will be a lot of them, but does anything stick out?

---

### Post by madnev on 2008-10-03
Thanks cool - didn't know you could do that.  Only thing that stood out was "on battery power - skipping file check" - before the kernel panic attached.

EIP ieee80211_unref_node_debug 

followed by kernel panic - not syncing: fatal exception in interupt.

Screen capture attached.

---

### Post by nixscripter on 2008-10-04
The output above is looks like a bad kernel oops, caused module misbehavior.

Just looking at it, I noticed ACPI was in there. Try to see if you can get a temporary workaround to boot without ACPI.

1. Boot the machine.
2. It should say something like "GRUB booting stage 2...2 seconds...1 second..." Hit escape before it boots.
3. You should get a list of boot options, and the first one should be selected. Hit 'e' to edit it.
4. There should be a line that says something like "kernel vmlinuz ..." with a lot of stuff on it. Select that and hit 'e' again.
5. Go to the end of the line, and type **acpi=off**. Hit enter. That should have been appended to the line mentioned in step 4.
6. Hit 'b' to boot.

Does that work?

---

### Post by madnev on 2008-10-05
Yes that workaround certainly nailed it.  So what am I missing without acpi and why would it be behave differently on battery power?

Thank you for taking the time to look at this.

---

### Post by nixscripter on 2008-10-05
In short, ACPI is a power management standard ([_Wikipedia provides a longer version_]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface")). It's somewhat important for a laptop, because it manages things like power consumption, going to sleep, waking up, and a full power off. You can live without it, but your battery life might suffer, and there is a risk that a sudden power loss might have more consequences (because the system can't warn you or take preventative measures to protect data first).

This probably is why your problem relates to the power being plugged in; some software is doing something weird, because ACPI sent it an interrupt at the wrong time. The actual place the panic occured appeared to be in the wireless driver, but that might just be a luck of the draw. This could relate to your battery.

Now that we've solved the immediate problem, time to do a bit more isolation. Charge up the battery so you can run without A/C power. Then boot up on A/C power **without the workaround.** After you boot, and get to a running system, go to the console (same Cntl-Alt-F1), and yank out the A/C power. Does it panic and dump a similar message? If not, this problem is probably something in the way that ACPI and other drivers load.

---

### Post by madnev on 2008-10-05
Thanks.  Now you have shown me where to look, I did a little more digging on ACPI.  I am getting cpufreq and ACPI errors on the CPU.  I also cannot enable speedstep or any other scaling program, and this is with ACPI running.

From doing some more digging, conclude that the bios could use an update, but discover that Acer packages the bios and flash utility as a *true* windows executable.  Bugger.  Will not work in WINE either.  I think I am at a dead end.
> 

Oct  5 09:13:02 suzy-laptop kernel: [  124.431446] APIC error on CPU0: 40(40)
Oct  5 09:13:05 suzy-laptop kernel: [  126.378162] APIC error on CPU0: 40(40)
Oct  5 09:13:08 suzy-laptop kernel: [  128.591454] APIC error on CPU0: 40(40)

Oct  5 09:12:56 suzy-laptop powersaved: Loading speedstep_centrino
Oct  5 09:12:56 suzy-laptop powersaved: enter 'speedstep_centrino' into CPUFREQD_MODULE in /etc/powersave/cpufreq.
Oct  5 09:12:56 suzy-laptop powersaved: this will speed up starting powersaved and avoid unnecessary warnings in syslog.
Oct  5 09:12:56 suzy-laptop powersaved: Cannot load cpufreq governors - No cpufreq driver available
Oct  5 09:12:56 suzy-laptop powersaved: Starting powersaved with ACPI support


---

### Post by madnev on 2008-10-05
Thought so......

So there is no way to update the BIOS of this computer outside a windows environment?  Despite several warnings and issues with using the windows environment to flash.  Buyer beware.


> Thank you for contacting Acer America. I apologize for the inconvenience that you have experienced. It is your choice to remove the Acer OEM operating system if you prefer however Acer's support is for the shipping OEM only. We have not tested non-Acer OEM or retail versions of Windows. Some drivers may be missing after the installation of a non-Acer OEM operating system. If this occurs, you may be able to locate the needed drivers by going to [http://www.acerpanam.com](http://www.acerpanam.com) under Drivers & Downloads. From here, search for your model of computer. If the drivers you need are not provided there, or those offered do not resolve the problem, we do not have others available. I'm sorry but I am unable to assist you further with this matter.


Respectfully,
Acer America 
Online Technical Support

Customer () - 10/05/2008 03:09 PM    
I would like to update my BIOS on a 5315.  I removed Windows Vista as it was unsatisfactory and am running Ubuntu.  The BIOS flash update on your website is a Windows program.  How can I update the BIOS in a non-Windows OS?


Question Reference #081005-000240
---------------------------------------------------------------
      Product Level 1: Notebook
      Product Level 2: Aspire
      Product Level 3: Aspire 5315
        Date Created: 10/05/2008 03:09 PM
        Last Updated: 10/05/2008 03:38 PM
              Status: Solved
      Date Purchased: 09/10/2007
    Operating System: Other

Serial Number
---------------------------------------------------------------

---

### Post by nixscripter on 2008-10-05
I don't know if it's the BIOS that's the problem. I think this is more about software drivers that are loaded later. In general, I would simply say that flashing a BIOS is almost always a windows OEM operation.

The second set of messages from powersaved might have been caused by not loading the driver, but let's stick to the original problem for a moment.

First, did you try pulling out the power after boot as I suggested? I suspect that won't cause the problem, but I just want to check.

If it doesn't cause the problem, similar to how I told you to put **acpi=off** on the GRUB command line, try booting without power plugged in and this time add **acpi=noirq**. If it doesn't panic, I believe this would be a reasonable fix to the problem, and I will tell you how to make it permanent.

---

### Post by madnev on 2008-10-05
Confirm no panic when system booted fully and power removed, after pressing CTRL+ALT+F1. (how do you get back to desktop?)

If power cord is pulled from rear of laptop at any other random time during boot, panic occurs.

When acpi=noirq appended, system loops trying to identify device on ATA4 (CD-ROM).  This occurs on AC and battery power. (Screen shot attached).

---

### Post by madnev on 2008-10-05
Update - now it also loops as above with ACPI=off appended. Hmmmmm?  Once again - no clue.

---

### Post by nixscripter on 2008-10-06
Back to the desktop is usually Alt-F7. Otherwise its Alt-F8, Alt-F9, or Alt-F10, depending on which virtual screen X windows gets started on.

Here we go deeper into kernel parameter heck. ;-)

For the moment, I'm going to assume that **acpi=noirq** would work were it not for this new problem. I'm wondering if whatever you did to try and flash the BIOS under wine might have "sort of" worked.

Try adding **all_ide_generic** to the command line options.

---

### Post by madnev on 2008-10-06
I tried all_ide_generic with no AC = Kernel panic

all_ide_generic acpi=noirq = loop on ATA as before
acpi=noirq all_ide_generic  = loop on ATA as before

I was not sure if order placement matters.

I have also noticed that sometimes the keyboard does not work (no keystrokes responded to) after these efforts.  A reboot cures.  I also realized I was typing no acpi instead of acpi=off in some of the earlier attempts.  I have also loaded and unloaded various cpufreq programs with no success.

I do not think the BIOS update worked at all since the program is a windows executable that does not do anthing until you press start.  In Ubuntu/Wine it fails to load period.

Thanks for your help so far.  Do you think the cpufreq not loading is linked to the kernel panic issue - since this would show up when on battery?

---

### Post by nixscripter on 2008-10-06
Order of placement doesn't matter usually, unless two things conflict.

If I can get this thing booting, then we can get more diagnostic information. I have a feeling I am just digging us into a deeper hole, but let's press on. ;-)

This time try adding **hdd=none** to the parameters instead of **all_ide_generic**. Hopefully this will make the kernel not try to look at your CD-ROM drive (if I guess correctly about which device it is on the bus).

---

### Post by madnev on 2008-10-09
Sorry for the late reply - I have been away from the laptop.  I do appreciate the help and do not want to appear ungrateful.

*hdd=none* yields OK boot with AC power and kernel panic when on battery.

Fudge.

---

### Post by nixscripter on 2008-10-09
Good. That knocks out the CD-ROM drive -- temporarily, of course.

Was that with acpi=noirq?

---

### Post by madnev on 2008-10-09
Upon the addition of *acpi=noirq* we are back to the looping failure to ID ata4.  *hdd=none* seems to have no effect on this error.

**nixscripter** - my hunch is that the failure to load cpufreqd is the bogeyman here.

Hmmmm....strange it just booted on battery.....twice.....then the keyboard locked up (no lights).  The only thing I did this time was edit the GRUB line to remove *quiet splash*

On third attempt it got all the way to the funky music and then locked up, with CAPS light flashing.

On fourth attempt (still with GRUB edit pause - is this a timing thing?) I was able to boot to a stable OS.

On reboot from this phase, with no pauses and hitting CTRL+ALT+F1, result is ANOTHER GOOD BOOT!

I shut everything down (from the GUI)...on battery and...got a Kernel panic - not synching error again.

On cold reboot...on battery...good OS.  On shutdown from GUI..no issues.  

One more go (all of this is on battery power).  From fully shutdown machine...boot all the way to login, keyboard freezes on entering password.  No lights.

Only my great self control and respect for a $300 laptop from Walmart prevents it's ejection from the adjacent open window.


Given that the results are not reproducable, I may have given you a bum steer now and again. Still something is amiss.  Any other thoughts?

---

### Post by nixscripter on 2008-10-10
> **madnev said:**
> Upon the addition of *acpi=noirq* we are back to the looping failure to ID ata4.  *hdd=none* seems to have no effect on this error.

I guess it wasn't the right device after all.

> 
**nixscripter** - my hunch is that the failure to load cpufreqd is the bogeyman here. Maybe, but power management seemed to be more a focus, since ACPI disabling fixed it.

> 
Hmmmm....strange it just booted on battery.....twice.....then the keyboard locked up (no lights).  The only thing I did this time was edit the GRUB line to remove *quiet splash* Those two options just affect whether you get the splash screen and how many errors. 

> 
On third attempt it got all the way to the funky music and then locked up, with CAPS light flashing.
 The flashing CAPS lock indicates a kernel panic, I believe. It's just another form of that. What funky music?

> 
On fourth attempt (still with GRUB edit pause - is this a timing thing?) I was able to boot to a stable OS.

On reboot from this phase, with no pauses and hitting CTRL+ALT+F1, result is ANOTHER GOOD BOOT!

I shut everything down (from the GUI)...on battery and...got a Kernel panic - not synching error again.

On cold reboot...on battery...good OS.  On shutdown from GUI..no issues.  

One more go (all of this is on battery power).  From fully shutdown machine...boot all the way to login, keyboard freezes on entering password.  No lights.



If I remember correctly, you said something about this computer being physically damaged. This is now starting to sound more like a serious hardware problem. Something electrical might be causing all sorts of faults; ACPI might just be one of them.

I would really need to see the exact causes of all the panics, and see if there is any common pattern in the callback stack (i.e. what code was executing in the kernel at the time).

Unless you want to take this thing apart, I'm not sure what else I can suggest.

---

