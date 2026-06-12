---
title: "non-bootable ISO"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by jameschaucer on 2009-05-22
I've downloaded the ubuntu desktop ISO (v9.x) and burned it onto a CD. My computer wouldn't boot off of it. 

I did a little more reading and found that all the necessary files weren't on the CD, just the ISO. The HOWTO very nicely explained that that was an indicator of an invalid CD; it even showed what should be on it. 

I opened the ISO and found all those pesky missing files. So, I burned that entire directory onto the CD and... my computer wouldn't boot off of it.

I took the ubuntu repair CD that came with my ubuntu mini laptop from Dell and tried booting off of that; it worked. 

So, my computer is capable of booting off of a properly built CD but, apparently, I'm missing how to build one properly. 

I've finally broken down and ordered a free CD from the site. I just wanted to let you know that there is some little issue with the ISO download.

---

### Post by Sef on 2009-05-22
1) Did you burn the iso as an iso?

2) Did you burn the iso at 4x or less?

3) Did you md5sum the download?

---

### Post by jameschaucer on 2009-05-22
1) I do not know how to 'burn as an ISO' so, no, I didn't. I did a drag and drop this last time when I used my ubuntu laptop to try and burn it.  So maybe if I try the command-line version of the burn command I can get it to work. I'll give it a try tomorrow. 

2) No. I'll use a slow speed next time

3) No. I'll do that too.

Thanks for the tips. We'll see what happens.

---

### Post by pricetech on 2009-05-22
To burn an ISO you'll need to open your burner software first.  Look for a menu option / command like "Burn Image", "Create disk from Image", or something along those lines.  When you do, your burner software will allow you to browse for different types of images.  Browse to the ISO you downloaded and select it.  Drag and Drop will definitely not do it.

---

### Post by Str1pe on 2009-07-08
> **pricetech said:**
> To burn an ISO you'll need to open your burner software first.  Look for a menu option / command like "Burn Image", "Create disk from Image", or something along those lines.  When you do, your burner software will allow you to browse for different types of images.  Browse to the ISO you downloaded and select it.  Drag and Drop will definitely not do it.
This answered my question. Thanks, mate.

I don't regularly burn CDs and the distinction between simply burning the file to CD and searching for a disk image to burn to CD held me up for a while.

For Nero Express 5.5.10.44 users that means looking for the option, "Disk Image or Saved Project" when it asks, "What would you like to burn?" In the "Open" popup select the All files (*.*) setting to find the ISO file you downloaded. Add that and burn.

\\:D/ Sometimes the simplest things....

---

