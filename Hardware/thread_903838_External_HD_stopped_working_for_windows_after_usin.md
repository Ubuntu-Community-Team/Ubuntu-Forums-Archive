---
title: "External HD stopped working for windows after using Ubuntu."
date: 2008-08-28
forum: Hardware
---

### Post by lyznx on 2008-08-28
FootNotes: Hard drive worked for Windows and Ubuntu, but stopped working for Windows. Still works for Ubuntu. I need it to work for Windows again.
Please read...



 I hope this is the right place to put this, if not, please let me know if there is a better place to get a response.
 
 I have a couple of Maxtor external hard drives, I swear by these things, They are the best things I have. I have bought a couple over the years.
 
 Well, I finally made the switch from Windows Vista to Ubuntu. I set it up as a dual boot, because there are some things I just know and like better on Windows, such as Nero.
 
 After I switched to Ubuntu I didnt go back to Windows for a week or 2, but i have to burn some DVDs so i went back. All was fine.
 A couple of weeks later I went back to burn some more DVDs, all of a sudden, Windows cannot access the HD.
 Whats up?

 I thought I lost all my data on the drive, but I switched back over to Ubuntu and upon starting, it started doing this Disc Check thing, and then it recognized the drive. And all my files are there and working.
  

 I know it has to have something to do with Ubuntu. I have been using these things for years across XP and Vista, with absolutely no problem.

Note: the Hard drives are and always have been in NTFS.


 I am really linux retarded, so i could really use some help.
  I have saved alot of stuff on the hard drive while using Ubuntu, could the way it saves the files, make windows not recognize the whole drive?

 Please Help.
 
 Thanks, LyZnx

---

### Post by arch0njw on 2008-08-29
Have you tried...
1. with the computer off, disconnect the drive (I'm assuming it is USB)
2. turn on the comptuer
3. boot into Windows
4. connect the drive to the computer

Maybe that will jiggle the device discovery process...

---

### Post by ChimpofDOOM on 2008-08-29
1.  Are they USB drives and are they powered from the USB?  Or external power supply?

2. Do you boot up with the external drives plugged into the PC?

---

### Post by lyznx on 2008-08-29
> **arch0njw said:**
> Have you tried...
1. with the computer off, disconnect the drive (I'm assuming it is USB)
2. turn on the comptuer
3. boot into Windows
4. connect the drive to the computer

Maybe that will jiggle the device discovery process...

I believe i have tryed this. I will do it again.


 and ChimpofDOOM,
 They are USB.

And yes, the harddrives remain plugged in 24/7

---

### Post by lyznx on 2008-08-29
> **arch0njw said:**
> Have you tried...
1. with the computer off, disconnect the drive (I'm assuming it is USB)
2. turn on the comptuer
3. boot into Windows
4. connect the drive to the computer

Maybe that will jiggle the device discovery process...

Didnt work....

---

### Post by arch0njw on 2008-08-29
Very curious.  In Windows, if you go to "Start | Programs | Accessories | System Tools | System Information" and select "Storage / Drives" What drives are listed?

Subsequently, if you go to disk defragmenter, what drives are listed?

Out of curiosity, what is the drive?  Make, model?

Have you completely powered the drive off and tried reconnecting it when in Windows?

---

### Post by lyznx on 2008-08-31
> **arch0njw said:**
> Very curious.  In Windows, if you go to "Start | Programs | Accessories | System Tools | System Information" and select "Storage / Drives" What drives are listed?

Subsequently, if you go to disk defragmenter, what drives are listed?

Out of curiosity, what is the drive?  Make, model?

Have you completely powered the drive off and tried reconnecting it when in Windows?

Ok sry for the delay.
 Here is the deal.
 The drive letter is "G:\" as you are about to see.
 
 The drive does show up, but it wont let me access it.

 Now when i unplug it, start windows, then plug it back in, I get this message,
 "You need to format drive G before using it."
 
But the drive is visible.
 and when I go to "My Computer" to access it. I get this message,
 "G:\ is not accessible. The file or directory is corrupted and unreadable."

 What the heck...   grrrrrr...
 Obviously it isnt corrupted, because Ubuntu reads it find. I swear it must have something to do with the different file systems, i just dont know anything about it.
  Thanks for the assistance so far.
 I sure am hoping that somebody can help me out.
 lyZnx

 PS: Make: Maxtor
     Model: Maxtor one touch 3

---

### Post by chadridesabike on 2008-08-31
There might be something wrong with the way its trying to mount, to reset try this:

In ubuntu, unmount the drive:
umount /dev/(name of drive)

Then, enter this:
sudo mount -t ntfs-3g /dev/(drive location) /media/disk -o force

drive location might be sdb1 or sdb2, etc.

This resets the mount point.  From here, restart the computer into vista and it should be able to mount it.

---

### Post by arch0njw on 2008-08-31
What has me really curious here is that I have used external drives interchangeable with Windows XP and Kubuntu.  I have had...

1. 40GB (fat32)
2. 160 GB (fat32)
3. 250GB (ntfs)
4. 500GB (ntfs)
5. 500GB (100GB NTFS, 400GB ext3)

I have mounted the first 4 with USB and the last with eSATA.  The only time I ever experienced a problem, I tried to hotswap a drive from USB to Firewire; that was a sad lesson in "not smart".

Have you tried a driver update?  I searched around for a bit, and there appears to be some issues with the Maxtor OneTouch 3 and 4 with Vista.  Do you have a Win XP machine you can connect the drive to?  That might help confirm this.

I might not have the answer off-the-cuff, but I'm not going to give up yet!  :-)

---

### Post by lyznx on 2008-08-31
Ok. I just pulled the HD off of my vista machine, and plugged it into my xp machine. AND IT WORKED!
 Then I plugged it back into this machine when Ubuntu was running, and Ubuntu said that it couldnt mount the drive. Once I restarted, Ubuntu mounted it, and it worked fine automatically.

 Now, just to be sure, I reinstalled the Maxtor Drivers. On every machine I have used these things on (like 4 different machines) I never installed the drivers off of the cd, it always just worked. Including in Ubuntu. So, I was starting to think that this was the solution, becuase it was taking so long to install and think. but.... Nope.
 I did the restart in vista, and it didnt work.

 
 Chadridesabike I have to admit, I am very afraid about doing all that code you are talking about. One of my biggest turn-offs about linux is all the code. And i dont think im ready for that.
 I just know I am oging to mess it up.
 Do you really feel that would work?

Thanks again.
 anxiously awaiting more replies.
lyZnx

---

### Post by lyznx on 2008-08-31
> **arch0njw said:**
> What has me really curious here is that I have used external drives interchangeable with Windows XP and Kubuntu.  I have had...

1. 40GB (fat32)
2. 160 GB (fat32)
3. 250GB (ntfs)
4. 500GB (ntfs)
5. 500GB (100GB NTFS, 400GB ext3)

I have mounted the first 4 with USB and the last with eSATA.  The only time I ever experienced a problem, I tried to hotswap a drive from USB to Firewire; that was a sad lesson in "not smart".

Have you tried a driver update?  I searched around for a bit, and there appears to be some issues with the Maxtor OneTouch 3 and 4 with Vista.  Do you have a Win XP machine you can connect the drive to?  That might help confirm this.

I might not have the answer off-the-cuff, but I'm not going to give up yet!  :-)

Just to clarify. It is a 500 gb. i dont know if that would matter.
 And also, I have been using this thing on crappy Vista for over a year, and never had a prob.

 I hate to even register to another Windows forum, but maybe I should be putting the burden on them, instead of the Ubuntu community, since it is Windows that seems to be having the problem.
 I just figured since it only happened right after i installed Ubuntu, that maybe it was to blame. But im thinking not now.
 I honestly dont see how Ubuntu could cross over and do anything to confuse windows *VISTA   and just VISTA. Since it didnt do anything to the xp machine, it probably isnt anything to do with file system.

---

### Post by lyznx on 2008-08-31
I sure hope double posting isnt against the rules here.
 I am not trying to post whore.
 Anyways, I have already tried Maxtorblast. this doesnt do jack for me.
Chkdisk doesnt do jack.
I have done "Safely remove hardware" to see if that would jolt anything with a fresh install.
I did a restore to a date where it worked (about 2 weeks ago) 
I Deleted the device through the device manager. This didnt help.
Even tried a diff port. nope/

There can only be 2 things;
First, There is a virus on it, But it doesnt affect windows xp, just vista. 
Second, Vista must be holding some type of info on it, like a mac address or something, not allowing it to porperly refresh.

I think the later may be more probable.
Does anyone know where info about a particular device may be held, and how to erase it?
I believe that if I did this, It should finnally be able to access it, like xp and Ubuntu

---

### Post by in-dust-rial on 2008-08-31
just to notice:
while reading through reviews i often read, that maxtors die after they are overheated!
that is a common problem to a lot of external drives!
(the price loweres the quality, here)
so dont use it 24/7 if you dont have to, and be sure to have a upright position, so the warm air can circulate!

my western digital mybook was internaly glued! and through heat (without moving it) there was a defective contact!

imho try to avoid 7200 turns per second if the disk is not cooled!

thanks

---

### Post by lyznx on 2008-08-31
> **in-dust-rial said:**
> just to notice:
while reading through reviews i often read, that maxtors die after they are overheated!
that is a common problem to a lot of external drives!
(the price loweres the quality, here)
so dont use it 24/7 if you dont have to, and be sure to have a upright position, so the warm air can circulate!

my western digital mybook was internaly glued! and through heat (without moving it) there was a defective contact!

imho try to avoid 7200 turns per second if the disk is not cooled!

thanks
That Bites about your western digital.
 But my HD still works FANTASTICALLY. Just not for Vista.
  I ownder if what chadridesabike said about the whole hard drive mounting thing is a key.
 But not for Ubuntu, as I said, it works in Ubuntu. But maybe I need to somehow unmount it in Vista.
 I guess i have some more googling to do. Mounting probably doesnt work the way i think. Im sure that if you unplug the device, it UNMOUNTS.
 There has to be some type of information that Vista is holding onto that it causing it not to work.
 I feel like a creep for continuing to post about what is obviously a vista problem on an Ubuntu forum.
 
 I do have another question though. If it is a virus like i was saying in a previous post. 
 Could I run a Virus cleaner FROM Ubuntu>? like AVG. If i do that i might have to get into that WINE thing, and there is more Googling.
 WHY CANT ANYTHING BE SIMPLE.!?

---

### Post by computerjunkie on 2008-08-31
avg makes a native client for ubuntu. just fire up synaptic and type "avg". there is also clam + gui (klamav) and a few others. This isnt a virus problem though. I have seen this on vista. DO NOT let is scan the drive just click "continue anyway" and the drive will work fine. Just a vista quirk from what I've seen. If anyone has more information about this or can correct me if I'm wrong, please let me know.

---

### Post by lyznx on 2008-08-31
> **computerjunkie said:**
> avg makes a native client for ubuntu. just fire up synaptic and type "avg". there is also clam + gui (klamav) and a few others. This isnt a virus problem though. I have seen this on vista. DO NOT let is scan the drive just click "continue anyway" and the drive will work fine. Just a vista quirk from what I've seen. If anyone has more information about this or can correct me if I'm wrong, please let me know.

What do you mean "do not let it scan"
 Are you talking about chkdsk?
 Because if you are. I bypass it everytime now, still to no avail.

---

### Post by lyznx on 2008-08-31
Late breaking Update.
 
 Im so mad now.
 I know that I said the filesystem was NTFS, because it WAS. somewhere along the line it changed to RAW. So now i have to find a way to reverse this, or make  vista see raw.

 I still dont understand why XP can see it but not Vista.
 
 Could using the drive with Ubuntu caused the file system to change to RAW, or is this just a timing coincidense(sP)??
 I hope not, because assuming i get this fixed, i wouldnt want it to happen again.
   Back to google.

---

### Post by lyznx on 2008-08-31
There are NO simple programs or patches to make vista see RAW.
 I HATE WINDOWS. EVer heard of Backward Compatability???

 I will have to reformat the drive. And attempt to restore the NTFS partition table (or whatever) will most likely result in losing data.
Unfortuanatly, the whole problem is that I have nowhere to back all this data up to. I have 6 drives all filled to the rim, and no free space. This particular drive has over 450 GBs. 
 I will have to wait and purchase another harddrive later, use linux to retrieve my data, and reformat the disk. 
 I have been working on this problem for about 10 hours today, and this is the final solution. and it involves spending money.
 
 This topic can be closed or deleted. W/E.

 Thanks for the help Guys.

---

### Post by ChimpofDOOM on 2008-09-01
Ubuntu wouldnt of changed the format over to RAW, and sorry for my late response, but RL business and all that.

I'm not 100% sure how vista works, mainly due to me refusing to even let it near my PC's. But after some manic googling..

(in Vista)
Run the check disk with the Repair option
Though it generally requires opening the Command Line Interface and typing in the CHKDSK/r on the affected HDD. The exact string will be in the help files and generally speaking you need to reboot and the repair is run on the restart.

See if that makes any sense to you, best back up the data on ubuntu first, not 100% sure what that will do.

Good luck
Chimp

---

