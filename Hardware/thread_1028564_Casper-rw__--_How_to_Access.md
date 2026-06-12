---
title: "Casper-rw  -- How to Access"
date: 2009-01-02
forum: Hardware
---

### Post by praxis1949 on 2009-01-02
If this is a stupid question -- sorry in advance. 

I have Ubuntu 8.10 on a 4 gig Kingston flash drive (using the PenDriveLinux install), and the persistence is working fine EXCEPT I have not found an easy way of putting documents directly into (I assume)casper-rw.  When using the flash disk version of Ubuntu, I can save attachments to emails (email myself documents?),  or even access them on another computer over the home network, and then save them (I assume in casper.rw). No problem. But, is there some way I can mount casper.rw (assuming it is some kind of partition), and save files directly in it (on the flash drive)  from my desktop Ubuntu computer or my Vista computer)? To make the flash disk version of Ubuntu a serious work tool, I must find some simple way of transferring files to and from it from other computers.

Regards


John S

---

### Post by Endolith on 2009-04-11
just make a directory to mount it in:

```
sudo mkdir /media/casper
```

and then mount it:

```
sudo mount -o loop casper-rw /media/casper/
```

---

### Post by tg3793 on 2010-11-15
I tried this myself. But it doesn't seem to be working for me. Is my situation a little different?

I have a 1Gig Knoppix casper image that I am trying to access on my USB thumb drive. I would like to do two things:

1) I would like to transfer the contents of this 1Gig casper image to a larger 4 Gig casper image which is on another flash disk.

2) I would like to copy my tomboy notes from my USB drive and put them on my Ubuntu desktop.

~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ 
What I did, and the error
~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ 

1) With my desktop already booted into Ubuntu I placed the thumbdrive into the USB slot.
2) Drive came up in Nautilus and I looked inside the "casper" directory just to see what I could already view. The following files are listed there:

- filesystem.manifest
-  filesystem.manifest-desktop
-  filesystem.size
-  filesystem.squashfs
-  initrd.lz
-  vmlinuz

3) Next I copied the casper file (or is it a directory) to a another temp directory. I'll show you my mistake too .. Here is what I did:

scribe@scribe-desktop:~/Temp/workbench$ sudo mkdir /media/casper
scribe@scribe-desktop:~/Temp/workbench$ sudo mount -o loop casper-rw/medi/casper/
casper-rw: No such file or directory ([COLOR=DarkOrange]duh of course not :-)[/COLOR])
scribe@scribe-desktop:~/Temp/workbench$ sudo mount -o loop casper /media/casper/home/scribe/Temp/workbench/casper: Is a directory ([COLOR=DarkOrange]hmm[/COLOR])

- - - - - - - - - - - - - - - - - - - - - - - - - - - - 

So is what I am trying to do even possible? I haven't tried copying these six files over to the two gig casper image yet. But as for the second goal I thought there would be a way that I can mount the casper image and then browse the directory structure?

I know I'm a newb :-) But I'm willing to do my homework and document my efforts for the future benefit of others ... Please help.

---

### Post by C.S.Cameron on 2010-11-15
I don't think what you want is in the casper directory but is in the casper-rw file.

---

### Post by tg3793 on 2010-11-15
Imagine the sound that Scooby Doo makes when he discovers something. That's sorta what went on inside my head when I read you comment. 

And then I went to look at the files on the USB drive and again. And there it was just two or three inches down from the casper directory. At this point my eyes rolled up into my head involuntarily.

Thanks, I'll retry this :-)

---

### Post by tg3793 on 2010-11-15
Wow; if Ubuntu was a woman I could possibly be in love with her. But since being in love with lifeless objects would be simple foolishness, my wife will never have anything to worry about :-)

In any case, for the benefit of others here is what I did to solve my Tomboy notes problem. 

1) Mounted the casper-rw file as instructed:
- This worked but it threw me off for a moment when I saw both "casper" and "casper-rw" on the left side navigation panel of Nautilus. The "casper-rw" eventually disappeared but not before I had clicked on it a couple of different times trying to figure out why I couldn't access it.

2) Found out that the recent version of Tomboy now hold it's data in .local
... So for the bootable USB drive I have the default user that is created it "ubuntu"
... Had to bring up a 'root' instance of nautilus and expose hidden files to see this but then went to:
/media/casper/home/ubuntu/.local/share/tomboy

3) After that I copied those files to the /.local/share/tomboy directory on my Ubuntu 10.04 desktop and everything worked just great.

Thanks for your help !

---

### Post by gogolac on 2010-11-16
wow, awesome solution, that' work very well for me
thank you Endolith.

and tg3793, before you do the ```
mkdir /media/casper
```
you have to be sure you are in flash memory stick by the command promp and then do the mount command.


sorry  for my bad english.

---

### Post by C.S.Cameron on 2011-01-28
Oops

---

