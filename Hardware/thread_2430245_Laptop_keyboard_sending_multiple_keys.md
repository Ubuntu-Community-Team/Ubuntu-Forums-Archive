---
title: "Laptop keyboard sending multiple keys"
date: 2019-10-29
forum: Hardware
---

### Post by kenshie on 2019-10-29
Hey guys,

I have a weird problem. Running 18.04 on a Dell Inspiron 5570.

The built in keyboard behaves wonky, with Ubuntu recognizing multiple incorrect characters for a single keypress, mostly on the number pad.

Eg. if i hit '3' on the number pad, the following keys will register q,w,e,r,u,i,o,p,numlock,page up,numpad 4, numpad 3. Similar issue exists if i hit numpad 6 or delete button, with different keys being registered for each.
Images attached show the keys registered when a single key is pressed:
numpad 3
[ATTACH=CONFIG]284293[/ATTACH]

numpad 6
[ATTACH=CONFIG]284294[/ATTACH]

delete
[ATTACH=CONFIG]284295[/ATTACH]

I've tried resetting / changing keyboard layout multiple times. Messing with the layout sometimes fixes the issue for a few minutes. The issue sometimes goes away on reboot, I know it's not a hardware issue since I do not have the problem on Windows (laptop is dual boot). External keyboards are not affected by the issue either. 

I ran the following command, rebooted the system with no change:
sudo apt-get --purge autoremove xserver-xorg-input-all && sudo apt-get install xserver-xorg-input-alln/ 

Can anyone point me on where to check next? Note the issue did not occur when the OS was first installed, only a few months after.

---

### Post by kenshie on 2019-10-31
bump

---

### Post by Autodave on 2019-10-31
The only suggestion that I can think of would be to try and boot the machine from an installation USB or DVD and just run it from that to see if it works.  If it does, then I would seriously consider re-installing 18.04

---

### Post by kenshie on 2019-11-01
Wow... ok so it definitely IS a hardware issue.

While trying to boot from a live USB I noticed that the menus wouldn't select in the BIOS. For giggles I decided to boot into Windows and recheck the operation of the keyboard (even though I checked it before making this post), lo and behold the keyboard does the same wonkyness as in Ubuntu. Checked under the laptop- noticed 3 screws missing on the side with the numpad. If I flex the base of the laptop or hit it a smack the keyboard suddenly works perfectly again!

 It seems like some sort of grounding issue stemming from the missing screws causing the keyboard to send mixed signals. When I get home I'll salvage some screws from an old laptop and replace the missing ones.

+1 internets to Autodave for pushing me in the right direction

---

### Post by kenshie on 2019-11-01
Pulled some screws off an old IDE hard drive in work, luckily they're the same threading as the current screws. I noticed that ALL the original screws were loose, and probably would have all fallen out at some point. Boo to Dell for not using threadlock. 

I only wish I hadn't undone so much of my customizations to Ubuntu trying to hunt down this problem... but oh well, glad that it's over :D

---

### Post by Autodave on 2019-11-01
Sorry: was going to tell you to mark thread as closed, but you had already done that.  Glad we could help you!

---

