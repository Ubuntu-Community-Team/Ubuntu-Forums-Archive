---
title: "[SOLVED] Help! Denied Access"
date: 2008-09-22
forum: General Help
---

### Post by Leslier69 on 2008-09-22
Hi. I had xp home installed on my 250GB hard-drive. It crashed after i resized my 1TB hard-drive and i still have files on the 250GB that i need. I resized my 1TB to a 200GB, and a 700GB and installed XP Home on the 200GB Partition in hopes of being able to move my files from the original 250 to the 700. Unfortunatly, for some reason, The 'Matt' folder in My Documents is 'access denied' so i tried booting into linux with the live CD. When i tried to move files around, it said i couldnt due to write protection. I tried 'sudo nautilus' to get permission but it did not work. Please help. I can give more info on problem if asked. I tired using Knoppix, did not help either

---

### Post by matt79 on 2008-09-22
I do not know if this will help a windows folder but you might want to try chmod.
The best way to do this if you are just trying to access the folder is 
"sudo chmod 777 directory"
Just take the quotes off and put the path of the folder in where it says directory.

---

### Post by Leslier69 on 2008-09-22
hey, i tried that. i typed "sudo chmod 777 /media/700" and it says the target has been changed. but for some reason it still wont work. *frustration* i am moving files from the 250GB onto a flash drive, rebooting into windows, and pasting them there, rebooting and goin back to ubuntu, putting more on it and so on, but i have over 200GB of stuff to move and i only have a 2GB flash, arg.

---

### Post by matt79 on 2008-09-23
> **Leslier69 said:**
> hey, i tried that. i typed "sudo chmod 777 /media/700" and it says the target has been changed. but for some reason it still wont work. *frustration* i am moving files from the 250GB onto a flash drive, rebooting into windows, and pasting them there, rebooting and goin back to ubuntu, putting more on it and so on, but i have over 200GB of stuff to move and i only have a 2GB flash, arg.

Do it through a network file transfer. It will go much faster. But you should not have to do it at all. If you did the chmod try the chown.
"sudo chown username /directory" just take the quotes off and put you user name and the file path in.

---

### Post by Leslier69 on 2008-09-23
hey, that worked. thanks a lot. much quicker

---

### Post by matt79 on 2008-09-24
Great  :D

---

