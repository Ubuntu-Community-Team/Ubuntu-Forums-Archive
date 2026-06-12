---
title: "Trying to extract audio from CD.  Can't access the drive!"
date: 2008-11-24
forum: General Help
---

### Post by ratdog on 2008-11-24
Hello, 
I'm trying to load my CD collection on to my computer and having difficulty.

Rhythmbox recognizes and plays the CD, but when I try to 'copy to library' it says "Error Copying Track: Access Denied".  It gives me that message as many times as tracks on the disc.  I have to keep clicking close.  
If I try to navigate to the Audio CD under Places, it says... 
"Could not open location 'cdda://scd0/' There was an error launching the default action command associated with this location."
However, if I'm browsing my hard drive and then click on the Audio CD icon on the left, It will open the disc and show me the wav files.

I don't know where to start with this...
Please help.
Thanks

---

### Post by ratdog on 2008-11-24
*Pops head back in the door*

Anyone?

---

### Post by ratdog on 2008-11-26
Any ideas or maybe another suggested program to try?
Thanks!

---

### Post by oldos2er on 2008-11-26
Check System, Administration, Users and Groups, and make sure your user has 'Use CD-ROM drive' privileges.

---

### Post by ratdog on 2008-11-26
Yes, my user does have cd drive privileges.
And the CD will play, just no extraction.

---

### Post by oldos2er on 2008-11-26
Maybe the device cdda://scd0/ is wrong then. Try /dev/cdrom or /dev/cdrom0

---

### Post by ratdog on 2008-11-26
Where would I change this setting?
Remember, Rhythmbox does access and play the disc...

---

### Post by oldos2er on 2008-11-27
I don't use Rhythmbox, but possibly somewhere in Preferences? Sorry I couldn't help you out more.

---

