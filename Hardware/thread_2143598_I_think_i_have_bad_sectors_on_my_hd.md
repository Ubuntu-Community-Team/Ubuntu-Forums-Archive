---
title: "I think i have bad sectors on my hd"
date: 2013-05-09
forum: Hardware
---

### Post by komrad3006 on 2013-05-09
i have been having problems install any OS on this laptop. it is a dell inspiron 3520, i would like to know if there is a bootable tool i can use to defrag the disk, it has linux-mint 14 on it now but i had u.studio on it before and wireless issues so i thought i would try to mint out. anyways i was going to put studio back on but when i booted into mint this morning it took forever to load and said someting about not reading the /tmp and then when i went to click on logout a error poped up and would not have the menu show up. 

so i stuck in my usb with studio and went into gparted to see if there is someway to use that and i got this error.
[[IMG]http://i1351.photobucket.com/albums/p794/Komrad3006/hderror_zpscbc37999.png[/IMG]]("http://s1351.photobucket.com/user/Komrad3006/media/hderror_zpscbc37999.png.html")

edit: another ss

[[IMG]http://i1351.photobucket.com/albums/p794/Komrad3006/gparted_zps4c0754de.png[/IMG]]("http://s1351.photobucket.com/user/Komrad3006/media/gparted_zps4c0754de.png.html")

---

### Post by slickymaster on 2013-05-09
Maybe this can help you:

[http://askubuntu.com/questions/21101/how-do-i-fix-the-gparted-message-error-while-reading-block-at-sector-xxx](http://askubuntu.com/questions/21101/how-do-i-fix-the-gparted-message-error-while-reading-block-at-sector-xxx)

---

### Post by ahallubuntu on 2013-05-09
~

---

### Post by afz12 on 2013-05-09
I wonder if komrad3006 has data that needs to be recovered?  Thanks for your suggestion ahallubuntu - I'll make a live USB stick in case I need to do the same in future.

Also, I doubt if defragging will help as this only reorganizing existing data but doesn't repair anything. Even Windows disk-check, I think, only fixes operating system errors but doesn't do much else. Unfortunately, notebook drives are not as easy to analyse as a standard PC as their drive is difficult to remove and connect to via a different machine.

Perhaps a computer service shop could take the hard drive and run-check-fix it on any specialised equipment they have? For example, shops that sell USB drives often say they can offer to try and fix their products (or replace if in warranty). I doubt that many will support notebook drive recovery but a computer service centre might.

If there is no data recovery required, then I agree - ditch it as replacement drives are cheap enough (and a good opportunity to purchase a much larger version - I swapped out a 320 GB drive on an older machine with a 500 GB upgrade for example)

---

### Post by slickymaster on 2013-05-10
Back up all your important data and run the disk utility and click the SMART diagnostics. Run the long self test, and when that finishes, look at the values of the following attributes:
```
Offline_Uncorrectable Current_Pending_Sector Reallocated_Sector_Ct
```
If the uncorrectable count is non zero, or the reallocated or pending counts are more than a few, you need to replace the drive. If there are only a few pending, then you can attempt to repair them. First you need to identify the number of the bad sector. The badblocks utility can be used for this. Then you can use ```
hdparm --read-sector
``` to try reading from it to make sure you have the right one, and then ```
hdparm --write-sector
``` to try and rewrite the sector with zeros. Repeat for all bad sectors.

---

### Post by komrad3006 on 2013-05-10
> **ahallubuntu said:**
> You can install GSmartControl on any Ubuntu live USB or live CD as long as you are also connected to the internet.  Then, check the S.M.A.R.T. Attributes tab and see which if any lines are highlighted in pink or red.  The Parted Magic Linux distro has GSmartControl already built-in - but they call it "disk health."

If you have pending sector errors or hundreds of reallocated sectors, the disk is probably junk and needs to be replaced.

I did install GSmartControl and here is what is says:  
"Cannot retrieve SMART data"
Device open failed, or device did not return an IDENTIFY DEVICE structure.

i think i got it work once in linux mint though and there was alot of red peices of the circle graph. think that means its bad?

> **afz12 said:**
> I wonder if komrad3006 has data that needs to be recovered?  Thanks for your suggestion ahallubuntu - I'll make a live USB stick in case I need to do the same in future.

Also, I doubt if defragging will help as this only reorganizing existing data but doesn't repair anything. Even Windows disk-check, I think, only fixes operating system errors but doesn't do much else. Unfortunately, notebook drives are not as easy to analyse as a standard PC as their drive is difficult to remove and connect to via a different machine.

Perhaps a computer service shop could take the hard drive and run-check-fix it on any specialised equipment they have? For example, shops that sell USB drives often say they can offer to try and fix their products (or replace if in warranty). I doubt that many will support notebook drive recovery but a computer service centre might.

If there is no data recovery required, then I agree - ditch it as replacement drives are cheap enough (and a good opportunity to purchase a much larger version - I swapped out a 320 GB drive on an older machine with a 500 GB upgrade for example)

I have no data that need recovered, im just trying to not buy a new HD unless i know that is what absolutely wrong with it. but my gut is telling me to replace the hd and problem solved, was thinking about buying [this one from newegg.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136856") I really dont want to spend money to have a computer shop around here check it.

> **slickymaster said:**
> Back up all your important data and run the disk utility and click the SMART diagnostics. Run the long self test, and when that finishes, look at the values of the following attributes:
```
Offline_Uncorrectable Current_Pending_Sector Reallocated_Sector_Ct
```
If the uncorrectable count is non zero, or the reallocated or pending counts are more than a few, you need to replace the drive. If there are only a few pending, then you can attempt to repair them. First you need to identify the number of the bad sector. The badblocks utility can be used for this. Then you can use ```
hdparm --read-sector
``` to try reading from it to make sure you have the right one, and then ```
hdparm --write-sector
``` to try and rewrite the sector with zeros. Repeat for all bad sectors.

I have no data that needs backed up and i have ran Dban 2.2.7 twice already and at the end it even has an error code. and when i do happen to get studio installed, i turn it off and the next day i get all the same errors again.

i did run those codes you said and here is what i get.

```
Offline_Uncorrectable Current_Pending_Sector Reallocated_Sector_Ct
```
came up command not found

hdparm --read-sector
> read-sector: bad/missing sector value
hdparm --write-sector
> write-sector: bad/missing sector value

should i just scrounge up some cash and buy a new hd?  i have even tried to install the original windows 8 (yuck) OS and it dont even find my hd.

---

### Post by slickymaster on 2013-05-10
Well, there's something else you can try, don't give up on your drive just now.

Get a Ubuntu LiveDVD and boot your computer from it, when asked whether you want to 'Try Ubuntu' or 'Install Ubuntu' select 'Try Ubuntu' and when you see the Ubuntu desktop navigate to System -> Administration -> Gparted and disable the swap partition (in other words, "swapoff") and note down on a paper the name of your corrupted drive.
Open a terminal window and run the command ```
sudo badblocks -sv -b 512 <device-name>
``` where <device-name> is name of your device you previously wrote down. After a long time waiting, the result is a list of numbers which are the corrupted sectors.
Run the command ```
sudo dd if=<device-name> of=/dev/null bs=512 count=1 skip=<sector>
``` where <sector> is the first number given by the previous command.
Repeat the previous point for each number.
To check if your rescue succeeded, run again the command ```
sudo badblocks -sv -b 512 <device-name>
``` If all went well, it should give you, after a long while, no number.

---

### Post by komrad3006 on 2013-05-10
i will try that again, but it locked up my laptop last night at about 89% was what it said half way up on the terminal as it locked up when i tried it. so i will give it another go, and let you know.  maybe if i turn on the power settings and try it again it might help

---

### Post by komrad3006 on 2013-05-11
well, i let it go over night thinking it would be done when i woke up.  I turned off the settings that turned off the screen but i guess it doesnt want to listen. so now its runing through all the numbers still but the whole computer is slow responding, if i move the mouse it barely moves, but anyways i have seen at least 20 of this code below in at atleast 10 minutes.

```
391846044 40.12% Done 10:16:32 elapsed. (391846044/0/0 errors)
```

and before i went to bed i watched it for about 5 minutes and seen atleast 20 quickly scoot up the terminal, i only can see what it says now cuz of how lagy the laptop is.

---

### Post by ahallubuntu on 2013-05-11
~

---

### Post by komrad3006 on 2013-05-12
> **ahallubuntu said:**
> There is no "circle graph" in GSmartControl.  You must have been using something else.

Sometimes GSmartControl (which is just a graphical front end to the command line utility "smartctl" - part of smartmontools) has trouble accessing USB hard drives.  You said this was an internal laptop drive, right?  Is it possible that error message was for an attached drive?  I've run GSmartControl on many desktops and laptops, and it's very rare that it cannot access the internal S.M.A.R.T. data on an internal drive - unless the drive is almost or completely dead.

I wouldn't waste a second myself running any other tool before I find a way to look at the current S.M.A.R.T. attributes of your internal laptop drive.  Once you get it to work, you can see the attributes instantaneously - it's not running any test, just looking up the status of the drive.  There are ten to fifteen S.M.A.R.T. Attribute lines it will bring up and (in GSmartControl they will be highlighted in pink or red if they are "problem" lines).  You can also simply try the command line version (already installed if you installed GSmartControl) and type this in a terminal:

```
sudo smartctl -a /dev/sda
```

assuming your drive is on sda.  Look for the RAW value for Pending Sector Count and Reallocated Sectors.  If greater than 0, they could indicate serious problems with the drive.

****

---

### Post by komrad3006 on 2013-05-12
> **ahallubuntu said:**
> There is no "circle graph" in GSmartControl.  You must have been using something else.

Sometimes GSmartControl (which is just a graphical front end to the command line utility "smartctl" - part of smartmontools) has trouble accessing USB hard drives.  You said this was an internal laptop drive, right?  Is it possible that error message was for an attached drive?  I've run GSmartControl on many desktops and laptops, and it's very rare that it cannot access the internal S.M.A.R.T. data on an internal drive - unless the drive is almost or completely dead.

I wouldn't waste a second myself running any other tool before I find a way to look at the current S.M.A.R.T. attributes of your internal laptop drive.  Once you get it to work, you can see the attributes instantaneously - it's not running any test, just looking up the status of the drive.  There are ten to fifteen S.M.A.R.T. Attribute lines it will bring up and (in GSmartControl they will be highlighted in pink or red if they are "problem" lines).  You can also simply try the command line version (already installed if you installed GSmartControl) and type this in a terminal:

```
sudo smartctl -a /dev/sda
```

assuming your drive is on sda.  Look for the RAW value for Pending Sector Count and Reallocated Sectors.  If greater than 0, they could indicate serious problems with the drive.

Sometimes when i boot my Laptop i go to boot otptions so i can choose boot from usb, most of the time it does not read my hd, but when it did read it again i installed GSmartControl and took these  screenshots.  Also when i let it boot like normal it says to boot linux mint 14 but then nothing ever happens?

****Edit**** I noticed that i mistyped the code in terminal but when i do type in in correctly i get the same exact message as the last screenshot, sorry.

when it did not read my hd
[[IMG]http://i1351.photobucket.com/albums/p794/Komrad3006/gsmart_zpsa72233c3.png[/IMG]]("http://s1351.photobucket.com/user/Komrad3006/media/gsmart_zpsa72233c3.png.html")

then when it did read hd i took this one   
[[IMG]http://i1351.photobucket.com/albums/p794/Komrad3006/gsmart2_zpse4e61d9d.png[/IMG]]("http://s1351.photobucket.com/user/Komrad3006/media/gsmart2_zpse4e61d9d.png.html")

then this one of the details
[[IMG]http://i1351.photobucket.com/albums/p794/Komrad3006/gsmart3_zps3f51fa25.png[/IMG]]("http://s1351.photobucket.com/user/Komrad3006/media/gsmart3_zps3f51fa25.png.html")

---

### Post by komrad3006 on 2013-05-13
Ok, i found a 160gig hard in an old aspire one netbook, installed into my laptop and have not hand any problems for the last 24 hours. guess my hd was my issue.  thanks for hleping me diagnose my problem though.

---

