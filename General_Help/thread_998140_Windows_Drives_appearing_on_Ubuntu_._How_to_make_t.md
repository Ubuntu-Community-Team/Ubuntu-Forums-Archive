---
title: "Windows Drives appearing on Ubuntu . How to make them disapper (Using 8.10)"
date: 2008-11-30
forum: General Help
---

### Post by Arghoslent on 2008-11-30
Hi I use Windows XP a bit and have 4 drives on that. One is my OS drive and the rest are for various other things. I recently installed 7.10 and then upgraded to 8.04 and then eventually to 8.10  and when Ubuntu starts I see the 4 windows drives on my desktop. How can I make a single drive disapper so that I don't screw up my windows OS partion 
Thanx

---

### Post by 2hot6ft2 on 2008-12-01
one way would be to right click on it and unmount it but that would only last until a reboot. Another more permanent way would be to remove it from the fstab file that way it wont auto-mount when you boot.
In a terminal type code:
sudo gedit /etc/fstab
just delete the line (it may be 2 lines) that is/are pointing to your windows drive.
Save and close, then reboot.
Then it wont automatically mount it when you boot up but you will still see it under places and can mount it whenever you want to.

Be very careful with the fstab file as you can make your computer stop working if you mess it up.

And then there's this way to just hide them from the desktop which is what I was looking for. [http://ubuntuforums.org/showthread.php?p=6290826#post6290826](http://ubuntuforums.org/showthread.php?p=6290826#post6290826)

---

### Post by 2hot6ft2 on 2008-12-01
I'm running ultimate edition and drive icons don't show up on my desktop they show up on the left in nautilus as you can see here the 36.7 is my windows drive
[ATTACH]94915[/ATTACH]

---

