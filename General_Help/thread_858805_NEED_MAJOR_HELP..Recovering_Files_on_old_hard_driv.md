---
title: "NEED MAJOR HELP..Recovering Files on old hard drive"
date: 2008-07-13
forum: General Help
---

### Post by chrisk9 on 2008-07-13
Hey I'm gonna make this as drawn out as I can....
I recently got engaged on the 4th of july and obviously that is a very important day in my life, and I had a lot of pictures from that day on my computer and my fiance & I planned on using the pictures for a slideshow at the reception....then my friend came over to use my computer when i was away a couple days ago..and he said something was wrong with it and he needed to reformat it and he wanted to try this Ubuntu stuff...
so anyway long story short...

I had bought  this computer brand new a few months ago formatted with Windows Vista, and it is now reformatted with this ubuntu thing on it..._I NEED TO GET MY PICTURES/ INFO FROM THE OLD HARD DRIVE AFTER IT WAS REFORMATTED ONTO THIS. IS THERE ANY WAY I CAN DO IT?? (For Free??) _

I took the computer up to Best Buy and asked the people at GeekSquad and they said i could have the files recovered but they would need to send it to another state or country and the STARTING Cost would be $550. I do not have that kind of money to spend, so it would be extremely helpful if there were a way to fix this for free, or cheap.

Any Help Is Appreciated!!!

---

### Post by mikewhatever on 2008-07-13
You can try using photorec from a CD.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by chrisk9 on 2008-07-14
Okay that didnt work...i have found free recovery programs but it downloads them as a   ".exe" file and my computer now can not open that...

:(

---

### Post by Valsodar on 2008-07-14
Hmm this is a tough one. Its the fact that you have formated your harddrive (I dont know if ubuntu does a quick format or a full one). My suggestion is to:
1. stop using the hard drive you want to recover files from. (Get a new one if possible, and install windows/ubuntu on it) (at lest as big as your one that you need to recover files from)
2. If using ubuntu, install photorec from the repositories (or TestDisk)
3. Make your harddrive (one to be recovered from) into a secondary drive or a usb external drive (you can make a hard drive very easy in an usb external for about 20$).
4. Run photorec or other recovery programs and save all the recovered files on you primary harddrive (not the one you need to recover from)

This will come to about 100-150$ and the chances for success are decreasing as you keep using your data harddrive you need to recover from. (Also I managed to run photorec on an external drive, with some very impressive results)

Good luck on recovering your data

---

### Post by timcredible on 2008-07-14
the short answer is no, the partition was reformatted and any data has had it's pointers to where it is on the drive removed.  now, is the data still there?  well.......... maybe.  i say maybe because reformatting doesn't actually overwrite the data on the disk, but removes all pointers, creates new sectors, etc.  but in order to retrieve it, you need something that can look at every sector and try to figure out what sectors go with other sectors to make a file.  well, the other tough part is that whatever windows-based program you try, it won't work with an ext3 partition format, so you have to re-format back to ntfs just to attempt anything.  

what best buy was saying is that they can send it off to someplace that specializes in manually scouring each sector on the drive and try to piece the files together, and yes, this is expensive because it's extremely time consuming.

---

### Post by chrisk9 on 2008-07-15
Alright thank you guys for your help/suggestions...i have another harddrive the same size and i will try it...if not then my friend agreed to pay half to recover the files since he did it... 
so anyway thank you!

---

### Post by Taxman415a on 2008-07-15
Ok, in case you haven't already told him, your friend is an idiot for reformatting a drive without asking you what was on it and backing it up. But are you sure he didn't just shrink the windows partition and save your data? Boot from a livecd and run sudo fdisk -l (you may need to specify the device such as sudo fdisk -l /dev/sda1) from a command line and see what the output shows about your hardrive. Maybe your data is still there.

Even if he did really reformat, as the others explained there are free tools that can be used in Ubuntu to recover files. There's a decent chance you can get some back.

---

