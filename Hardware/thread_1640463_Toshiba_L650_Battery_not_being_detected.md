---
title: "Toshiba L650 Battery not being detected"
date: 2010-12-07
forum: Hardware
---

### Post by scared0o0rabbit on 2010-12-07
Just got a new laptop, and everything is working great (after installing the wireless drivers), except for one thing.  Ubuntu isn't detecting that there's a battery in the computer, and it doesn't seem to know the difference between when it's plugged in and not plugged in.

Any suggestions on things to look at or try?

---

### Post by scared0o0rabbit on 2010-12-10
Bump?

---

### Post by itilious on 2010-12-12
I also have a toshiba satellite m35x-s149 with ubuntu 10.04 lucid installed with this same issue

i've been searching for about a week straight for a fix and have found nothing, any help on this is GREATLY appreciated

---

### Post by itilious on 2010-12-13
update:

i updated the bios to 2.0 for this laptop and it fixed the issue 

i'm A+ certified and I passed this idea up:oops: pretty embarrassing lol

---

### Post by viswaraj on 2010-12-15
I also have same problem on my Satelite L650 with ubuntu 10.04 lucid

---

### Post by scared0o0rabbit on 2010-12-16
Actually, I meant to put in my original post that I'm running Maverick not Lucid.

---

### Post by shak courses beekeeping on 2010-12-16
great downloads! i find this forum very interesting. thank for the information

---

### Post by techinterplay on 2011-01-11
Hello,

Just bought a Toshiba Satellite L650 laptop and I have the same issue of battery not being detected. Is there any workaround for this ?

-------------------------
dmesg | grep batt
[    0.963845] ACPI: Battery Slot [BAT1] (battery absent)
-------------------------
Installed Version is 10.10 and everything updated to the latest.

---

### Post by sigfrido on 2011-01-15
Hi. I also have the same problem on a satellite L655 (running lucid):

[http://ubuntuforums.org/showthread.php?t=1546463]("http://ubuntuforums.org/showthread.php?t=1546463")

I noticed very recently that Advanced Power Management for hard drives detects the battery. Somehow, however, the system in general does not seem to do so.

---

### Post by rvsh07 on 2011-01-18
I have the same problem on my Toshiba Satellite L650-BT2N23. I have tried multiple Ubuntu releases (9.04, 9.10, 10.04 and 10.10) in addition to other distros such as Mandriva, Fedora and OpenSuse, but nothing has worked so far. I have also tried rebuilding some of the older kernels with the copy_dsdt patch described in ([https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)), but no joy. 

It looks like this is a common problem in various Toshiba Satellite models, and I have not found a solution in any forum so far. The DSDT supplied with my laptop was compiled with a Microsoft compiler, and upon recompiling with Intel's compiler, it returned some errors and warnings. I was able to fix the issues and recompile, but even the patched kernel (with fixed DSDT) did not seem to resolve the problem :(

@sigfrido: looks like your issue is exactly the same.

I found a bug open in launchpad for this issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703302](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703302) 

Hope this will solve the ACPI issues..

---

### Post by Eric J on 2011-01-30
I'm experiencing this same issue.  Any help would be greatly appreciated.

---

### Post by scared0o0rabbit on 2011-04-30
Bumping this up.  Just installed 11.04 (kubuntu) still having the same issue.

Anyone have any suggestions yet?

Also just updated to the latest bios (2.30 from 3/31/2011), which didn't make any change either.

I have no idea if this gives anyone any clue as to what's going on, but I installed acpi and ran it with -V and got this:


Adapter 0: on-line
Cooling 0: LCD 7 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10

My laptop was unplugged at the time...

---

### Post by itilious on 2011-05-01
> **scared0o0rabbit said:**
> Bumping this up.  Just installed 11.04 (kubuntu) still having the same issue.

Anyone have any suggestions yet?

Also just updated to the latest bios (2.30 from 3/31/2011), which didn't make any change either.

I have no idea if this gives anyone any clue as to what's going on, but I installed acpi and ran it with -V and got this:


Adapter 0: on-line
Cooling 0: LCD 7 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10

My laptop was unplugged at the time...

When I updated to latest bios from toshiba(stated it had ACPI fixes) it fixed the "no battery" issue for me, but I still constantly would get an error saying "power management" was locking up upon login.  This issue eventually went away without anything done on my part, prob just an update fixed it. <<<--- Ubuntu 10.04 32bit

I just upgraded the same Toshiba mx35-S149 laptop to 11.04 Ubuntu the other day and it basically broke every single application i use on Ubuntu so i went back to 10.04 again, too new for me. So I can't help you with 11.04 much at all but,,,,

,, only suggestion I can offer is re-install Kubuntu AFTER you have applied the bios update. When i first updated the bios on my toshiba it didnt show any improvement, I re-installed for another reason and notice the issue was fixed with the only change being the bios update. This suggestion is just from experience, I'm still new to the linux scene myself :) Good luck on the hunt for the answer tho :)

---

### Post by scared0o0rabbit on 2011-05-02
I had considered doing that, but wasn't sure it would be necessary.  Maybe I'll launch with a live cd and see if it shows up that way before I wipe everything again, and see if it shows up that way.

---

### Post by scared0o0rabbit on 2011-05-03
A fresh install of 11.04 didn't resolve the issue either.

---

### Post by subbs on 2011-07-18
This might surely help all of you:

[http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)

---

### Post by scared0o0rabbit on 2011-07-25
That certainly did solve the problem.  The question I have is if this is something I'm going to have to repeat every time a new kernel version comes out?  If so, are there any of the steps that I can skip from now on, or am I just going to have to redo the process every few weeks?

---

### Post by scared0o0rabbit on 2011-11-28
I moved onto debian several months ago, and had the same problem there.  In answer to the question I posted above, yes if you follow that guide you will need to recompile your kernel each time a new version comes out.  I'm going to attach the files I used to correct this for a 64 bit install.  I have no idea if these will help people out over here but I can't imagine them being much if any different.

The DSDT.aml file should be placed in the /boot directory.  The 01_acpi file should be placed in /etc/grub.d

Afterward run update-grub2 and you should see it add a line about loading custom DSDT table.  On your next boot you should see your battery working, even in a kernel where your custom DSDT isn't recompiled in.  If you have a different laptop than the model I'm using you will of course want to not use my DSDT, but you could use the same script.

Now for credit where credit is due:

Information on how to get the DSDT.aml was taken from [http://techinterplay.com/fix-toshiba-battery-issue-linux.html]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html").  If you need a different DSDT file I imagine the process is very similar for other laptops.  This guide talks about recompiling and everything as well, but you can skip all of that if you are going to load it through grub 2.  It also doesn't mention the .aml file, but you will make it at the same step that you make the .hex file

Information on loading the custom dsdt.aml file into grub2 comes from [http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/]("http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/") which is also where I ultimately found the script in the attachment as well.

Hopefully this helps someone else.  I'm marking this as solved.

---

