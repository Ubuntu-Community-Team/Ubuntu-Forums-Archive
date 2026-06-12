---
title: "Adding XP to my Ubuntu MBR - Please Help"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by SableSlayer on 2009-06-07
Ok heres the story. To start with I had 3 partitions. The First a Vista 40gb, the second is a file partion with 400GB or so and the third with XP on a 25gb partion. I Installed Ubuntu over the Vista 40gb partion and added a 10gb swap out of the 40gb. Now i am trying to add XP to the grub MBR and have had no luck. I have a Sata drive and so far every tutorial has been for a IDE. 

Any Help would be greatly appreciated! Thank you :)

---

### Post by shifty_powers on 2009-06-07
have you tried following [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

i know it is for recovering ubuntu, but it will reinstall grub, which should also add xp to it as well...

---

### Post by presence1960 on 2009-06-07
run in terminal>  sudo fdisk -l BTW that is a lowercase L. Post the output here. We'll see what you have and then edit the menu.lst file so windows will be on your GRUB menu options.

---

