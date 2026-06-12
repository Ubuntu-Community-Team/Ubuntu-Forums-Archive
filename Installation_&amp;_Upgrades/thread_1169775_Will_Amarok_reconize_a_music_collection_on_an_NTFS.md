---
title: "Will Amarok reconize a music collection on an NTFS mount?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by T1Oracle on 2009-05-25
When I was using 64 bit Kubuntu 8.10 I had no problems getting Amarok to update from my music collection on my NTFS Vista partition.  Now that I upgraded to Kubuntu 9 I can't even find that folder in the Amarok settings.  I can get to it manually from Dolphin, but to access it for the first I have enter my password.

I have played music in Amarok from my NTFS folder, but I can't find a way to get it to add that folder to my collection so that I can use all of the features of Amarok to browse my library of files and select the music I want.  Without this, Amarok is more of a nuisance than a benefit.

---

### Post by taurus on 2009-05-25
Did you remember to mount that ntfs partition first before you tried to access it?

---

### Post by T1Oracle on 2009-05-25
Yes.
> **T1Oracle said:**
> I have played music in Amarok from my NTFS folder

---

### Post by T1Oracle on 2009-05-25
Great, so I manage to get banshee to browse that folder but then it randomly decides to quit playing.  So I close it and try again and it doesn't work.  But if I go to file and double click it Amarok starts up and plays it.

So, Amarok won't go into my mounted NTFS drive and Banshee will for awhile until it decides to die. Sigh...

---

### Post by T1Oracle on 2009-05-31
I fixed it.  I just did "sudo apt-get install gksu" in the terminal, then I ran the "NTFS Configuration Tool" (just type NTFS in the KDE menu search), and set the mount point as "windows" which was auto corrected to "/media/windows".

---

