---
title: "Help with Xorg and Graphical progblems"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by NK-Magi on 2008-02-17
I recently installed 7.10 on my laptop and was loving it fine messing with different applications and setups till I found that direct rendering was working properly and Cedega was saying that my 3d abilities were off.  

From that, I thought that Ubuntu was just running off a generic driver and I looked up the graphics chip in my HP Pavilion ze5155 and found it was a ATi M6LY.  So I went on and found Envy and gave it a shot installing 8.28.8 ATi drivers on it and preceded to restart.

Thats where the problem began.  From there I found out it corrupted the settings in my xorg.conf and I found the reconfigure command via Google and gave it a shot.  The problem is though, when I run it, every other line is out of focus just like if the card was artifacting and I cannot read any of the settings to change it.  Also another problem is when I log in I have to press enter till I notice text since for some reason the prompt is being covered up by a black of the monitor, as if the resolution I can see is horribly small and the text expands beyond it.

I'm able to get to the partition via the Live CD and yet even by restoring the xorg.conf via a backup in the folder, I still have problems.  Anyone know any solutions or any way to get a basic xorg.conf that might let me get into GNOME and run the reconfigure again where its not corrupted?

Edit: Bah, can't fix the title.

---

### Post by NK-Magi on 2008-02-17
Whew, never mind.  Fixed it by going into the Live CD and copying and replacing the xorg.conf off the temporary files of the CD to the main partition.

---

