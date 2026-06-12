---
title: "Dell laptop fan gets stuck on high untill poweroff/suspend"
date: 2014-11-08
forum: Hardware
---

### Post by Trevorius on 2014-11-08
I was trying to use thread [http://ubuntuforums.org/showthread.php?t=2114236](http://ubuntuforums.org/showthread.php?t=2114236) that is marked as solved in order to solve my own identical issue with my identical model of computer but I need some suggestions on how to apply the solution that was posted and the thread was closed so i can't post in it. The original thread said:

"> [SOLVED] Dell laptop fan gets stuck on high untill poweroff/suspend 
 Hi everyone,

 I have a Dell Vostro 3750 with the dreaded Nvidia Optimus and Ubuntu 12.10 on it.
 Everything works pretty well except the fan (and other known things which I don't bother that much).
 Power consumption is good (maybe a bit better than in W7). All works well until I do some intensive work and the CPU temperature gets high. At some point the fan hits max rpm (~4200) which is normal.
 The issue is that even the CPU & Co cools down at < 45 C, the fan remains stuck at max rpm. The only way to reduce the fan speed is to go through a power off or a suspend (restarting ubuntu doesn't help). Sounds like a hardware problem but in W7 doesn't happen - when the CPU temp decreases, the fan rpm goes down. In Ubuntu I can leave it alone for 3 hours, the cpu cools down to 35 degrees, cpu load is 2-4% but the fan stays on max rpm until I suspend the pc and resume.

 Any clues as what to check and where to start?
 Thank you."

and a later post said:

> SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED

 Solution:
Code:
 sudo gedit /etc/default/grub
Modify line 12, instead of:
 GRUB_CMDLINE_LINUX=""
 make it:
 GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
 save, close gedit and then:
Code:
sudo update-grub
I found this solution some time ago related to a fan problem and also to other issues but I tried it with GRUB_CMDLINE_LINUX="acpi_osi=Linux", with GRUB_CMDLINE_LINUX="acpi_osi="Linux"" and with GRUB_CMDLINE_LINUX="acpi_osi='Linux'" (I think?) with no luck
 Today I found another link
[http://www.maximumpc.com/article/new...eased#comments](http://www.maximumpc.com/article/new...eased#comments)
 and said "Whoaaa, where was my head?! How about some java/C syntax?? I tried and voila!

 I did intensive tests, run the cpu up 85 C (couldn't get it higher), now the fan has all the speed steps as in win (instead of 4), reaches top speed at 80C (instead of 72C) and beautifully reduces its speed as soon as the temp gets back to 70_something. 

 Me happy

 Thanks for assistance guys!

Which sounds awesome but when i attempt it, it doesn't seem to be working. When i edit the grub file and save it as "acpi_osi=Linux" it lets it save but doesn't seem to affect the fan behaviour, and when I edit and save it as "acpi_osi=\"Linux\" then when I do sudo update-grub it won't update and gives a a CMD message saying "Syntax error: EOF in backquote substitution" as if it won't accept the code I've saved. I don't know how to get around this. Can someone clarify the exact scripting I need to be using? This really isn't my forte.

---

### Post by Trevorius on 2014-11-09
I'd be interested in any feedback or suggestions of course. :)

---

### Post by cipx2 on 2014-11-09
It was supposed to edit the grub file with superuser rights (type in a terminal window): sudo gedit /etc/default/grub
Then save the file (with the same name, not <save it as "acpi_osi=Linux"> as you wrote above) - just got to menu File > Save (or Ctrl+S). Then close the editor.
Then type in a terminal: sudo update-grub. It works with no errors! I just tested it.
Then reboot the computer.
Then see if the fans start behave more normal.

On the other hand, all this was for Ubuntu 12.10 and it's not needed no more starting with 13.10 - which was the 1st ubuntu flavor which really worked like a charm out of the box for this type of Dell (plus installing bumblebee because of the ***** nvidia optimus card it has - i hope you did that no matter the ubuntu version).
 
On the 'third' hand, this stupid laptop might spin the fans like crazy for hours for all sorts of reasons not really connected with the operating system, software or program load. Examples: usb power load (something connected to usb ports that drains a lot of power) or battery overheating (which it does everytime you charge it from under 5% juice left when it gets close to 100%). These have nothing to do with the O.S. and cannot be software controlled (only hard - remove the battery or the heavy power consumers in the usb ports).

---

### Post by Trevorius on 2014-11-09
Yes I edited the file with kate and saved it with the same file name and re-opened it and made sure it was saved. I meant save it with that version of the scripting not with any different file name. But I haven't went to a new version of ubuntu since before your original thread so if a version update will correct all these issues I will try that. I've been through a good 5 version of (K)ubuntu and gave up on new versions really correcting issues as every time it corrected one thing it causes another lol.

Thanks for replying btw! I really think I'm going to get it solves this time after years of this driving me crazy.

---

### Post by cipx2 on 2014-11-09
I don't what to say about Kubuntu, never tested the KDE. I'm on regular ubuntu and I can recommend you the 14.04 - preferrably installed from scratch.
Backup your entire partition(s) before upgrading though (clonezilla is my favorite by far).
Good luck!

---

### Post by Trevorius on 2014-11-09
I never bother backing anything up except a few browser settings like bookmarks and passwords because I have a dedicated 10GB ext4 partition for the OS and never store any of my own data there, only using my separate "storage" FAT partition for that. So I will install it right away. I just have to find a flash drive to do it with or maybe a blank DVD. Wow, I just realized I haven't burnt a DVD in a good couple years lol.

---

