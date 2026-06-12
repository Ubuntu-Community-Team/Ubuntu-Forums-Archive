---
title: "Rebuilding a dead hard drive in RAID1 array?"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by lozzd on 2005-05-24
Hey,

I have a RAID1 software array running with two identical hard drives. I (please forgive me) accidently disconnected one of the pair (don't ask) whilst the server was running ( [img]http://ubuntuforums.org/images/smilies/eusa_whistle.gif[/img] ) so that became failed, obviously. 
Now, i rebooted with the drive plugged in, hoping it would beautifully repair itself in accordance to the other one. Much to my delight, this message appeared: (or something to this effect... I don't have a photographic memory unfortunately)
md: Backround rebuild started on drive....
md: started with 1 of 2 drives running

and then after a short 3 second or so pause, i get the message "stopping tasks failed (1 remains)" and the system stops booting.

Eventually I got the system to boot by simply unplugging the drive completly. so the array is currently running with only 1 drive. 
Even if I could've worked out how to start the rebuild in linux, I now cannot get in with the drive connected (thus available to linux) so it seems unless i can correct this strange "stopping tasks failed" message, i'm gonna be running with 1 drive permemantly. 
I did a search, which returned only one result, which i checked and added to the GRUB (by using the E to edit the commands) (acpi=off) but this didnt help at all.

Any suggestions? 

Thanks in advance!

Laurie  ](*,)

---

