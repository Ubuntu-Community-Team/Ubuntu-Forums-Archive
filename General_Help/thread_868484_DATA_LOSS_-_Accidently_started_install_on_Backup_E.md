---
title: "DATA LOSS - Accidently started install on Backup Ext Drive - How to Recover?"
date: 2008-07-23
forum: General Help
---

### Post by mikemccoy on 2008-07-23
I just did possibly the absolutely STUPIDEST thing of my life.

It was my first time using Ubuntu, so I used the Live Disc to test it out.  I loved it and wanted to install it on my machine.  I restarted the machine, it booted to the Ubuntu Install.  I followed through the prompts and got to this part:

For the partitioning section, it gave me the list of options with the default radio button selected for the very first option - I think divide the install into two partitions - free space and the actual OS.  I changed the option and clicked "Use the Full Disc" and started the install.  It got to 5% when I looked at the front of my machine and realized that it was using my EXTERNAL BACKUP DRIVE! I immediately turned off the External drive, the install threw a prompt saying that something happened, and I restarted the machine.

I am back in the Live Test of Ubuntu and it does not see the external USB drive at all.  I have also plugged it into a windows machine to see if anything comes up, and nothing comes up in My Computer.  I checked the Disc Manager of the Management portion of Windows, and it sees the drive, but there is no active partition.  I think it MAY have split it into two partitions, not entirely sure.

Anyway - from what I am guessing, when the install started, it stripped the MBR which from what I am thinking, renders the rest of the data on the drive useless? I'm not sure - thats why I'm here.  I DESPERATELY Need access back to this data.  I have everything on there - all pictures, documents, music, business items, school items, everything.

I feel so incredibly stupid right now, words cannot describe my feelings or loss.  And for being an IT person, this was the biggest mistake I've ever done.

ANY SUGGESTIONS WILL BE GREAT! Is there any backup program that I can pre-boot to to try and access the data, or any special software tools? Anything at all!

Respectfully,

---

### Post by the_real_fourthdimension on 2008-07-23
Hmm...  
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
This will work for most of your data...  hopefully all of it.  However, I think it contains pirated software, so you might want to check it out before using/downloading it.
Here's an freeware alternative:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
Both have recovery tools.  Good luck!

---

### Post by mikemccoy on 2008-07-23
Thank you, I'm going to check both out ASAP.  I'll post results if possible.

Do you know if these would still work even if the MBR is stripped? Just curious before I try it - wont be able to until tomorrow afternoon.

Even if I have to pay for software, I'd do it - I've lost close to 300GB of data, and I'd say that's worth every penny of it.

Thanks! Keep the replies coming!

---

### Post by the_real_fourthdimension on 2008-07-23
> **mikemccoy said:**
> Thank you, I'm going to check both out ASAP.  I'll post results if possible.

Do you know if these would still work even if the MBR is stripped? Just curious before I try it - wont be able to until tomorrow afternoon.

Even if I have to pay for software, I'd do it - I've lost close to 300GB of data, and I'd say that's worth every penny of it.

Thanks! Keep the replies coming!

Yes, since you're booting from the CD.  Actually, HBCD (and possibly UBCD) has tools to restore the MBR. :)  It might take some time to get used to the tools, but they should have what you need.

---

### Post by todlangweilig on 2008-07-24
Perhaps you should take it to someone that specializes in data recovery? You might be able to recover all of your data, not just the parts that weren't overwritten. Even if the MBR was the only thing overwritten, I think it wouldn't take them long or cost so much for them to figure that out. If you're considering this, I would do it before writing to the disk. I don't know much about this, it's just something to consider. Unfortunately I don't think it's cheap, but if you need the data badly enough...

Is this a backup drive, or the original copy of your data? The real question is, do you have another copy of the data? If that disk WAS the only copy, now would be a good time to consider backing up whatever data you manage to recover, before the next time comes.

Best of luck

---

### Post by mikemccoy on 2008-07-24
> **todlangweilig said:**
> Perhaps you should take it to someone that specializes in data recovery? You might be able to recover all of your data, not just the parts that weren't overwritten. Even if the MBR was the only thing overwritten, I think it wouldn't take them long or cost so much for them to figure that out. If you're considering this, I would do it before writing to the disk. I don't know much about this, it's just something to consider. Unfortunately I don't think it's cheap, but if you need the data badly enough...

Is this a backup drive, or the original copy of your data? The real question is, do you have another copy of the data? If that disk WAS the only copy, now would be a good time to consider backing up whatever data you manage to recover, before the next time comes.

Best of luck

What happened was is that this drive was my backup drive when I was using Windows.  But I had to do a wipe/reload Windows because of corruption the other day, so this was the only drive that has all of my data on it.  Now with this drive "broken" - I'm without any data.

Good suggestions though.  I'm going to get ready to try this stuff.  My only thoughts is that with the HBCD it is a DOS boot - will my USB drive even work in DOS, I dont think so.  If needed I'll take apart the external drive and hook it up to and IDE cable.

---

### Post by mikemccoy on 2008-07-24
UPDATE

I searched around and found similar situation that happened to another guy ([http://ubuntuforums.org/showthread.php?t=560209](http://ubuntuforums.org/showthread.php?t=560209)).  I started using testdisk but I was nervous making any actual changes to it, so I decided not to do that.  I decided to try to use PhotoRec ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) which comes packaged with TestDisk.

I had to install Windows back onto my computer in order to move data back to it.  Unfortunately, now my SATA RAID 0 STRIPE isn't working which would equal 300GB.  My external is 320 but not all of it is used.  So, what I was forced to do is transfer as much as I can to one of the 150GB HDs.  This is simply a test, if this works well, then I can gauge how much data I can recover.  I know that I'm going to have to restart this entire process eventually.

I think I might have a bad SATA drive which is preventing me from setting up my SATA RAID 0 STRIPE.  Before any of this, Windows was saying Delayed Write Error repeatidly.  Then when I went to reinstall Windows with the proper RAID drivers, it said that one of the disks cannot be used and to check for possible h/w problem.  With further testing, I can determine if it is a bad drive.  If it is, then I may just go get either another SATA large drive to create the array, or just stick with the 1 disc for the operating system and have a 2nd external (which would basically backup my backup) haha.

I'm so paranoid now.  Thoughts about anything?

New question: PhotoRec is able to recover files, but it renames them with random integers - strips the filename away from it.  I have an extremely large MP3 collection, and with random integers - it would be a pain to have to go through and rename each individual one (I dont mind Word Docs, pictures, etc).  But is there a program that can analyze the individual file/song/whatever and rename it with the proper file name?

Any help would be great.  I know this is going to sound weird, but preferably to have a program in Windows that can do all of this, just so I can have everything the way I want it before I officially migrate everything to Ubuntu.

I'll keep this updated.  Thanks again for input.

---

### Post by todlangweilig on 2008-07-24
If there is ID3 tag data on those mp3s, it could probably be used to rename the songs. id3ed plus some shell scripting would seem to work. See the link below for some info on id3ed
[http://tldp.org/HOWTO/MP3-HOWTO-13.html](http://tldp.org/HOWTO/MP3-HOWTO-13.html)

If you're looking for something with gui and on windows, the first two results from google seem promising. I think the rest of the results on the first page are pretty golden too, so give it a look. 
[http://www.google.com/search?hl=en&q=mp3+rename+using+id3](http://www.google.com/search?hl=en&q=mp3+rename+using+id3)

---

### Post by mikemccoy on 2008-07-25
Thanks! I'll look at those when I get a chance.  I woke up today with seeing exactly what I was guessing would happen - it ran out of space so I need to fix this first before I do anything else.

At least I know I was able to recover the majority of my data.  Even though every file is renamed with numbers, at least I know it is there.  I still need to verify that my documents are legit.

---

### Post by Growbag on 2008-07-25
It maybe a bit late now, but here is a really good recovery page.

It is for ReiserFS, but the part about making a backup copy of a damaged drive BEFORE trying to recover it is priceless.

It might be useful for someone else though as it has a lot of other info about data recovery.

And I wish you good luck too :).

[http://www.cgsecurity.org/wiki/ReiserFS_File_Undelete_HOWTO](http://www.cgsecurity.org/wiki/ReiserFS_File_Undelete_HOWTO)

---

### Post by Yannick Le Saint kyncani on 2008-07-25
> **mikemccoy said:**
> At least I know I was able to recover the majority of my data.

Hi mikemccoy, so this would be another photorec's succes story ? I think I'll keep this tool around from now on, just to be safe++.

PS: Best of luck on the recovery process.
PS2: That's why you should keep backup on at least two separate medias and keep them at two separate locations if you can.

---

### Post by mikemccoy on 2008-07-30
Yes this is using photorec.  Unfortunately it cannot copy back the filename which sucks because if your like me that has thousands of almost every file type, then its going to suck for you.  I havent tried the MP3 program that someone posted here earlier, but eventually I will.

I found out that 1 of my 2 drives that make up my RAID array is dead, so I dont have enough space to backup everything.  So I can either get another external drive or get another internal drive for the RAID setup.  Not really sure what I want - to me, RAID is kind of too much work for so many problems that I've had before.  But since I'll eventually be switching to Ubuntu, maybe that will change.

I wonder if there is another free program out there that works like photorec but can pull the filename.  I'm sure there's got to be...

Thanks everyone for your help! Work has been real busy so I havent had time to actually sit down and finish this deal.

---

### Post by Yannick Le Saint kyncani on 2008-07-30
> **mikemccoy said:**
> Not really sure what I want - to me, RAID is kind of too much work for so many problems that I've had before.

I suggest ditching raid altogether unless you can afford very expensive setups.

In many case, you would be better off using additionnal backups for the same price and it would protect your data better.

---

### Post by pacificial on 2008-07-31
Hi to all,

To recover your hard drive, you can use Ubuntu recovery cd. If it doesn't help then use stellar phoenix [Linux recovery]("http://www.data-recovery-linux.com") software which recover your partitions as well as important data and files. Check the preview of recovered data with demo versions.

Thanks

---

### Post by Growbag on 2008-07-31
> **pacificial said:**
> Hi to all,

To recover your hard drive, you can use Ubuntu recovery cd. If it doesn't help then use stellar phoenix [Linux recovery]("http://www.data-recovery-linux.com") software which recover your partitions as well as important data and files. Check the preview of recovered data with demo versions.

Thanks

Handy to have that link, but unfortunately it only runs under the microsoft windows OS.

You would have to buy a license for windows and a new hard disk to install it on first.

Not too bad if your data is extremely important, and money is no concern I guess.

---

### Post by mikemccoy on 2008-07-31
So I downloaded the trial version of VirtualLab and here are my thoughts:

VERY GOOD - keeps the previous file tree AND keeps file names.
VERY BAD - freaking expensive! [https://www.binarybiz.com/vlab/buy/]("https://www.binarybiz.com/vlab/buy/")
Quota Version
  * $40 for 100MB
  * $100 for 1GB
  * $150 for 10GB
Pro Version
  * $200 unlimited - once license.

I think the software itself is very good, but that is incredibly expensive IMO.  I just bought a 500GB drive for $106 just so I can backup my broken external to it, then basically pay another $200+ for this - very expensive mistake, huh?

There HAS to be something else out there that does the same exact thing for either cheaper or free and does a good quality job.  The PhotoRec - yes - I guess it did the job by simply pulling the files, but thats it, and thats bare minimum.  I guess I'm getting very picky, but data is picky - and so is time, and I dont have the time to go through thousands of files just to rename them.

---

### Post by mikemccoy on 2008-07-31
Here are some more reviews about VirtualLab
[http://www.reviewcentre.com/reviews12700.html](http://www.reviewcentre.com/reviews12700.html)

Not sure if I want to try the product with that many bad reviews...

---

### Post by mikemccoy on 2008-08-03
Well, I buckled and DID pay the $200 for the unlimited Professional version of VirtualLab.  I figured, it took 4 hours to recover all of my data, in the proper file structure, and with the file names - all for $50/hour - in my eyes, thats a good deal, and I'm sure the good reliable tech's at GeekSquad would charge probably $400+ for the same exact thing.  Psh.

Anyway.  Hope this is a lesson for others - look before you install, you may be accidentally formatting your BACKUP drive.  

As a review: Although the VirtualLab is expensive up front, I think in the long run it definitely paid off.  I would highly recommend this software to anyone else who needs to use it.  If you dont care about renaming all of your files with 111111.mp3 for thousands of files, then use PhotoRec, but if you want as much of your original data the same exact way it was before, then use this.

Thanks all for your help.

Time to install Ubuntu for real this time.  =)

---

