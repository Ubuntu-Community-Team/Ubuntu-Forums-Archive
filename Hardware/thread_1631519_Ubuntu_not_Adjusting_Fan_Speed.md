---
title: "Ubuntu not Adjusting Fan Speed"
date: 2010-11-26
forum: Hardware
---

### Post by gerowen on 2010-11-26
I've had this problem across several versions of Ubuntu and other distributions as well, and nobody has ever been able to fix the issue.  I'm using a Toshiba Satellite L355D-S7829 with Ubuntu 10.10 64bit.  Ubuntu detects the make/model of the laptop on install because it tries to name the computer accordingly.  My CPU fan speed is always stuck on next to zero.  It's just "barely" running at all.  I did a:
```

cat /proc/acpi/fan/FAN1/state

```
and got
```

status:                  off

```
I'm unable to make any changes to this file even as root.  Can anybody lend me a hand at all?  The problem is that any time I do "anything" somewhat CPU intensive my video card and cpu begin to heat up rapidly and I can't really get them to cool off.  I don't have this issue with Windows, and the CPU fan is clean and clear of dirt/dust.

---

### Post by fiacobelli on 2010-12-05
I have a similar problem: Ubuntu 10.10 64bits on a laptop (HP dm1z). However, I get the opposite. The CPU is constantly at 53C (as reported by proc/acpi/thermal_zone/temperature) but the fan is running at full throttle and I can't get any info on it. /proc/acpi/fan/ is empty.
Is there a way that I can know what the fan is doing? or how does it determine to go full speed? This just started happening. 

Any advice, anyone?

---

### Post by Silent_Surface on 2010-12-07
I agree that this is an issue. I have a Toshiba laptop also, and have no choice but to run WIN7 on it, since Ubuntu will cook my laptop.  The fan runs either not at all, or V E R Y slowly, and temperatures rise rapidly. If left on, the laptop will reach a thermal limit and shutdown. WIN 7 does not have ANY overheating issue with this laptop, so it is not a dirty fan issue, or dirty heat-sink, or any other hardware related issue.  Ubuntu 10.10 just can not manage the fan to cool the laptop. It is sad, I have used Linux almost exclusively for 4+ years, and have had to go back to Windows full time.
:confused:

---

### Post by kd4dii on 2010-12-07
Hello all
     I have a Toshiba c655 and was having a lot of problems with usb.  It seem the BIOS is buggy.  I tried with the acpi turned off but that can lead to fan problems like those mentioned above,  The best fix I have found involves editing ect/default/grub and edit it 

add to line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt"  

This must be done as root and after you should run "sudo update-grub" in the terminal and reboot.
     I don't know if this will help the above problems but with my machine the acpi appears to operate normally with this edit.  Hope this helps.

bob

---

### Post by gerowen on 2011-02-07
This is an old post, but it's still an existing problem.  In Linux, my fan refuses to adjust speed.  So whereas in Windows I'm just fine with maxing out my CPU for extended periods of time for whatever reason (updating virtual machines while playing age of empires), if I try to do anything for too long in Linux I'm forced to close it down to avoid damage to my computer.  I can't even watch flash videos for more than 5 minutes.  In Windows I have no such problems.

---

### Post by t0adman on 2011-03-03
This is worrisome considering I plan to run 10.10 64-bit on my new dm1z scheduled for delivery on Monday.  

Is there any course of action to elevate awareness around specific issues and encourage people to work on a solution?  I'm a humble follower with zero ability to create the solution so I'm eternally grateful for those who can and do.

---

### Post by AliceKingsley on 2011-03-16
> **fiacobelli said:**
> /proc/acpi/fan/ is empty.

I have the same problem, with 10.10 running on an HP tx2500. Could someone who has a populated /proc/acpi/fan/ please a post a copy of what is supposed to be in that folder? Trial and error might get me somewhere from there.

Thanks for any help.

---

### Post by bilderbuchi on 2011-03-17
> **t0adman said:**
> Is there any course of action to elevate awareness around specific issues and encourage people to work on a solution?  I'm a humble follower with zero ability to create the solution so I'm eternally grateful for those who can and do.
Yes. Go to launchpad.net, find a bug report which is relevant to your problem, and contribute. Check the "affects me too" button instead of posting a "+1" message, to raise visibility of the bug. Read the comments, find out if anything is missing in the bug description (often the output of various console commands which are typically given; not more difficult than copy&paste), provide relevant details.

---

### Post by gerowen on 2011-04-24
I just wanted to let everybody know that after a couple of years I have FINALLY solved this problem.  I'm currently running Debian 6.0.1, but was having the same issues.  The problem lies in the proprietary ATI drivers that come from Debian/Ubuntu repositories.  Here are the steps I took and my fan speed is now adjusting normally.  I'm not sure which of these two steps actually solved the problem though, but if I narrow it down I'll let you know.

1) I ran this command as root in the terminal:
```
aticonfig --acpi-services=on
```

2) I removed the fglrx driver that I got from the Debian repositories and installed the proprietary driver from ati.com.

I can FINALLY watch flash videos without my computer overheating in a matter of a minute or two, lol.  You guys have no idea how happy I am to have finally solved this problem, lol.

---

### Post by gerowen on 2011-04-24
So I did a full shutdown/poweroff, then rebooted the computer, and the fan not speeding up again became an issue.  I re-ran the following commands as root and rebooted again and then the fan operated normally, actually holding the temperature at around 70 celsius while doing operations that would normally make it peak out at about 95 before the computer would overheat and shut itself off.  Kind of odd, hopefully this time it sticks.

```

aticonfig --acpi-services=on
aticonfig --acpi-display-switch=on

```

---

### Post by gerowen on 2011-04-24
So it's official, if I shut all the way down, when I power the computer back up the fan will revert back to being stuck at barely spinning at all, and temperatures will rise. Once I run those two commands in the previous post as root, then do a normal "Restart" the fan behaves properly. Weird...

---

### Post by KegHead on 2011-04-24
Hi!

Has anyone updated the kernel?

sudo apt-get update

sudo apt-get install linux-image -f

or

sudo aptitude install linux-image -f

KegHead

---

### Post by gerowen on 2011-04-24
Kernel is up to date.

Alright, I've written a script to add the commands to your rc.local so they should run as root on startup.  This APPEARS to have fixed my problem, I've been rebooting and playing Unreal Tournament 2004 for about 30 minutes to make sure the fan keeps up and holds temps down, and it seems to be working just fine.  Just download the script, make sure it's executable, and run it from a command line.  It makes a backup of your rc.local as it is before it makes any changes, appends the commands with a comment line and some white space to help you see where the added text was, and it runs the commands for you since rc.local has already been run at boot-time.  If any of you guys are having similar issues give this script a shot, and if it works for you please post back here and let me know.  Hope this helps everybody out!

**[Download the Script Here](http://adams-family.homeip.net/software/fixfan.sh)**

---

### Post by sasidevan on 2012-04-01
@GEROWEN >>>
Hi... many thanks for posting this solution....It has worked for me... I am using Lubuntu 11.10 and my dell laptop was switching off after a few minutes of usage (especially when using flash player...).. There was no problem when I boot Windows... I cleaned the fan and all, but the problem persisted... Now very happy ....
I think the problem doesn't happen with Ubuntu 10.04 LTS but happens with all other versions....

---

### Post by sRaaSilva on 2012-05-06
When i installed the Ubuntu arrived _**overheating**_ matter where in the BIOS. My computer is  **hp g6 coer i5 laptop with switchable ati 6470M graphic** . I already try all of post in this posts but i still can't found real solved.

Please help me!   :mad: :mad: :oops:

---

