---
title: "Can't read/write to creative mp3 player, please help !!"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by Strev_123 on 2006-02-06
Ok, I have a Creative Zen Micro 5GB player (latest firmware etc...) connnected via USB, I can see it in the device manager list as "Nomad Jukebox Zen Micro MP3 Player". I've typed ```
dmesg | tail
``` in terminal and got this back ```
[4297225.870000] usb 1-2.3: new full speed USB device using uhci_hcd and address 5

``` umong other things which I assume had nothing to do with the player. Could I mount the player as a USB HDD, if so how can I do this, I'm new to ubuntu and the only thing stopping me deleting my winME partition is getting hardware to work.

---

### Post by wondering_jew on 2006-02-06
hmmmm i'm not exactly sure how to solve it completely but i think i might be able to point you in the right direction.

If it shows up in the device manager it should also show up in disk manager
(from gnome panel menus System--> Administration-->Disks)

My guess is that your mp3 player will be towards the bottom of the list of hard disks just above your cd/dvd rom drives, select and click on the partitions tab
this will list any partitions on the mp3 player and allow you to change the Acess Path  (mount point) and enable access to the disk itself.

Just as a side note the device will probably show up as /dev/sda or /dev/sdb

hope something i said helps

---

### Post by Strev_123 on 2006-02-07
Thanks, but it doesn't show in the list of disks... I've found a guide to get it running under Gnomad2 @ [http://gnomad2.sourceforge.net](http://gnomad2.sourceforge.net) but it's complete gibberish to me :/

Any *easy* step by step guides GREATLY appreciated :)

---

