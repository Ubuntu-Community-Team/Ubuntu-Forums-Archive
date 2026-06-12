---
title: "feisty has no eject option"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by Lary Grant on 2007-05-31
I have a SanDisk mp3 player.  When I plug it into the USB port it displays "USB connected" on the mp3 player's LCD and mounts on my computer, which is fine. Under Dapper, when I was finished with it, I was able to right-click it and select Eject.  That would cause all the buffers to be flushed (the computer would display "writing buffers" for a few seconds) to the mp3 player and the LCD on the mp3 player to stop displaying "USB connected".  However, in Feisty, when I right-click on the mp3 player, I have an "unmount" option instead of "eject".  When I do "unmount", the icon disappears from the desktop, but the "writing buffers" window on the computer never comes up and the mp3 player continues to display "USB connected" on its LCD.  That seems to mean the buffers are not being flushed.

What can I do to get back the Dapper "eject" capability?

---

### Post by MikeDX on 2007-05-31
I use feisty, but the unmount option does write the cache to disk. 

From a terminal, try sudo umount -a, see if that forces the unmount. 

As for the eject... its a mystery!

---

### Post by coffeecat on 2007-05-31
Find out where the mp3 player has been mounted to. Let's assume this is /media/SanDisk. Open a terminal and do:

```
eject /media/SanDisk
```If that works you can set up a permanent little utility on the desktop by right-clicking anywhere on the desktop (I'm assuming you're using gnome), selecting Create Launcher and putting that command in the command field. You can select your own icon if you don't like the default purple executable one.

Having a permanent eject icon on the desktop is not ideal, but will serve you unless someone comes up with a better idea/solution.

Having said all that I would have thought that unmount would flush all the buffers.

---

