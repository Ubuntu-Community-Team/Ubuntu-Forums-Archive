---
title: "SOME COPY to FLOPPY others Don't"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by LateNighter on 2005-10-30
[B]I have a rather "STRANGE" Problem:confused: 
 Any Document "NO MATTER" the Format, after I save it to my Default Spot which is a folder I Titled "MY GOODIES", Made in open Office, after I mount my FLOPPY, and open up the disk, Whenever I try to copy and paste, or Drag n Drop and then Copy/Or Move  it to my FLOPPY.
 It will either come up Can't Copy file, "ACCESS IS DENIED" or just plain CAN NOT COPY FILE???

 Now here is the "STRANGE" Part?:???: 

 I can copy almost any other type of File, Like jpg or what have ya but any others as far as Open Office, I might as well be trying to PULL TEETH...:mad: 

 I thought maybe my Floppy was going BAD but thats not the Case if I can Copy others. Besides Open Office.

 I even tried My FLOPPY with another OS, Windows to be Precise, and it "WORKED JUST FINE" It's detected every place, That I can CHECK IT!!!!

 I've used my FLOPPY a few times to Store Documents from Open Office.

 Why all of a Sudden would it START to Foul Up NOW???:???: 

 ANY IDEAS/HELP I'd be MOST GREATFUL...:KS [/B]

---

### Post by MarcDM on 2005-11-03
ok this is just a stab in the dark, but it might work.

On my machine, I was having a problem where a floppy was used on a windows box in the next room, refused to mount on my machine.

without knowing the filesystem on the floppy (formatted on windows), I assumed it was FAT so I mounted it using :
```
sudo mount -t msdos /dev/fd0 /media/floppy
```

This kinda worked, as the files with names longer than 8 chars where displayed and copied as sixchr~1.doc 

I then decided to experiment, and discovered that the floppy was formatted so tha it could use long filenames. blah blah blah....

Anywho, the end result is, I've modified the file /etc/fstab
the line that says 
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0 0
```
now reads :
```
/dev/fd0        /media/floppy0  auto,umsdos,vfat,ext2    rw,user,noauto  0 0
```

And I've had no more floppy problems. 

Essentially what I've done was tell the mount(8) program to check for umsdos,vfat and ext2 filesystems on the floppy in addition to autodetect. This seems to have the effect of choosing one of the mentioned options before the autodetected 2nd choice. In my case, the autodetect was not doing so well at detecting the FAT32 aka vfat filesystem on the floppy.

Hope this helps.

Marc DM

---

