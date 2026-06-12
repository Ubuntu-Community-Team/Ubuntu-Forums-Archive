---
title: "Upgraded ubuntu, now just memtests"
date: 2008-09-04
forum: General Help
---

### Post by zenithan on 2008-09-04
I work for a PC repair shop as one of the techs. We had someone come in with ubuntu on their machine and was having a few issues with drivers and what not. While it was here since they don't have broadband they asked us to process the ubuntu updates. I hit the update button and let it have it's fun for a good 2hrs until it asked to reboot.

Now it just memtests. Over... and over... and over. Nothing else. grub loads, and the only bloody options are root, memtest, quiet. 

Can someone please help me get this running again. I don't know jack about this OS, second person ever to come in with it.

EDIT: I loaded up their gos recovery cd and looked at the menu.lst file, at the very bottom is just says:

title         Ubuntu 7.10, memtest86+
root          (hd0,0)
kernel        /boot/memtest86+.bin
quiet

---

### Post by porchrat on 2008-09-04
Do you have an ubuntu liveCD?  If so you can reboot with it...mount the harddrive and then edit the /boot/grub/menu.lst file.

However you can't do any of that unless you have the liveCD I'm afraid.

If you have a fast enough connection on another machine with no cap or anything I suppose you could download one that would at least let you boot so you could do something about it.

[http://www.ubuntu.com/GetUbuntu/download]("http://www.ubuntu.com/GetUbuntu/download")

You can get the LiveCD ISO from there but bear in mind the thing is like 700MB

---

### Post by zenithan on 2008-09-04
I have their recovery CD, which boots into ubuntu. I edited the menu.lst file and it only shows an entry for memtest86+.bin, nothing else. (posted above).

---

### Post by porchrat on 2008-09-04
this is what my menu.lst looks like...or at least these are what the parts that are missing look like:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=6922929b-6e62-43c5-b2fb-0b4e1e3a787d ro
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=6922929b-6e62-43c5-b2fb-0b4e1e3a787d ro single
initrd		/initrd.img-2.6.24-19-generic

```

however...before you do that we need to know what the UUID is for there HDD because it won't match mine so please post the ouput of this:

```
sudo blkid
```

You then replace the UUID seen in my menu.lst with the UUID number you see in that ouput

If I were you I would also add "quiet" and "splash" to the end of the line starting with "kernel" (only the line appearing under Ubuntu 8.04.1, kernel 2.6.24-19-generic...not the one under "Recovery Mode"

---

### Post by porchrat on 2008-09-04
They don't dual boot on that machine do they??...if they do the harddrive numbers may differ

---

### Post by zenithan on 2008-09-04
/dev/sdal: UUID="fb917c71-b51c-449e-bd95-6d464bd428b4" SEC_TYPE="ext2" TYPE="ext3"

/dev/sda5: UUID="d8749168-ad64-443b-864e-fa94adcfala7" TYPE="swap"

That was the result of that command. I noticed in the /boot folder there's just a folder for grub and memtest86+.bin Should there be other bin files?

---

### Post by porchrat on 2008-09-04
I also need the ouput of this command...(sorry I'm a little forgetful today)

```
uname -r
```

---

### Post by zenithan on 2008-09-04
2.6.22-14-generic

It's cool, it's early and I'm glad to just be getting help with this. Been trolling the net for hours trying to find a solution.

---

### Post by Bucky Ball on 2008-09-04
Probably wasn't a good idea to offer to update an os you knew nothing about. Totally different to what you are familiar with, probably windoze or mac or both, but will try and help out as this is a real pickle. Your update has removed your kernel entries obviously enough and not replaced the appropriate headers. If it has removed the headers, what else might be missing? Go recovery from the live cd and drop to a shell.

This should get you going. You need to, in a shell '**locate /boot/grub/stage1**'. Go for the 'In the Terminal' section (you don't have a lot of choice):

[https://help.ubuntu.com/community/GrubHowto/#Backup,%20Repairing%20and%20Reinstalling%20GRUB]("https://help.ubuntu.com/community/GrubHowto/#Backup,%20Repairing%20and%20Reinstalling%20GRUB")

Good luck, let us know how you go. :)

---

### Post by zenithan on 2008-09-04
I honestly didn't think much of it, there's an update button, there was some posts online saying the issue the customer was havign was fixed in 8.04. It seemed so innocent so I pressed the update button and let it run. Bloody thing ><

Hell I knew more about it then the customer, they thought it was Vista (no lie).

Hardy.. Hardy when I hit the upgrade button I think it said it was upgrading to 8.04 Hardy. Is there a way I can dig out the kernel number?

EDIt: 

I typed in locate /boot/grub/stage1 into the Terminal on the gos recovery CD (the place I've been getting the other terminal data from) and it says:

locate: warning: database /var/lib/slocate/slocate.db' is more then 8days old

---

### Post by Bucky Ball on 2008-09-04
You sure you didn't hit the *upgrade* button? That would have upgraded it from 7.10 to 8.04 and yes, that takes hours doing it that way (sometimes forever and a day like 7-12 hours, all depending on connection speed). A normal update just updates the *current kernel* (you can do this daily if you like). The security updates on an upgrade like this would have killed a few things.

[http://www.sitefuse.com/f16/t80.html](http://www.sitefuse.com/f16/t80.html)

That helps to explain a bit ...

This should work so you can try the locate instructions from previous post: Try **sudo updatedb** (this will take awhile to run)from this page (just adding stuff as I find it, fascinating, never come across this one before! :))[B]:

[/B][http://agaricdesign.com/locate-commands-database-not-updating-solved](http://agaricdesign.com/locate-commands-database-not-updating-solved)

If that did work, do the **locate /boot/grub/stage1** instructions from before.

---

### Post by egalvan on 2008-09-04
OK, if you are still trying to resolve this, I have an idea...

first, see if the menu.lst~ (back-up copy) has valid entries. 
If so, try replacing the menu.lst and see if it boots ok.
if so, problem solved.
If not, make a copy for later use. The UUID for the drive is needed.


replace the client's drive with a spare from your inventory.
install geos using the client's livecd
or install on a similiar machine

make a copy of the NEW menu.lst

if needed, replace the original drive (client's).
replace the non-working menu.lst with the copy you got from the NEW install.
replace the UUID from the back-up (menu.lst~)


what you are trying to do is generate a good menu.lst


for more on grub, try

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


for more on UUID's, others will have to chime in.

---

### Post by egalvan on 2008-09-04
> **zenithan said:**
> 
H Is there a way I can dig out the kernel number?


How to find out the Kernel version of the Ubuntu release you're using

terse:
```
uname -r
```

supplies more info:
```
uname -a
```

---

### Post by porchrat on 2008-09-04
> **egalvan said:**
> How to find out the Kernel version of the Ubuntu release you're using

terse:
```
uname -r
```

supplies more info:
```
uname -a
```

His kernel entries in /boot are GONE ...he needs to do a recovery... not a nice situation

It isn't the menu.lst...its all the headers etc.

---

### Post by Bucky Ball on 2008-09-04
Excellent idea, Egalvan, and it just might work. As you mention, you will need to change the UUID for the correct one once the good menu.lst is on the client's box (this might take a little trial and error).

I have to go to bed now as getting late here and things to do in the morning but before I do ...

> I honestly didn't think much of itI don't think much of German either but I don't speak or understand it. You are in the position in the shop to throw a box together with a hard drive and a gig of ram, load Hardy 8.04 on and tinker about for a month or two in your spare time. Let me know how you feel about it then. It is not windoze and was never meant to be, but realise that a lot of the people on this forum and linux users in general are *extremely* experienced windoze and mac users who, through frustration and for a million other reasons, have made the change after many years. We dual boot, just use Ubuntu, but one thing is for certain - there are no Gates closing us in and no more expensive Windoze to upgrade. We are part of a thriving open source community and few if any ever return. The software is flexible and free and we can update the OS every night if we really want to and then make it work just the way we want it to.

Please let us know how you went with all this and hope it turns out well. :)

As for the UUID - sudo blkid - but I mentioned that before. :)

---

### Post by zenithan on 2008-09-04
So I gathered enough information to let me make a new menu.lst entry, but it won't let me save the little sob. I'm downloading the livecd thing now, I'm guessing this recovery gos cd is pretty much useless.

---

### Post by egalvan on 2008-09-04
> **porchrat said:**
> 
It isn't the menu.lst...its all the headers etc.

The OP stated:

*I edited the menu.lst file and it only shows an entry for memtest86+.bin, nothing else. (posted above). *

so it MIGHT be that the menu.lst file is the problem.
Trying a known-good menu.lst is a way to check, and should not take too long, and it should not mess up anything else.

I further agree that, if he did an up*grade*, he may have deeper problems.

but lets try the simple things first, no?


"When you hear hoofbeats, think horses, not zebras."

---

### Post by Bucky Ball on 2008-09-04
> won't let me save the little sobDon't forget you need to be root to do a lot of things, thus

**sudo**

before your commands if in doubt. Night all ... zzz :)

---

### Post by porchrat on 2008-09-04
> "When you hear hoofbeats, think horses, not zebras."

I like that.

I had him do a uname -r and a blkid earlier so we should have what we need to create an entry.

---

### Post by porchrat on 2008-09-04
> **zenithan said:**
> So I gathered enough information to let me make a new menu.lst entry, but it won't let me save the little sob. I'm downloading the livecd thing now, I'm guessing this recovery gos cd is pretty much useless.

don't download the liveCD...it won't let you save because you need to type "sudo" in front of the gedit command when you edit the menu.lst as you need to edit it as root.

---

### Post by egalvan on 2008-09-04
> **zenithan said:**
> So I gathered enough information to let me make a new menu.lst entry, but it won't let me save the little sob. I'm downloading the livecd thing now, I'm guessing this recovery gos cd is pretty much useless.

You need to have root privalege to edit menu.lst.

gksudo gedit boot/grub/menu.lst

it will ask for the user's password, and it probably will show no cursor movement.

There are other ways to do this "root" thing.

And remember, it's not Windows, it's different.
As another poster suggested, toss a machine together from discarded parts, and play with it. The specs needed are not high, just try to get at least 512m RAM. Linux is free and full of choices, and you can make money installing and  supporting it... heck, you can even sell copies of it, to folks without broadband. It's a service.

And you have all these nice folks here-abouts to help :)

ErnestG

---

### Post by zenithan on 2008-09-04
> **porchrat said:**
> don't download the liveCD...it won't let you save because you need to type "sudo" in front of the gedit command when you edit the menu.lst as you need to edit it as root.

Oh I didn't realize that's how the command structure worked, that makes sense. Let me try that real quick

EDIT: Typed in that command, got:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authenication failed.

I'm not really mad at ubuntu or anything, I just have nearly zero linux experience so it's all new to me. Just figuring out the command structure is different then the concepts I'm used to.

---

### Post by zenithan on 2008-09-04
I've been unable to find a way to open the menu.lst in such a way that I can edit it. I tried to commands posted but it opens a blank menu.lst not the one that's present.

---

### Post by porchrat on 2008-09-04
if it opens a blank page then you may be misspelling something.

Have you tried copying and pasting a command straight off the forums.

```
gksudo gedit /boot/grub/menu.lst
```

Just copy and paste that and it should work

> Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authenication failed.

Oh I see.  looks like you can't use root permissions...that is going to be a problem

---

### Post by zenithan on 2008-09-04
Actually I figured it out, the file is located at /media/disk/boot/grub not just /boot/grub. That let me edit it, and add all the new line. Here's what I added:


title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro
initrd		/initrd.img-2.6.22-14-generic
quiet

Now I goto load it, and it says file not found. Do I need to put the /media/disk in there too?

---

### Post by porchrat on 2008-09-04
> **zenithan said:**
> Actually I figured it out, the file is located at /media/disk/boot/grub not just /boot/grub. That let me edit it, and add all the new line. Here's what I added:


title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro
initrd		/initrd.img-2.6.22-14-generic
quiet

Now I goto load it, and it says file not found. Do I need to put the /media/disk in there too?

your kernel numbers don't match...change the line starting with kernel to this:

> kernel		/vmlinuz-2.6.22-14-generic root=UUID=fb917c71-b51c-449e-bd95-6d464bd428b4 ro quiet splash

---

### Post by zenithan on 2008-09-04
Oh sorry, was copy and pasting and missed that. On the laptop with ubuntu it's correct. All three numbers are the same.

---

### Post by porchrat on 2008-09-04
can you post the actual error you get?

Unfortunately it sounds like something has happened to the kernel or the headers, but we will keep trying...how long until you have to give it back.

I am really impressed at your determination I wish we had computer repairman like you where I come from

---

### Post by jimv on 2008-09-04
Backup /home folder, reinstall from Hardy cd, and restore files from /home folder backup.

Problem solved.

(Chances are pretty good that if they thought this was Vista, they didn't change much, if anything, on the system that would be lost during a format/reinstall.)

---

### Post by zenithan on 2008-09-04
Let me reboot it to get the exact error:

Error 15: File not found

Press any key to continue...

When you press a key to dumps back to the grub menu (which has my new line and memtest listed)

Hehe I'm trying, I don't like just having to do like /reformat that really sucks for people. 

I used the locate command mentioned and was able to find the initrd file and a initrd bak file. Though I don't know exactly if that's any good or not.

---

### Post by zenithan on 2008-09-04
> **jimv said:**
> Backup /home folder, reinstall from Hardy cd, and restore files from /home folder backup.

Problem solved.

(Chances are pretty good that if they thought this was Vista, they didn't change much, if anything, on the system that would be lost during a format/reinstall.)

Can ths HD be connected to another windows based machine? I thought linux used a different file system format then Ms machines

---

### Post by Bucky Ball on 2008-09-05
menu.lst needs to be in /boot/grub/ not /media/boot/grub. That is where you hard drives and other media lives (mount points for them anyhow - everything is treated as a file including media) and the system won't look there for the menu.lst on boot. 

Error 15: File not found

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

That page explains what is happening there. First, backup your menu.lst:
[B]
sudo cp /media/boot/grub/menu.lst /media/boot/grub/menu.lst_backup

[/B] Then:

**sudo mv /media/boot/grub/menu.lst /boot/grub/menu.lst**

And that should put the menu.lst in the correct directory. Type:

**dir /boot/grub** and check that the menu.lst is now in your /boot/grub/ directory. Reboot and see how you go. (If I have missed anything with the code here or there is a better way, others users please sing out ... :)

If no joy and error 15 (or any other error), could be a syntax error or some detail is wrong in the menu.lst. So, having a look might help then ... a great tool is SuperGrubDisk found at:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

Down load, burn disk, boot from it and that will probably (probably) get you on your way from here.
> 
Can ths HD be connected to another windows based machine? I thought linux used a different file system format then Ms machinesIf you mean in a network, sure. That should work out of the box via samba. If you mean the hard drive file system itself, kinda. Linux uses EXT3 but can understand fat anything (vfat in linux lingo) and the microsoft creation NTFS and can readily read and write to them (FAT reliably and is often used as a shared drive between the two OSs, NTFS with aid of software patch - yet another gate that needs to be opened). The other way, Windoze will not recognise EXT3 for reading and writing and you will find in Windoze disk management on a dual boot box EXT3 drives/partitions just show as 'Healthy' and that is that.  Which means ... forget Windoze, it will have no idea what is on that drive as it is EXT3 for Linux and you can't fix a linux install with Windoze, Like speaking Polish in China (to use the language analogy again!). They are not related in any way, not even distant cousins.

Sounds like you are getting very close, my friend. :)

* Update - I just thought of something which I should have suggested when I realised you had upgraded to 8.04 not updated 7.10. You could have just downloaded the install iso,made a disk and done a fresh install to the partition your old install (with the dodgy menu.lst) was on. This would have installed a fresh menu.lst and all sweet - running system and you can say you have upgraded it from Gutsy to Hardy for them! Still an opton ...

---

### Post by jimv on 2008-09-05
You can use this driver in Windows to access an EXT3 drive:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Or you can boot from the LiveCD and plug in a portable drive to do the backing up, and also to do the install.

---

### Post by Bucky Ball on 2008-09-05
Thanks for the tip, Jimv. Learn something every day ... :)

---

### Post by egalvan on 2008-09-06
> **Bucky Ball said:**
> 
 linux  can readily read and write to them (FAT reliably and is often used as a shared drive between the two OSs, NTFS with aid of software patch - yet another gate that needs to be opened). ...

Can't speak for 7.10 or earlier, since I didn't use them much,
but 8.04 sees NTFS 'out-of-the-box', no patches needed.

I've dual-booted at least seven XP-8.04 machines, and they all see the XP partition just fine.

And as other have stated,

 [http://www.fs-driver.org/](http://www.fs-driver.org/)

gives you almost perfect ext2 support for Windows.

One day, one shall rule them all....

---

### Post by egalvan on 2008-09-06
> **porchrat said:**
> 
I am really impressed at your determination I wish we had computer repairman like you where I come from

Amen to that!

+1

---

### Post by porchrat on 2008-09-08
> **Bucky Ball said:**
> menu.lst needs to be in /boot/grub/ not /media/boot/grub. That is where you hard drives and other media lives (mount 

I think he has it under media/boot/grub because he is mounting the HDD from a liveCD boot.  I don't think it matters when GRUB runs for real on boot it should just read it from /boot/grub

hope that makes sense to everyone because it doesn look kind of convoluted when I write it down...seemed a lot more coherent in my head

---

### Post by Bucky Ball on 2008-09-08
[quote=egalvan]Can't speak for 7.10 or earlier, since I didn't use them much,
but 8.04 sees NTFS 'out-of-the-box', no patches needed.[/quote]

Totally, but does not reliably* write* to them. Unless, of course, there has been some advance I am unaware of. All ears. :)

[quote=porchrat]I think he has it under media/boot/grub because he is mounting the HDD from a liveCD boot. I don't think it matters when GRUB runs for real on boot it should just read it from /boot/grub[/quote]

Gotcha

---

