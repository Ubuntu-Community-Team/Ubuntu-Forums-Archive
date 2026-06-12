---
title: "Help My Filesystem is corrupt?"
date: 2009-03-23
forum: Hardware
---

### Post by kehon on 2009-03-23
i know everyone says backup your files well i put all my files on and 120gb external drive(same size as my laptop drive (laptop only computer)) and then checked that files where there and they were formated computer drive installed windows vista and ubuntu 8.10 then i was copying some files back to computer using vista, after a while about a day i went to get some more files, windows said there is an error or something it want me to run check disk (chkdsk), i ran checkdisk overnite woke up to find that the external hard drive partion the files were on could not be mounted/read it wanted me to format(will not and have not done) the partion that my files were on, all my stuff, music collection, school work, arhives, programming projects, etc are on this drive can someone help me i tried testdisk but when i tried to read directory it said "Can't open filesystem. Filesystem seems damaged." i would like some help on this so that i may recover my 10's to thousands of files(offline websites too)

also this is as far as i have gone with testdisk and i'm stuck as what to do now any help to get all of my files back would be greatly appreciated you can email me at [email]coolkehon@gmail.com[/email]


Additional Details
i think windows may have defraged that drive during that night because defrag was going i just selected to defrag whatever was default but when i woke up it was on the laptop partion defraging not the external so i'm not sure but its a possiblity if it could help

also when i plug it in even though i cant read it when i try to safely eject windows says it in use by another program and nothing should be touching it not explorer.exe or anything any ideas whats wrong with this drive

i posted on answers.yahoo.com and wouldnt you know no answers i hope someone can help and i dont know how to use testdisk to well and i dont want to lose files so i havent messed with too much

ubuntu doesnt pull it up but gpartion editor sees it
i see the option to rebuildBS should i use this will i restore file system
by the way all of the partions are there and green

---

### Post by PerryTatchett on 2009-03-24
When you say that you "can't mount" the file system, do you mean from Vista, or from Ubuntu? Information about what has gone wrong from Vista is useful, but the most useful would be what you have tried on Ubuntu. (This *is* the Ubuntu forum after all.)

That being said, it sounds like you have a problem beyond the usual advice of: "Let your system figure out what to do with the drive"

Have you tried explicitly mounting the drive with this?

  ```
sudo mount /dev/drive_device_here /media/place_for_drive_here
```

(Note: I don't really expect that to work, given what you have said. Nonetheless, it might be worth a shot or give more information.)

I wouldn't try fiddling with the partition using gpartition unless you have another backup of your backups, or you *really* know what you are doing.

Finally, it might be useful to know how you made the backups in the first place.  Basically, what I'm asking is if there is a back story to this external hard drive or the copying procedure that might reveal some more information.

Did you, for example, do something like this to back up your hard drive: .dd if=/dev/sda1 of=/dev/external_harddrive_device? ;)

---

### Post by kehon on 2009-03-24
vista shows the drive but always ask to format it and testdisk says cannot read from file system i believe that the mft is messed up can i rebuild this

---

### Post by TheUnderTaker on 2009-03-24
I dont know much about vista but try running chkdsk /f C:

---

### Post by kehon on 2009-03-25
i thought i put it in there somewhere that chkdsk was ran overnight and when i woke up my drive wouldnt read file table messed up or something and testdisk on vista(havent tried linux yet) stops and wont complete because my computer starts doing scans and stuff going to do on linux tonight so it can finish because process gets stuck and cant be canceled vista has this problem

edit:
ok i found a program that would read all the files and directories and extract them but it cost $100 dollars needless to say i dont have that and it wont register on vista anyway some issue with it

is there another program that will do the same thing mabye on linux i would like on windows so that i can compress the data and then copy it back

edit:
i dont know if the the mft is messed up because testdisk says it is ok and there was no mirror so i copied the cur mirror to backup because there was not one

it says the mft is ok
but it says it cannot read filesystem so how can fix this
it says that the boot sector was bad so i copied to backup because there was none now it says its ok so should i just rebuild bs because zar 8.3 finds all of my files with their folders but cost $50 and dont have that and i think the mft is actually ok

any help please

---

### Post by Mark Phelps on 2009-03-25
Hate to say it, but I think you're pretty much stuck having to get an MS Windows utility to recover your files and directories.

I know, I know -- everyone is going to jump in now and claim how Testdisk and/or Photorec will do this for free -- but I had a similar situation to yours a few weeks ago (where an NTFS partition got corrupted), and my attempts to recover with testdisk and photorec yielded nothing but huge lists of unintelligible filenames.  

I had to resort to using an old version of GetDataBack for NTFS (from Runtime SW) and it was able to find and recover ALL of my files and directories.

So, maybe someone who HAS been able to recover an NTFS partition with Linux utilities can jump in here and tell you how to do it.  I didn't have any success trying that.

---

### Post by davec64 on 2009-03-25
Sorry to hear of your troubles!

I am going through exactly the same at the moment on a 320GB hard disk formatted with NTFS.
Basically my MST is corrupt and Chkdsk can't load the backup as that's corrupt as well.
Unfortunately you can't rebuild the MFT so the only thing to do is use a utility to pull as much data off the hard disk as possible.

Photorec (part of Test Disk) is really good (that's what I've used. It took approx 26 hours to run on an Athlon XP2400, so be patient!

Just make sure you've got a drive of an equivalent size to recover your files to.

Oh and one other thing the naming convention used by Phtorec isn't that helpful, so once the files have been recovered you have to go through everything naming each something meaningful and also removing the dross!

Be patient with Photorec and you should get pretty much everything back (assuming it's just the MFT causing your problem!)

Time for lots of coffee! :)


EDIT:

Just read the last post again! Photorec has a Windows version as well, if the linux one isn't succesful.

ANOTHER EDIT:

It could be the Partition Table is corrupt, you can use Testdisk to rebuild it if that is the case.

---

### Post by kehon on 2009-03-27
thanks for the advice i found another program and may have used it improperly :-# so that i was not a trial anymore called recover 2000 and it got all my files off even renamed them correctly it said the mft which i knew was bad was offset or something and testdisk said it was corrupt so i got my stuff back plus i'm in college living with uncle no money to buy program and need school work back so torrents come in handy every now and then

[IMG]http://i177.photobucket.com/albums/w235/Dekasutu/hit-it-crowbar.jpg[/IMG]

that'll fix it

---

### Post by mal_conductor on 2009-03-29
Try this for help with testdisk and photorec

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

### Post by kehon on 2009-03-30
thanks but i got a program to do it for me but this is very good for future use hopefully i wont need it

---

