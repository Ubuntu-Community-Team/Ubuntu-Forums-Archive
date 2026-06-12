---
title: "Grub2 doesn't boot xp"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by rafaellaguna on 2009-10-23
I have installed xp on sda1 and karmic RC on sdb1. it worked with jaunty, but now grub doesn't recognize windows drive. Xp appears on the menu but when I select it says "error: no such device:0620f43920f430f3". Could anyone tell me, please, how to edit menu.lst or grub.cfg or whatever to enable this device?:( thanks in advance

---

### Post by Cybie257 on 2009-10-23
I had a similar problem a while back. The way I fixed it at the time, although I'm sure there are better ways but I was in a hurry, was to shut down, unplug the windows drive, reboot, update grub, shutdown, plug the windows drive back in, reboot, and update grub again. 

Sort of a crazy way to do it, but it has something to do with changing things in my BIOS for boot order and the UUID of the drive(s). If no better way comes up, then give this a try. 

Just updating GRUB never worked for me until I did the above steps. 

hope this helps,
Cybie

PS. Be sure the Linux drive is set as the first boot device in BIOS

---

### Post by Dullstar on 2009-10-24
I am having this...  exact...  problem.  Except, it doesn't give an error, it just sits at a screen containing a flashing _

---

