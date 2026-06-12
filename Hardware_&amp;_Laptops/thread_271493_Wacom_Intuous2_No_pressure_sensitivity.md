---
title: "Wacom Intuous2: No pressure sensitivity"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by Wilmer Huffman on 2006-10-04
I've been through every thread on this board that had the word "wacom" in it, but I have yet to run across someone else with a similar problem as mine.

I have a USB Intuous2 tablet, and if I have it plugged in when I boot the computer I can get the relevant gibberish out of wacdump or xxd as described [Here]("http://www.ubuntuforums.org/showthread.php?t=25151") for device /dev/input/wacom like it should be, but then Gimp will tell me that there are "No extended input devices detected".  The tablet works wonderfully as a mouse, all my buttons work and everything, but there's no pressure sensitivity in either Gimp or Maya.

If I plug in the tablet *after* X starts, Gimp will recognize that I have an extended input device, but still has no pressure sensitivity.  At this point if I check wacdump on /dev/input/wacom there will be no response.  None of the event#'s respond either, even though the tablet is still functioning as a mouse.

Any ideas? :-?

---

### Post by Ryupower on 2006-11-11
*BUMP*

I'm bumping because it doesn't work with me either! The difference being that I'm using a Graphire4 tablet and the Gimp won't find an imput device whether I plug it in before starting x or not.

---

### Post by petepan on 2006-11-16
same here.. hm.. this sux.](*,) maybe ill change back to windows. :(

---

### Post by Jiawen on 2006-12-08
I'm having the same problem. 

The tablet's relative mode is also very lacking -- when I try to go to the bottom of the screen, I usually have to make about four attempts before the relative mode actually works right.

---

### Post by nihlton on 2006-12-10
rats.  this answers my question.

next question >> are there any plans to properly support tablets in the future?  Id love to dump windows but I *NEEEED* my tablet.  :(

---

