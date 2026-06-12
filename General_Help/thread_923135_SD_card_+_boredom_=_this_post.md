---
title: "SD card + boredom = this post"
date: 2008-09-18
forum: General Help
---

### Post by EvilRobotDrew on 2008-09-18
Can i have an SD card mounted without having an icon on the desktop?

i have a laptop with Hardy, a built-in SD card reader, and a brand new 2gb SD card gathering dust. my plan is to use this card as an emergency backup, i use this laptop for everything school related (all of my notes, assignments, papers, etc), i have a script written that copies everything important over to the card (i am anal about backups, but i have broken 2 linux installs and NUMEROUS windows installs, i like to tinker and don't always know what the hell i am doing). because i plan to keep this card in 24/7, and i don't plan to pull data off it, i don't need the icon on my desktop and it is starting to annoy me.

secondly, besides a CYA backup of my school stuff, what cool things could i do with this card? i tried making it a swap partition, but that made no difference to my laptop's performance and seems like a stupid idea.

---

### Post by ajmorris on 2008-09-18
hi there,
There are a couple of ways you can stop the SD card appearing on the desktop... the first (assumes you use gnome), is probably not what you want, as it stops all media from appearing on your gnome desktop, however, to do it, open up gconf-editor as root, and navigate to apps --> nautilus --> desktop, and uncheck 'volumes_visible'. (requires an X restart to take effect) The second method, is to open up /etc/fstab and change/add an entry for the SD device, to mount to somewhere other than /media (i.e. /mnt) as if i remember correctly, only devices mounted to /media will appear on your desktop.

As for other cool things to do with your SD card... i dunno really, the turning it into extra SWAP, as you say, will not give you any added, noticable performance, and you can do this with a file created on your hard disk at any rate...

AJ

---

### Post by EvilRobotDrew on 2008-09-18
it took a while, but this line:

/dev/mmcblk0p1 /mnt/microSD vfat utf8,rw,gid=46,umask=007 0 0

added to my /etc/fstab removed the icon from my desktop, and now a window pop up and annoy me when i plug the card in.

---

