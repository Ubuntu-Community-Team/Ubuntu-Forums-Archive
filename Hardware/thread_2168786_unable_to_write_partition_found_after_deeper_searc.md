---
title: "unable to write partition found after deeper search in testdisk"
date: 2013-08-19
forum: Hardware
---

### Post by mandeep3 on 2013-08-19
Hey guys,

I am a newbie to ubuntu but have been searching and going through a lot of ubuntu forums since last few days, here is my problem:

My laptop was installed with windows 7 and I wanted to remove windows and install ubuntu and still keep all my personal data intact. But accidentally I selected the option to remove windows and then install ubuntu so it started to remove all files on my 500GB hard disk, I quickly (within 2 seconds) removed the pen drive hoping it was only deleting files and only a few things would have been deleted. But, now my laptop won't boot and shows a black screen with a white cursor blinking:(.

I booted from the ubuntu live CD only to find that my data was gone, and the partition table too.
After going through a lot of forums I found that testdisk might help my case, so I used testdisk and analysed my harddisk.
Quick search doesn't shows the partitions on my hard disk but on deeper search, it finds all three partitions and the files but there is no write option in deep search unlike the quick search. I have been hitting my head against the wall since last few days.  I just need to get my data off that hard disk anyhow because i don't have a backup :( .

Can someone now please help and tell me how to restore the partitions found in the deep search option in testdisk or at least a way to recover my data (pictures).  Any help would be appreciated, Thank you so ****ing much in advance. :popcorn::KS

---

### Post by Mark Phelps on 2013-08-19
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by mandeep3 on 2013-08-19
Hello Mark,
Thanks for the quick response, but actually my laptop is still under warranty and if I want my laptop to be opened, the warranty seal will be teared hence voiding the warranty, thats the reason I did'nt go for windows recovery options. Is there a way through which I can get my essential data off the disk through live CD in my case??  Thanks again for the quick reply...   I am still looking for some way to write the partitions found after deeper search in testdisk.

Thank you :)

---

### Post by mandeep3 on 2013-08-19
OK! I have now found one probable way to write the partitions found in deeper search option while using testdisk.

When deeper search shows the list of probable partitions on the disk, use UP and DOWN key to select the partition, then press p to list the files, if you can recognise your files in that partition then this partition is the one to be saved, so now press 'q' to come back to the list of all partitions. 
Now using LEFT or RIGHT key, we can change the type of the original partitions from D(deleted) to L(logical).
 Now press 'q' and if you are pretty much sure that these are all of your partitions you are looking for, then select [WRITE] and press enter.  
This will most probably re-write the partitions and data will be accesible.

I found all my partitions and data listed while using above method but I stopped at the point where testdisk gave me the option to write the partitions because I just wanted to confirm weather am I going to get my data back or making the situation even worse.   Any help regarding this is appreciated, Thank you!  :)

---

### Post by nemesis045 on 2013-11-07
Hi Mandeep, did this work for you? Were you able to write your partitions and recover lost data? I have the same issue and would like to know if that worked.

---

