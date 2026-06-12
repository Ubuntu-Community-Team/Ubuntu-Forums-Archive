---
title: "Partition resizing in ubuntu"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by supasye on 2009-02-25
Hi People, I'm new to ubuntu and i'm switching to it just because windows is getting a bit on my nerves now..

I plan to keep some hard drive space for windows because i am heavy on graphics work and i need to use programs such as 3ds max and photoshop. From what i have read they do not work so well on Ubuntu.

I am trying to use GPart to resize and partition on my hardrive. At the moment there is an exclamation mark on my hard drive and i cannot resize. It says there are bad sectors on the disk etc, im sure many of you have encountered this before, i followed the instructions to run the check disk (three times ive done it already all five stages) and to defragment the hdd. But it doesnt make a difference. The problem persists. 

How can i get around this problem? Is there a program that will allow me to do it inside Windows?
I notice when i defrag my hdd that there are unmovable files towards the end of the disk, i was sondering if this could be the problem even though i dont think it is.. 

its Ubuntu 8.04 btw..

Thanks in advance for your help guys..

---

### Post by Mark Phelps on 2009-02-25
Which version of MS Windows do you need to keep -- Vista or XP?

The tools that work on resizing partitions are different for each.

---

### Post by supasye on 2009-02-25
Hi, 

It's Windows XP Home SP2..

Thanks.

edit: it was preinstalled on the system, not sure if that makes a difference..

---

### Post by Mark Phelps on 2009-02-26
Ok, that's good news because Vista would pose extra problems...

Inside MS windows, Open MyComputer, click on the drive icon, select Tools, and select check for errors (or something like that).  If it prompts to have you specify that for the next boot, click OK.

That will run chkdsk inside of Windows -- and should repair the disk.

If it doesn't, there's the possibility that the drive is failing.

---

### Post by lindsay7 on 2009-02-26
I you do not already know, find out what brand hd it is. Go to there web site and look for diagnostic software to download. When you run the software program it will tell you if you hd is just plain bad.  If it is then you sould very quickly clone you bad drive to a new one asap or it least backup everything that you need and do a clean install of Ubuntu.  If you can clone you old disk to a new one, you could do a dual boot install of just try the live disk ubuntu option to make sure everything works the way you want. You could then do the dual boot or the install where windows would be wiped.  Acronis is good software to do a clonning. You buy and download it online.

---

### Post by supasye on 2009-02-26
thanks gys.

@mark: ive already done chkdsk several times aswel as defrag..

@lindsay: i think my hdd is matshita or something, but what you suggested got me thinking.. if i clone my current 80gb onto a bigger laptop hdd, an then swap them.. would that work? once i do that i guess i can go ahead with the partitioning and ubuntu installation..... right? i dont want to completely remove windows because i need it for my graphics etc..

---

### Post by lindsay7 on 2009-02-26
Yes, I have done that before with Acronis Home Iamge 11. They have a new version call Acronis home 2009. You can load the software on you current drive or use it from the CD. Buy a new bigger hd for you laptop. Just be sure you get the corroct type the older type will be an IDE or parallel or pata. They are all the same type. The newer type are SATA.  You can get a cable adaptor that will connect which ever type in currently in your computer to connect thru a USB port.  They cost from $4 to about $20.  Look at Tiger Direct, or Cables To Go web sites. Or Ebay.  Clone your current hd to the new one using the adapter. Then just put the new hd in you machine.  That is all that it takes.  I would suggest that when you do the cloning that you pick the option to keep the old date and etc, (ie windows and all the files on you old drive) that way if something does not go right you can put the old drive back in the machine and try again.  When you are happy that everything is the way you want it on the new drive, you can reformate the old drive and use it as storage.  You can buy an enclosure for you old (most likely 2.5 inch drive or whatever) for it and you will have a neat little portable back up drive. The encloseures are $10 and up depending on features and brand on Tiger or Newegg.  I just put Ubuntu on one of my computers to run as a dual boot system and the Ubuntu install program will partition the drive to any size you want. One for windows and one for Ubuntu.  It was easy and a lot faster and less complecated than doing a partition and then an install.

---

### Post by supasye on 2009-02-27
Thanks Lindsay,

I've decided that i'm not only going to upgrade my hdd but i'm also going to upgrade my ram. i'll do the ram first and then i'll go ahead and sort out the hdd..

Thanks again, i'll let you know how i get on.. ;)

---

