---
title: "RockBox player mounts, can't write"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by tel3caster on 2007-04-04
I've recently switched to ubuntu and before that I had changed my Cowon Iaudio X5's factory firmware with Rockbox's custom firmware. Rockbox allowed me to read and write on my old Windows box, however when I switched over to Ubuntu, I found that I could read and delete files but I could not copy or create new files to the player at all. Btw, I believe the player is formatted in FAT32 which I believe ubuntu should have no problem writing to because I'm able to write and read on my girlfriend's external harddrive which is also in FAT32. Any help would be appreciated.

---

### Post by tel3caster on 2007-04-04
I'm really desperate, any ideas?

---

### Post by tel3caster on 2007-04-06
Does it help to include that I'm running Edgy Eft?

---

### Post by tom56 on 2007-04-06
If I recall correctly, any FAT32 systems are set to read-only by default to stop you potentially messing up any Windows systems on the machine. Post your /etc/fstab.

---

### Post by strabes on 2007-04-06
You should mount it as writeable. Chmod 667 the /media/PLAYER directory perhaps?

---

### Post by tel3caster on 2007-04-08
I think I worked out a solution. The problem wasn't that it wouldn't let me have write access. In fact, I had full read and write access to all the entire harddrive. However, it wouldn't let drag a folder of music to the player. Oddly enough, I could copy each individual file from the folder to the mp3 player. Any suggestions?

---

### Post by tom56 on 2007-04-09
When you say "wouldn't let me", what do you mean? What did the error say?

---

### Post by aleska on 2007-04-15
I was going to ask the same thing tom56 did.  
When I first tried installing rockbox on my ipod mini, I encountered a problem where I thought I had successfully copying the appropriate files over to the ipod.  Then I'd unplug the ipod from the machine only to find that my changes (files copied over) weren't saved.  
In my case, the answer was simply making sure I unmount, or right click on my ipod device showing on the desktop and select "safely remove".  That was all that was necessary to ensure changes wrote to the device.

---

