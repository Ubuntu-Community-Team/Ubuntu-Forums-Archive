---
title: "files deleted, but i get no free space!"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by Ocxic on 2006-01-09
i recently deleted a bunch of files/folders from my main drive that i was using for storage. the folders were all in the root of the drive (ie: /Movies, /Music....)
all totaling about 110GB of data, now i clicked onto move to trash, but nothing ever went tino my trash, this files are no longer on my hard drive, or so nautilus (and the terminal) says, but there was no space cleared on the drive, i still only have 20GB left, when i should have around 100GB after deleting thos files/folders what gives?

---

### Post by super on 2006-01-09
try running nautilus as root [FONT="Courier New"]'gksudo nautilus --no-desktop --browser[/FONT]' then check the trash for root '/root/.Trash' (you need to select 'show hidden files' from the view menu in nautilus.) if the files are there then just delete them again.

you can also gain some space by cleaning the apt-get cache if you install a lot of software from synaptic. '[FONT="Courier New"]sudo apt-get clean[/FONT]'

---

