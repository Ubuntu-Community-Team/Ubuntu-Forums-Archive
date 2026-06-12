---
title: "Suspend problem when running LiveUSB from USB 3.0 port"
date: 2014-12-14
forum: Hardware
---

### Post by ping-wu on 2014-12-14
When running Ubuntu 14.04/14.10 from LiveUSB, the system would crash after suspend (either by closing the lid or forcing the system to suspend), when the USB stick was inserted into USB 3.0 port.

This problem was experienced with both USB 2.0 and 3.0 stick.

No problem was observed when the Ubuntu LiveUSB stick  (either USB 2.0 or 3.0) was inserted into a USB 2.0 port.  (I.e., the Ubuntu system would wake up normally after suspend when USB 2.0 port was used)

This problem was reproducible.

---

### Post by ping-wu on 2014-12-17
When I installed 14.04/14.10 into a USB stick (3.0), Ubuntu would wake up normally from suspend (again, from a USB 3.0 port).

It thus appears that this is not a BIOS problem.  The suspend (or more specifically, wake-up) problem only occurred when booting from a LiveUSB stick (USB 2.0/3.0) in a USB 3.0 slot.

---

### Post by sudodus on 2014-12-17
Thanks for sharing this information :-)

1. Would you be prepared to create a bug report at Launchpad?

2. Right now we are testing the alpha version of Vivid Vervet to become 15.04. (I'm testing Lubuntu.) It would be valuable if you test also this version (iso-testing at the following link) and check if it suffers from the same problem.

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by ping-wu on 2014-12-17
> **sudodus said:**
> Thanks for sharing this information :-)

1. Would you be prepared to create a bug report at Launchpad?  

Yes, I will.  I am using this forum to put my thoughts together before posting a more definitive bug report.

> 2. Right now we are testing the alpha version of Vivid Vervet to become 15.04. (I'm testing Lubuntu.) It would be valuable if you test also this version (iso-testing at the following link) and check if it suffers from the same problem.

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

Thanks for the suggestion and the link. Will do.

---

### Post by sudodus on 2014-12-17
Please post here about the bug report and the iso testing results with Vivid Vervet! I'll check after the bug report, if it also affects me, which would make the case stronger.

---

### Post by ping-wu on 2014-12-17
> **sudodus said:**
> Please post here about the bug report and the iso testing results with Vivid Vervet! 

Just tested on the Vivid LiveUSB (Ubuntu 15.04, today's daily built).  Problem seems to have been solved!!!

This test was done with a USB 2.0 stick in a USB 3.0 port.  Will be followed with a 3.0/3.0 test.

Thanks!

---

### Post by ping-wu on 2014-12-17
> **ping-wu said:**
> 
This test was done with a USB 2.0 stick in a USB 3.0 port.  Will be followed with a 3.0/3.0 test.


Unfortunately USB 3.0 in USB 3.0 failed for Vivid LiveUSB.

Will file a bug report in due time.

---

### Post by ping-wu on 2014-12-23
[COLOR=#666666][FONT=Ubuntu]Bug #1405278

[/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1405278](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1405278)

  [COLOR=#333333][FONT=monospace]**Bug Description**

[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]When running Ubuntu 14.04/14.10 from LiveUSB, the system would crash after suspend (either by closing the lid or forcing the system to suspend), when the USB stick was inserted into USB 3.0 port.
This problem was experienced with both USB 2.0 and 3.0 stick.
No problem was observed when the Ubuntu LiveUSB stick (either USB 2.0 or 3.0) was inserted into a USB 2.0 port. (I.e., the Ubuntu system would wake up normally after suspend when USB 2.0 port was used).
When I installed 14.04/14.10 into a USB stick (3.0), Ubuntu would wake up normally from suspend (i.e. no problem with the USB 3.0 port with an installed USB stick).
It thus appears that this is not a BIOS problem. The suspend (or more specifically, wake-up) problem only occurred when booting from a LiveUSB stick (USB 2.0/3.0) in a USB 3.0 slot.
Update: With Ubuntu 15.04, I was able to wake up the LiveUSB when it was on USB 2.0 stick in a USB 3.0 port, but not on USB 3.0 stick.
[/FONT][/COLOR]

---

### Post by sudodus on 2014-12-23
It is valuable to get this kind of bug reports. Thanks a lot :KS

Other people reading this thread: Please check if you have the same or similar problems (in your computers).
If this is the case, please click '[COLOR=#006400]Does this bug affect you?[/COLOR]' in the bug report and maybe add a comment.

---

### Post by sudodus on 2014-12-23
I had no suspend/wake up problem, when a ***Lubuntu desktop 14.10 64-bit LiveUSB stick (USB 2.0)*** was  inserted into a USB 2 port and a USB 3 port. (I.e., the Ubuntu system would wake up  normally after suspend also in my USB 3 port).

Computer: [http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

-o-

@[ping-wu]("http://ubuntuforums.org/member.php?u=1118737"): Did you run a 32-bit or a 64-bit system?

---

### Post by ping-wu on 2014-12-23
> **sudodus said:**
> I had no suspend/wake up problem, when a ***Lubuntu desktop 14.10 64-bit LiveUSB stick (USB 2.0)*** was  inserted into a USB 2 port and a USB 3 port. (I.e., the Ubuntu system would wake up  normally after suspend also in my USB 3 port).

Computer: [http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

-o-

@[ping-wu]("http://ubuntuforums.org/member.php?u=1118737"): Did you run a 32-bit or a 64-bit system?


Thanks.  I am using 64-bit systems.  I have tested on four different machines (HP, ASUS, Acer), including both UEFI and non-UEFI firmwares, and the problem I am experiencing is quite consistent.

---

### Post by sudodus on 2014-12-23
I think it is worthwhile to specify the affected computers (at least brand name and model) in the bug report. Maybe even more specs, for example the output of

```
sudo lshw -sanitize
``` or to run

```
ubuntu-bug <package>
``` so in your case
```
ubuntu-bug linux
```

and let it collect data.

---

### Post by ping-wu on 2014-12-23
> **sudodus said:**
> I think it is worthwhile to specify the affected computers (at least brand name and model) in the bug report. Maybe even more specs, for example the output of

```
sudo lshw -sanitize
``` or to run

```
ubuntu-bug <package>
``` so in your case
```
ubuntu-bug linux
```

and let it collect data.

Will do.

The term "crash" that I used probably need be explained.

When the computer wakes up (from LiveUSB), everything would seem to be normal--the wireless would be re-connected and I was able to continue to browse the existing web page or edit document.  However, I would not able to start a new process, including starting a new tab in Firefox (but OK with Chrome), or opening a new program.

If I tried to start a new process, the system would "then" crash, and I need to use the power button to shut the computer down.

---

### Post by sudodus on 2014-12-23
Yes, that is important to tell us. Otherwise we might just be happy that everything would seem to be normal :-P

But I tested now, and I can start new terminal windows, run cli programs, start firefox and open tabs in it. So it works in my Toshiba. I think this problem is specific to particular hardware, maybe the USB electronics or particular BIOS/UEFI system or some firmware. If you specify the computers affected (and they seem to be mainstream computer brands), it will be obvious to the developers, that it is a rather big problem.

By the way, ***what happens when you install a system to a USB pendrive***, and boot the computer with the pendrive in a USB 3 port? Will it recover from suspend?

---

### Post by ping-wu on 2014-12-23
> **sudodus said:**
> By the way, ***what happens when you install a system to a USB pendrive***, and boot the computer with the pendrive in a USB 3 port? Will it recover from suspend?

As I mentioned in the original post, 1404/1410 recovered without any problem after suspend when it was "installed" on a pendrive.  (I only tested on USB 3.0 stick, no interest in installing Ubuntu into a 2.0 pendrive.)

---

### Post by sudodus on 2014-12-23
Sorry, I forgot that (did not remember that it was installed in a USB pendrive, thought it was installed into an internal drive). Then we know, that it depends on the particular live properties of the operating system (in contrast to installed systems).

---

### Post by ping-wu on 2014-12-24
Just tested on a new Acer machine (Acer-E15 571P-59QA), running 14.04 LiveUSB (2.0) in a USB 3.0 port.  Everything was working OK.  The system woke up and then performed normally after suspend.

It thus appears that this suspend problem is dependent on the type of USB port the LiveUSB stick is plugged in.  I have never had problems with USB 2.0 ports, but have experienced problems with most of the USB 3.0 ports that I tested.

---

### Post by ping-wu on 2014-12-24
> **ping-wu said:**
> Just tested on a new Acer machine (Acer-E15 571P-59QA), running 14.04 LiveUSB (2.0) in a USB 3.0 port.  Everything was working OK.  The system woke up and then performed normally after suspend.

It thus appears that this suspend problem is dependent on the type of USB port the LiveUSB stick is plugged in.  I have never had problems with USB 2.0 ports, but have experienced problems with most of the USB 3.0 ports that I tested.


With this machine (Acer-E15 571P-59QA), no suspend problem was observed (*even*) when the LiveUSB is in a USB 3.0 stick (and inserted in a USB 3.0 port).

I am not changing the title to read [Solved], because there is still a need to find out why some USB 3.0 ports would present suspend problems for a Ubuntu LiveUSB and some won't.

---

### Post by ping-wu on 2015-01-07
[COLOR=#333333][FONT=monospace]Tested 2015-01-06 daily build on one of the previously problem-some machines: ASUS X202E.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]USB 2.0 (stick) on USB 3.0 (port): Now wakes up normally![/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]USB 3.0 (stick) on USB 3.0 (port): still couldn't wake up normally. Because the system crashed after wake-up, I was unable to get a log.[/FONT][/COLOR]

---

