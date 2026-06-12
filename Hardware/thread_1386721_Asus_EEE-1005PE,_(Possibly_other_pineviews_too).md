---
title: "Asus EEE-1005PE, (Possibly other pineviews too)"
date: 2010-01-21
forum: Hardware
---

### Post by chadraytay on 2010-01-21
This applies to netbook and desktop editions.
Ubuntu fails to detect both keyboard and mouse, leaving system unusable.
System information lists both as "unsupported"
Also, lspci -vvnn gives odd responses to most of the hardware.
It gets most of the info but is full of "ACCESS DENIED" 

I used to usb keyboard and mouse to check and the driver wizard states no drivers needed/in use so it doesnt appear to be a proprietary issue...

:popcorn:


***after more poking around***
Uh, how odd. Express gate is installed though, and that's linux... and works perfectly fine. Least I can do a number of things without booting 7... ***shudders***

---

### Post by Hansmc on 2010-01-25
I was thinking about getting one of these, so I hope someone gets this figured out soon. [Here it says "As with the 1005HA, most of the stuff works fine out of the box, although there are some minor wireless connection issues."]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005PE") Let us know if any thing new comes up.

---

### Post by Link338 on 2010-01-25
I concur. Same problems with my 1005PEB. Also seems they've made it almost impossible to revert to anything other then Windows 7.

---

### Post by NESJumpman on 2010-01-26
Is this a problem after trying to install to HDD, or is this a problem trying to run from an SD card?

Should that even make a difference?

---

### Post by chadraytay on 2010-01-26
Xp runs fine. They even include 3/4 of the drivers needed on the disk that installs 7...

---

### Post by chadraytay on 2010-01-27
Alright now... wtf...

Happy to report that it's working now...
Not sure how, not sure why, not sure I care. lol

Um, steps taken. Used usb mouse and onboard program to type and did an apt-get update, sudo update-manager

Did all updates, rebooted. 
Same as before, got dissapointed. Plugged laptop in as battery was low, rebooted intending to go to windows.

Forgot to press arrow key and select windows, ubuntu starts loading. I pressed and held power till it died. Turned it on, ran windows for a bit. Rebooted to fiddle with xorg.conf and see if that would help...

Everything works upon startup. ?????????  No clue, guess it thought I was mad at it. :-/

oh well. It appears I may not have sound yet but I saw 10000 kernel crash messages related to intel sound card so at least I know the problem there. 
Oh, and brightness settings are way out of order. Keys work to change it but it's like, 100 then 50 then 10 then off then 30 then 50 then off then 100 again...

---

### Post by chadraytay on 2010-01-27
Ok, figured out exactly how to make the keyboard and mouse work...

unplug the computer. :-/

You can plug it in after it starts. But not before. And everything but sound works fine. If its plugged in completely during the entire startup process (I was plugging it in as it started the first time it worked) then keyboard and mouse are disabled...

very strange

---

### Post by Hansmc on 2010-01-27
> **chadraytay said:**
> Ok, figured out exactly how to make the keyboard and mouse work...

unplug the computer. :-/

You can plug it in after it starts. But not before. And everything but sound works fine. If its plugged in completely during the entire startup process (I was plugging it in as it started the first time it worked) then keyboard and mouse are disabled...

very strange

Thanks, chadraytay, for keeping us up with what is going on. I would be interested in knowing if any one else is having similar problems. Or is it just your system?  Have you contacted Asus, to see if they know anything about this? Thanks, I will keep looking in.

---

### Post by fajoes on 2010-02-16
I have the same problem with the brightness controls.
Does someone have a solution to this?

---

### Post by chainsonviolet on 2010-02-22
I am also having issues finding a solution to getting brightness control working on my 1005PEB. I've tried a couple of things:

-eee-control doesn't support this model yet (I'm impatient :P)
-xbrightness, which gives me no results whatsoever.

Still hunting around for a possible solution, wondering what others have tried and found.

---

### Post by chreekat on 2010-02-25
> **Hansmc said:**
> Thanks, chadraytay, for keeping us up with what is going on. I would be interested in knowing if any one else is having similar problems. Or is it just your system?  Have you contacted Asus, to see if they know anything about this? Thanks, I will keep looking in.

I'm also experiencing a problem with the touchpad and keyboard on the EEE-1005PE.

1. Xubuntu via Wubi worked fine... for a while. After a Xubuntu system update and a restart, the devices were inactive. I could plug in a USB keyboard and mouse and they worked fine, however.

2. I booted Ubuntu Netbook Remix 9.10 off of a USB, and the keyboard and touchpad worked fine.

3. I installed UNR to the hard drive, and upon restart the problem again manifests. I didn't try a USB keyboard or mouse yet. 

That's all I've had time to find so far!

---

### Post by sornen on 2010-03-11
Installing the latest BIOS using the Windows 7 utility fixed the keyboard and mouse problems for me.

---

### Post by luwandah on 2010-03-27
Updating to the 0901 BIOS does fix the keyboard/mouse issue. Brightness control can be fixed with changing the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

in /etc/default/grub and then running update-grub2. (found this in other threads).

I was concerned about ubuntu's performance on my new netbook until I updated my BIOS. Now things work.

---

### Post by arthurmaciel on 2010-06-28
So, is everything working for Asus EEE 1005pe running Ubuntu? I'm intending to buy one it. Is the keyboard alright?

Thanks,
Arthur

---

