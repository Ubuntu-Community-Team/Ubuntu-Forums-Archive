---
title: "A how-to for Ubuntu Breezy on a ThinkPad T42"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by emendelson on 2005-10-27
A first try; please let me know of corrections or additions:

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html)

---

### Post by emendelson on 2005-10-28
I've added a "what not to do" section to the how-to, because a lot of obsolete information is floating around the web, and tends to get repeated and reused without having been tested.

---

### Post by cportner on 2005-11-15
Thank you for the how-to. Very useful even for my Thinkpad T43p. I originally wanted to put Debian on it, but that turned out to be more trouble than it was worth, so I ended up with Ubuntu instead and are very happy with the result.

Two comments on the how-to:

1. I was unable to get the "Visual feedback for Fn+F5 (Wireless on/off)" part to work. The wireless.sh script refers to "/proc/acpi/ibm/bluetooth", which does not appear to work if you do not have bluetooth (like me). I can toogle the wireless on and off, but with the script the computer froze.

2. For the T43p hibernate does not work out of the box, so it looks like I will have to mess around with that. I guess the most direct way is using softwaresuppend2 (which requires a recompile).

---

### Post by emendelson on 2005-11-15
Thanks for the good words. 

1. Could you post the original contents of your wireless.sh script here? I'd like to post a "no-bluetooth" version on my page and it shouldn't be hard to sort this out.

2. For hibernating, it can't hurt to try the solution I offer in the section about a possible hibernation problem. If it doesn't help, just put "splash" back in the file (or restore the backup).

---

### Post by strawman on 2005-11-15
Hi emendelson
nice work on the Thinkpad T42 guide and on having a functioning suspend and hibernate.

I have a HP nc8000, and initially, I had suspend working but now for whatever reason it stopped: the laptop powers down OK but will not resume fully from suspend.  And i'm not running the fglrx drivers.

Would you post your /etc/default/acpi-support file?  Maybe i'm missing something in mine.

---

### Post by emendelson on 2005-11-15
[QUOTE=strawman]Would you post your /etc/default/acpi-support file?  Maybe i'm missing something in mine.[/QUOTE]

I'm away from the Thinkpad for a while, but I don't think my acpi-support would tell you anything, because it's the original, unchanged, default version of the file. I reinstalled after working on my page, because I didn't want to have the modem and other drivers in there, so I haven't touched acpi-support. If it would still help to have it, maybe someone else could post it - or I'll do so when I get back to that machine.

By the way, I didn't do anything to get suspend/hibernate working. They worked from the start, with no changes to the system at all.

---

### Post by tictactatic on 2005-11-23
Hi,

Thank you for the thorough howto. I've been implementing it gradually, albeit with Kubuntu.
Hence the question: how do you enable OSD display under KDE? Has anyone done it?

Thanks in advance

---

### Post by emendelson on 2005-11-23
[QUOTE=tictactatic]Hi,

Thank you for the thorough howto. I've been implementing it gradually, albeit with Kubuntu.
Hence the question: how do you enable OSD display under KDE? Has anyone done it?[/QUOTE]

Never tried it under Kubuntu - but an earlier version of that script used a method that didn't require the Gnome PostLogin feature. Here's how I think it worked:

In the OSD script, (1) remove the line that begins xuser= and (2) in the line below that line, replace the string "&xuser" with your actual user name, so that it begins something like this:

   su - username -c "echo etc etc....

with the string "username" replaced by your actual user name (no quotes around the username).

Please let us know if it works correctly under KDE...

---

### Post by umlungu64 on 2005-11-27
I have done most of your suggestions, and they work perfect! Thank you very much! As I'm new to Linux, it was very good documented.
But I do have a simular problem, when I run the Fn+F5, my system hangs! Where do I have to put my username in, and where not! There is one in the PostLogin/Default, and also in the acpi/osd! Are there any samples for a beginner?
Would be nice to hear from you!

Thank you again for the great work!

Heinz

---

### Post by emendelson on 2005-11-27
[QUOTE=umlungu64]
But I do have a simular problem, when I run the Fn+F5, my system hangs! Where do I have to put my username in, and where not! There is one in the PostLogin/Default, and also in the acpi/osd! Are there any samples for a beginner?[/QUOTE]

Thank you for the good words. If you follow the method on my page (originally devised by J. Kraemer) you will not need to enter your user name at all. The PostLogin/Default script enters your name automatically. If you use the scripts on my page exactly as they are written, it all should work.

---

### Post by popie on 2005-11-28
Anyone know if Ubuntu will work on a Thinkpad T40 with Intel Centrino wireless? (Intel PRO/Wireless LAN 2100)

I tried the live CD, but could not get wireless working. I'm not a Linux expert however, and info I found on the net was for other wireless cards.

---

### Post by umlungu64 on 2005-11-28
Sorry to bring this up again!
Okay, if the username is not needed, how come, my system hangs when I press Fn+F5. The harddrive starts spinning, and no action on the mouse at all! After about half an hour, it is still hanging, and I switched it of with the Powerbutton. I have copied the files from your articel, so I don't think I did any typing wrong. Have you got any idee, or how do I uninstall the function again?
Regards Heinz

---

### Post by emendelson on 2005-11-28
[QUOTE=umlungu64]Sorry to bring this up again!
Okay, if the username is not needed, how come, my system hangs when I press Fn+F5. I have copied the files from your articel, so I don't think I did any typing wrong. Have you got any idee, or how do I uninstall the function again?
Regards Heinz[/QUOTE]

I am sorry to say I can't imagine what could be wrong. You can undo the changes I described by simply going back and restoring the orginal version of the wireless.sh script that you copied to wireless.sh-original, if you followed by instructions, and you may want to delete the PostLogin/Default file. You rename a file with the mv command, like this:

cd /etc/acpi
sudo mv wireless.sh-original wireless.sh

Perhaps you have a different T42, with an Intel wireless adapter instead of the IBM/Atheros wireless adapter? That might affect this. I've only tested with the IBM/Atheros adapter.

---

### Post by umlungu64 on 2005-11-28
Hello again!
I do have a Intel PRO/Wiress 2200BG, so that might be the problem! So I did the reverse thing with Fn+F5, and it's fine again!
Also I found out, that my suspend to disk does not work anymore. But now I fount out, that I do have the Laptop-Mode already installed, perhaps that brings up the conflict. But if I want to uninstall it, it wants to delete three more programs, like acpi and ubuntu desktop! How can I get rid of it?

Thanks for your effort! Heinz

---

### Post by emendelson on 2005-11-28
[QUOTE=umlungu64]Hello again!
I do have a Intel PRO/Wiress 2200BG, so that might be the problem! So I did the reverse thing with Fn+F5, and it's fine again!
Also I found out, that my suspend to disk does not work anymore. But now I fount out, that I do have the Laptop-Mode already installed, perhaps that brings up the conflict. But if I want to uninstall it, it wants to delete three more programs, like acpi and ubuntu desktop! How can I get rid of it?

Thanks for your effort! Heinz[/QUOTE]

I don't think laptop-mode is the problem, and I don't know the answer to your uninstall question. Perhaps it might be best to start a new thread about laptop mode, and ask that way. I do not know anything else that might help. These procedures have worked perfectly for other people.

---

### Post by RdM on 2005-11-30
[QUOTE=tictactatic]Hi,
Hence the question: how do you enable OSD display under KDE? Has anyone done it?
[/QUOTE]
Sure you can get the OSD-display. At least it works in Gnome (Probably works in KDE too?). For IBM thinkpads there is a nice little utility called tpb. Check out this little nice how-to: [Thinkwiki]("http://thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_(1875)")

---

### Post by emendelson on 2005-12-01
[QUOTE=RdM]Sure you can get the OSD-display. At least it works in Gnome (Probably works in KDE too?). For IBM thinkpads there is a nice little utility called tpb. Check out this little nice how-to: [Thinkwiki]("http://thinkwiki.org/wiki/Installing_Ubuntu_5.04_on_a_ThinkPad_T43_(1875)")[/QUOTE]

I think the question was NOT about the OSD display in tpb, but the entirely separate and different OSD  described in the first post in this thread, and designed for use with Fn+F5:

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#wirelessbutton](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#wirelessbutton)

---

### Post by RdM on 2005-12-02
[QUOTE=emendelson]I think the question was NOT about the OSD display in tpb, but the entirely separate and different OSD  described in the first post in this thread, and designed for use with Fn+F5:

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#wirelessbutton](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#wirelessbutton)[/QUOTE]

sorry... my fault

---

### Post by VCSkier on 2006-02-09
first of all, i'd like to say your guide is great, and was very helpful to me, as well as good practice for leaning some of the basic in's and out's of ubuntu (btw, i'm very new to linux).  im using an ibm t41, which appears to be very similar to the t42.  from what i can tell, the only hardware differences between my system and the t42 are:

1.  i have an centrino, intel 2100 (b only) wireless card.
2.  i dont have bluetooth support.
3.  i have the ati radeon mobility 9000 graphics card.

i have not been able to get the Fn+F5 wireless control work, presumably because of differences #1 and 2, so i thought i'd post my original wireless.sh script:

```
#!/bin/bash
# Find and enable/disable wireless devices

for DEVICE in /sys/class/net/*; do
    if [ -d $DEVICE/wireless ]; then
# $DEVICE is a wireless device. Check if it's powered on:
	if [ `cat $DEVICE/device/power/state` = 0 ]; then
# It's powered on. Switch it off.
	    echo -n 3 > $DEVICE/device/power/state;
	    echo 0
	else
# It's powered off. Switch it on.
	    echo -n 0 > $DEVICE/device/power/state;
	    echo 1
	fi
    fi
done	
```

secondly, if any of you can point me in the direction of where i might be able to find functioning modem drivers for free, that would be great.  i think the link to the opensource drivers that you posted was broken...

thirdly, because i dont have the hardware to support bluetooth, i wanted to remove any reduntant or unneeded processes/applications from my system.  through synaptic, i removed libbluetooth1, and related applications.  is there anything else i can to do remove bluetooth related items?

finally, support for my graphics card would be nice.  if anyone has found any other means of getting their ati graphics card working w/o compromising suspend/hibernation features, what would make my day.  i tried the steps suggested on the blog that was linked to, but it would not work w/ my card (i do have a different model).

again, thanks so much to all of you, namely emendelson for putting all of this together.

edit: typo

---

### Post by emendelson on 2006-02-09
I'm sorry to say that my page includes absolutely everything I know about the subject!

---

### Post by Maximilian on 2006-02-20
[QUOTE=umlungu64]Sorry to bring this up again!
Okay, if the username is not needed, how come, my system hangs when I press Fn+F5. The harddrive starts spinning, and no action on the mouse at all! After about half an hour, it is still hanging, and I switched it of with the Powerbutton. I have copied the files from your articel, so I don't think I did any typing wrong. Have you got any idee, or how do I uninstall the function again?
Regards Heinz[/QUOTE]
I have the same problem...When i had the ipw2200-1.0.8 driver was all ok but when i have installed the  ipw2200-1.0.10 there is the same problem post above when i press Fn+F5....

---

### Post by LittleLebowski on 2006-02-23
These instructions were very helpful to me setting up Kubuntu and Ubuntu on my brand new FAST Thinkpad Z60m.  Thank you very much.

---

### Post by emendelson on 2006-03-14
There was a serious error in the replacement script for Fn+F5 in the original version of this page. Thanks to Wolfgang Roessler, I have now posted a corrected version here:

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#wirelessbutton](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#wirelessbutton)

The corrected script and instructions are in part 2. If you attempted to use the orignal version, please restore your original wireless.sh script (which you copied to wireless.sh-original) before modifying the ibm-wireless.sh script as described here.

Many thanks again to Wolfgang Roessler.

---

### Post by jfcous on 2006-04-28
IBM had an updated Rescue and Recovery combined with security updates.  When I installed, I could no longer boot into Unbuntu or anything else.  I managed to use another Linux CD to get into the system and it repaired the GRUB bootloader but put it into the MBR.   The IBM repair disk you suggested uses a 3 1/2 in floppy and it will not install to a CD.  I tried installing it to a floppy on a different machine and copy it to a CD but it will not boot.  Any suggestions?

---

### Post by gotmonkey on 2006-07-17
> **emendelson said:**
> A first try; please let me know of corrections or additions:

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html)

I am trying to use your guide on my dapper install. IBM t42 2378R4U. when I get to this point

> cd /etc/udev/permissions.d
sudo cp udev.permissions udev.permissions-backup
sudo gedit udev.permissions

I get this:

simian@ibm-t42:~$ cd /etc/udev/permissions.d
bash: cd: /etc/udev/permissions.d: No such file or directory

Any ideas?

---

### Post by emendelson on 2006-07-17
That guide is for Breezy only. I have no idea whether any of it is relevant to Dapper. I should probably put a warning at the top: "Do not use any of this advice with Dapper unless you are absolutely certain that it applies to Dapper."

Because of many problems amply described in other threads, I don't have Dapper on my ThinkPad. I'll wait for Edgy. Meanwhile, I'm sorry not to be able to help.

---

### Post by gotmonkey on 2006-07-17
thanks for replying back, I do appreciate it. Other than a few minor oddities, I have been happy with D.D. on my T42.

thanks for you help, I am looking forward to edgy. Every release has been better than the last

---

### Post by MrChonks on 2006-07-26
Thanks for the guide.  I was wondering if you could add a section about screen resolution.  I have read through the forums here and there are a number of people who seem to have questions about getting a better screen resolution out of their ATI Radeon Mobility 7500.  I know that I would love to have anything better than 1024x768.

---

