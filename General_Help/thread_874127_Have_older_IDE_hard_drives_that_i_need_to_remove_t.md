---
title: "Have older IDE hard drives that i need to remove the data from - how?"
date: 2008-07-29
forum: General Help
---

### Post by PsychedelicWonders on 2008-07-29
Alright I have 1 IDE cable/port on my mobo.

Right now it is hooked up to my cd/dvd rom drive.

Now I have my dvd drive listed as 1st boot when starting up.

So do I just wait until the the computer is loaded up and then disconnect the dvd drive and plug my old hard drives in and do some type of file transfer/copy?

Or should i go into the bios and take the dvd rom off of 1st boot and have the old hdd installed when I turn it on?

Are there any IDE cables that just have 2 ports instead of 3?

the extra one will never be used and is just takign up space...

But that gives me an idea... can I just plug my old hdd into the extra port on the ide cable and give them power and transfer/copy the files onto my new hdd that way?

---

### Post by mrhobz on 2008-07-29
> **PsychedelicWonders said:**
> Alright I have 1 IDE cable/port on my mobo.

Right now it is hooked up to my cd/dvd rom drive.

Now I have my dvd drive listed as 1st boot when starting up.

So do I just wait until the the computer is loaded up and then disconnect the dvd drive and plug my old hard drives in and do some type of file transfer/copy?

Or should i go into the bios and take the dvd rom off of 1st boot and have the old hdd installed when I turn it on?

Are there any IDE cables that just have 2 ports instead of 3?

the extra one will never be used and is just takign up space...

But that gives me an idea... can I just plug my old hdd into the extra port on the ide cable and give them power and transfer/copy the files onto my new hdd that way?

Your IDE port should support 2 channels.

A) Go buy a dual channel IDE cable.
B) Disconnect cdrom and replace it with the hdd.
C) DO NOT swap them out with the machine on.

---

### Post by PsychedelicWonders on 2008-07-29
youre saying the port on my mobo shoudl allow me to hook up 2 devices (a.k.a. "channels" as you call them?)

I guess im confused... cant I leave my cdrom drive hooked up and put the hdd on the 3rd ide port?

Not sure if the one I have is dual channel... i just bought it... here it it...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812123180](http://www.newegg.com/Product/Product.aspx?Item=N82E16812123180)

Or do I have to completely remove the cdrom from the chain?

---

### Post by coffeecat on 2008-07-29
Can you buy, beg, borrow or - er - borrow a USB hard drive case for IDE drives? Then you wouldn't have to muck around inside the computer case, and the drive partitions would be automounted when you plug the USB cable in.

---

### Post by coffeecat on 2008-07-29
> **PsychedelicWonders said:**
> Not sure if the one I have is dual channel... i just bought it... here it it...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812123180](http://www.newegg.com/Product/Product.aspx?Item=N82E16812123180)



That's a SATA cable. You won't be able to plug that into an IDE drive. An IDE cable is a wide ribbon cable (usually) and has one plug at one end to go into the motherboard, one about two-thirds of the way along for the slave drive, and one at the other end for the master drive.

**Edit**: reread your post. You should be able to plug the master plug into the hard drive, and the slave plug into the optical drive. You could try it the other way round. I presume your main hard drive is a SATA one.

---

### Post by PsychedelicWonders on 2008-07-29
shot im sorry, I put the wrong link... I have the ide cable.

cant i just plug the hdd into the slave port and extract the data by means of file transfer that way?

or do I have to have the hdd plugged into the master plug?

Yeah my new hard drives are all sata.

---

### Post by flytripper on 2008-07-29
All ide ports support 2 drives

on a lighter note , you could stare at it like Chuck Norris till it gives you the information you need.

---

### Post by flytripper on 2008-07-29
yes you can. just make sure you set the master/slave jumpers

---

### Post by PsychedelicWonders on 2008-07-29
> **flytripper said:**
> yes you can. just make sure you set the master/slave jumpers

What do you mean to set the jumpers?

---

### Post by tonez2600 on 2008-07-29
Try this website for info on jumper settings. [http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm](http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm)

The label on top of the hard drive will usually tell you which pins to put the plastic jumper on to set master and slave. Hope this helps.

---

### Post by flytripper on 2008-07-29
sorry i missed the part where you said you had sata...

just look on the drives and make sure theyre set to slave, to make sure they dont boot instead of your sata drive

---

### Post by PsychedelicWonders on 2008-07-29
hmm.  seems easy enough.  

thanks guys.

And then once I get this all set up... what is the "my computer" in ubuntu that allows you to view all drives?

---

### Post by tonez2600 on 2008-07-29
> **PsychedelicWonders said:**
> hmm.  seems easy enough.  

thanks guys.

And then once I get this all set up... what is the "my computer" in ubuntu that allows you to view all drives?

It should show you the drives under the "places" tab in the upper left hand corner.  Between "accessories" and "system". I believe, I am not at home right now, but i will double check when i get off work.

---

### Post by flytripper on 2008-07-29
above is right but its applications system


in any case click on places.

---

### Post by PsychedelicWonders on 2008-07-29
thanks man.

Whats the quickest form of copy transfer from one hdd to another?

just drag and drop?

---

### Post by flytripper on 2008-07-29
the only way to fly

---

### Post by PsychedelicWonders on 2008-07-30
I found the "computer" tab and went into it.

it had a bunch of drives listed that I didnt have, didnt list the hard drives that I had hooked up via sata, and only showed some of the files on these old hard drives I was trying to transfer data from.

now I went into all the folders I could find and didnt see any of the files, or the main file I was looking for.

What am I doing wrong?

Why arent my sata drives being recongnized in this computer tab and why cant I view all the files on these old hard drives?

Right now I'm only running 7.10 - working on trying to upgrade to 8.04, but no internet connection where that machine is.

---

### Post by PsychedelicWonders on 2008-07-31
bump

---

### Post by derrick81787 on 2008-07-31
There's always the command line way.  Maybe less user-friendly, but much more powerful and dependable (not to mention easier to explain).

Here are the steps:
[LIST]
[*]Create a temporary folder to be used as the mount point for the old drive
[*]mount the old drive
[*]copy the files from the drive
[*]Turn off the computer and take out the drive
[/LIST]

First, we need to find the old drive, though.  Can you copy and paste the results of the following command?

```
sudo fdisk -l
```

Once we find the drive, we'll be on our way in no time.

- Derrick

---

### Post by PsychedelicWonders on 2008-07-31
> **derrick81787 said:**
> There's always the command line way.  Maybe less user-friendly, but much more powerful and dependable (not to mention easier to explain).

Here are the steps:
[LIST]
[*]Create a temporary folder to be used as the mount point for the old drive
[*]mount the old drive
[*]copy the files from the drive
[*]Turn off the computer and take out the drive
[/LIST]



What do you mean "the mount point" for the old drive?

When you then say mount the old drive.. you mean plug it in to the system and start it up?

I guess I'm just really confused as to this process on how to access and copy files from one hdd to another.

---

### Post by fragos on 2008-07-31
$10 gets you an IDE to USB adapter. Much simpler.

---

### Post by PsychedelicWonders on 2008-07-31
that would be easier, but costs extra money and this is just a one time deal.

Plus i'd like to know how to work the system from the inside out.

---

### Post by jocko on 2008-07-31
> **PsychedelicWonders said:**
> What do you mean "the mount point" for the old drive?

When you then say mount the old drive.. you mean plug it in to the system and start it up?

I guess I'm just really confused as to this process on how to access and copy files from one hdd to another.

I'm pretty sure he meant for you to first post the output of:```
fdisk -l
```, and then he (or anyone else on the forums) would tell you how to create the mount point and mount the drive.

"Mount" means to make the drive accessible (to the os, which then will make it accessible to you), and the mount point is the folder where the content of the drive will be accessible.
But to mount the drive, you need to know some things about it, which you can get from the output of "fdisk -l"...

> **derrick81787 said:**
> There's always the command line way.  Maybe less user-friendly, but much more powerful and dependable (not to mention easier to explain).

Here are the steps:
[LIST]
[*]Create a temporary folder to be used as the mount point for the old drive
[*]mount the old drive
[*]copy the files from the drive
[*]Turn off the computer and take out the drive
[/LIST]

[COLOR=Blue] First, we need to find the old drive, though.  Can you copy and paste the results of the following command?

[/COLOR] [COLOR=Blue] ```
sudo fdisk -l
```Once we find the drive, we'll be on our way in no time.[/COLOR]

- Derrick

---

### Post by derrick81787 on 2008-08-01
> **PsychedelicWonders said:**
> What do you mean "the mount point" for the old drive?

When you then say mount the old drive.. you mean plug it in to the system and start it up?

I guess I'm just really confused as to this process on how to access and copy files from one hdd to another.

I guess I should have explained better.  The very first step before you do anything is to plug the drive into the system and then start it up.  I thought the drive was already plugged into the system.

After the drive is plugged in and you have booted the system, then you should run "sudo fdisk -l" and post the results here.  This command will give us the information we need to mount the drive.

Jocko was right about what I meant in my last post.  "Mounting" is the term used for making the drive available to use by the OS and the user.  You've probably already noticed that when you plug in the drive and turn on your computer, you computer just acts as if the drive doesn't exist.  That's because it isn't mounted yet.  Mounting the drive makes it to where you can navigate to a certain folder (called mount point) and view the contents of the disk.  For example, the mount point for your main drive is "/" because going there shows you every file on the drive.

You can specify any folder you want to use as the mount point though.  Therefore, we can create a folder on your desktop, mount the drive to that folder, and then when you open the folder, all the files on your other disk will be there. Then, we can just copy the files from that folder to some other place on your system, shut down the computer, physically unplug the drive from your computer, and you're done.  The files will be copied over and everything is good to go.

All you need to worry about right now, though, is plugging in the drive, starting up your system, running "sudo fdisk -l" and posting the output of that command to the forums.  We'll walk you through the steps from there.

- Derrick

---

### Post by PsychedelicWonders on 2008-08-14
alright I finally got everything up and running to where I am ready to do this.

sorta.

Here is the situation, the only IDE cable I have in my machine is for my cd/rom and I have it at boot up it checks this first.

Now I only have a wireless keyboard, not a ps/2 in order to change bios to do boot up on something different.  (my f10 button is not working yet.)

Can I start the computer up like normal and just unplug the cd/rom and plug in the hdd to access the files after ubuntu starts up?

---

### Post by fragos on 2008-08-14
By default Ubuntu checks for new hardware on every boot. Unpluging the CD and plugging in the disk should work fine -- powered down of course.

---

### Post by PsychedelicWonders on 2008-08-14
but wont it try and boot off of these ide hdds I am plugging in if I have my bios set to the ide as 1st boot instead of my normal sata OS hdd??

---

### Post by PsychedelicWonders on 2008-08-14
alright guys, its hooked up through ide, its a 40g drive and here are the results...

psychedelicwonders@JohnnyScience:~$ sudo fdisk -l
[sudo] password for psychedelicwonders: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4463        9327    39078112+   7  HPFS/NTFS
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3               1        4462    35840983+  83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003c9ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77b896d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081    c  W95 FAT32 (LBA)
psychedelicwonders@JohnnyScience:~$ 

What do I do next?

Ideally I want to save all of the media onto the 500g drive, but I dont know exactly what folders everything is in on the 40g, so I need to be able to access all files and then drag and drop to a 500g icon for easy transfer.

thanks.

---

### Post by PsychedelicWonders on 2008-08-15
bump

---

### Post by derrick81787 on 2008-08-15
> **PsychedelicWonders said:**
> alright guys, its hooked up through ide, its a 40g drive and here are the results...

psychedelicwonders@JohnnyScience:~$ sudo fdisk -l
[sudo] password for psychedelicwonders: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4463        9327    39078112+   7  HPFS/NTFS
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3               1        4462    35840983+  83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003c9ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77b896d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081    c  W95 FAT32 (LBA)
psychedelicwonders@JohnnyScience:~$ 

What do I do next?

Ideally I want to save all of the media onto the 500g drive, but I dont know exactly what folders everything is in on the 40g, so I need to be able to access all files and then drag and drop to a 500g icon for easy transfer.

thanks.

Okay, first open up a terminal.  Now, we're going to create a folder to hold the files, and make them accessible from that folder.  I'm going to call the folder "hd" but you can call it whatever you want.  Here are the commands:

```
mkdir hd
sudo mount /dev/sdc1 hd
```

Now you can open Nautilus, browse to the hd folder, and copy the files to your main drive the exact same way you would copy any other files.

Once the files are copied, just shut down your computer and remove the drive.  Next time you boot up, feel free to delete the "hd" folder.

Let me know if this works.

- Derrick

---

### Post by PsychedelicWonders on 2008-08-16
psychedelicwonders@JohnnyScience:~$ mkdir old hd ****
psychedelicwonders@JohnnyScience:~$ 
bash:: command not found
psychedelicwonders@JohnnyScience:~$ mkdir hd
mkdir: cannot create directory `hd': File exists
psychedelicwonders@JohnnyScience:~$ sudo mount /dev/sdc1 old hd ****
[sudo] password for psychedelicwonders: 
Sorry, try again.
[sudo] password for psychedelicwonders: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
psychedelicwonders@JohnnyScience:~$ 

did i do this right?

is everything all set now?

---

### Post by PsychedelicWonders on 2008-08-16
alright I actually had 2 hard drives to do this to, the first one I didnt find any of the files I was looking for, so I tried the second hdd.

this is what I did...

psychedelicwonders@JohnnyScience:~$ mkdir hd2
psychedelicwonders@JohnnyScience:~$ sudo mount /dev/sdc1 hd2
[sudo] password for psychedelicwonders: 
psychedelicwonders@JohnnyScience:~$ sudo mount /dev/sdc1 hd
psychedelicwonders@JohnnyScience:~$ sudo mount /dev/sdc1 hd2
mount: /dev/sdc1 already mounted or hd2 busy
mount: according to mtab, /dev/sdc1 is mounted on /home/psychedelicwonders/hd2
psychedelicwonders@JohnnyScience:~$ 

but this 2nd 80g hdd doesnt seem to be showing up...

---

### Post by PsychedelicWonders on 2008-08-16
Alright I found the file I was looking for and when I dragged and dropped it to my 500g hdd, it started to work, but then after a few minutes gave me this error...

But it still seems to be copying most of the files.... so how can I tell what files it would not copy?

---

### Post by PsychedelicWonders on 2008-08-16
it seems that when i tried to move my files to my 500g, it didnt allow me because it says I dont have access?

Then it seemed to default and save the files on my desktop which is my 80g.

Does this sound right?

What do I have to do to my 500g so I can drag and drop this main file to store on that hdd?

---

### Post by PsychedelicWonders on 2008-08-16
Alright i checked the properties of the file that saved on my desktop to the original file i dragged and dropped, and the one on my desktop has 3,353 files where the original has 3,354 files.

Is there any easy and quick way to tell what actually didnt transfer?

Still having problems of not being able to drag and drop onto my 500g.

---

### Post by PsychedelicWonders on 2008-08-16
Also, alot of the pictures and files I transfered over seem to have a small lock icon attahed to them at the top right hand corner.

What does this mean, and how do I get rid of them all in one mass way?

---

### Post by fragos on 2008-08-16
> **PsychedelicWonders said:**
> Also, alot of the pictures and files I transfered over seem to have a small lock icon attahed to them at the top right hand corner.

What does this mean, and how do I get rid of them all in one mass way?

It means they are read only. You can change permissions if you need to.

---

### Post by PsychedelicWonders on 2008-08-16
> **fragos said:**
> It means they are read only. You can change permissions if you need to.

Alright, can I change permissions for all of them at once?

Or do I have to do one by one?

Any idea on why my 500g wont let me drag and drop?

---

### Post by fragos on 2008-08-16
Right click a folder, change it's permissions and click the "Apply Permissions to Enclosed Files" button.

My best guess is that the files that won't drag belong to root and you're dragging them to a user folder.

---

### Post by PsychedelicWonders on 2008-08-17
Alright everything is transfered over and those 2 extra hdd are formatted.

Now I want to edit the code to take all history of them out and keep it nice and clean.

I mounted 2 hard drives and created 2 files for them.... what code can I run for you guys to figure out exactly what needs to be edited?

---

### Post by fragos on 2008-08-17
Phyically remove the drives and they wounted be discovered on the next boot. Delete any mount poit folders you may have created.

---

### Post by PsychedelicWonders on 2008-08-17
Alright I removed them, but how do I delete them out of the mount point folders?

---

### Post by fragos on 2008-08-17
I may be wrong but I don't think there's anything else you need to delete. If you made manual changes to /etc/fstab you would want to remove those.

---

### Post by derrick81787 on 2008-08-17
> **PsychedelicWonders said:**
> Alright everything is transfered over and those 2 extra hdd are formatted.

Now I want to edit the code to take all history of them out and keep it nice and clean.

I mounted 2 hard drives and created 2 files for them.... what code can I run for you guys to figure out exactly what needs to be edited?

To remove any trace of what I told you to do, you just have to remove the folder you created.  Everything else should be taken care of.

- Derrick

---

