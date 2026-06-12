---
title: "Installing GRUB on DOS/FAT partition"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by aajax on 2009-03-25
I've been using another Boot Manager but would like to try GRUB.  My idea is that a Boot Manager needs to reside in its' own partition which is separate and distinct from other partitions on the drive.  In that, I don't want any operational system to depend on another.  The preferred type of partition is FAT.  With my existing Boot Manager I also need DOS.  Likewise DOS may be desirable on this partition when running GRUB.

I've studied the GRUB installation methods and think I understand it pretty well.  However, there is a curious finding.  The stage 1.5 file for FAT has a file name that cannot be stored on a real FAT partition, which only supports 8.3 style names.  While I would concede that a file with the given name could be created using Windows I have no need or desire to install Windows.  Furthermore, the Boot Manager I'd be replacing does not have any such requirement and I'm sure I'm not going to start installing and maintaining Windows just to be able to use GRUB as a Boot Manager.  Surely, I'm not the only one who feels this way.

Is there something I've missed or did the designers of GRUB really create something the requires Windows where DOS ought to be sufficient?

---

### Post by meierfra. on 2009-03-26
If you  mount a fat partition in Ubuntu, you can also create such files names. In fact I used to have fat32 grub partition.  And as far as I can see it,  doesn't make much sense to use  Grub, if you don't have a linux  operating system. Grub can only boot linux (and bsd,etc)  directly. For other OSs it has to rely on a native boot loader.

---

### Post by Mark Phelps on 2009-03-26
> **aajax said:**
> 
Is there something I've missed or did the designers of GRUB really create something the requires Windows where DOS ought to be sufficient?

Fail to see how MS Windows or MS DOS enters into this.  GRUB is most commonly used for Linux systems, and if the proper stanzas are added to the menu.lst file, can also boot MS Windows OSs by invoking the MS Windows boot loaders.

So, that fact that GRUB may not work when installed in a FAT (16) MS DOS partition, is not really a fault with GRUB.

As with what others have said, if you want to play around with MS Windows boot loaders, GRUB is not your best choice.

---

### Post by aajax on 2009-03-26
I have many computers that all run multiple systems (i.e., they are multi-boot).  Some run Windows and some do not but the objective is to have a small partition whose only purpose in life is to boot several other partitions.  I've been using Powerquest Boot Magic and it works very nicely but Powerquest no longer exists and the Boot Magic product hasn't been updated in quite a while.  I thought GRUB could be used as a replacement.  If so on these small Boot Manager partitions, it would only be used to do what it calls chain loading.  This would be true even in the cases where it is booting a Linux partition that has its' own instance of GRUB.  I think this is necessary even for the Linux systems in order to preserve the ability for each respective system to be independently maintained.  In that, kernel updates and modification of menu.lst, etc.  From what I've read GRUB can do this.

So I suppose a different way to put the question might be, "why would any developer build something advertised to work on a FAT partition and specify a file name that is incompatible with FAT when they could just as easily chose one that is?".

---

### Post by meierfra. on 2009-03-26
> "why would any developer build something advertised to work on a FAT partition and specify a file name that is incompatible with FAT

Did you try to install Grub?  How are you planning to install Grub?  The only problem I can see is with installing grub to the Fat partition. Once its installed it should work just fine, even if  all you OS's are DOS:

[LIST]
[*]The filenames  are   not incompatible with FAT. As I said I used to have  Grub  on FAT partition. The filenames are only incompatible with DOS. But DOS will not be involved in the booting process.

[*]  The only files which need to be on the Grub partition are stage2 and menu.lst and whose filenames are not incompatible with DOS.  The stage1.5file is going to be  embedded in the first few sectors of the hard drives and the actually name of the stage1.5 file  is not going to be used during booting. 

[*]  stage1.5 is optional.  With  stage1.5  one gets  better error messages and maintaining grub is slightly easier, but stage1.5 is not essential for booting 
[/LIST]

So I don't  think there is any real problem  with Grub on a FAT partition.

Have you considered Grub4Dos in place of Grub?

---

### Post by aajax on 2009-03-30
> **meierfra. said:**
> Did you try to install Grub?  How are you planning to install Grub?  The only problem I can see is with installing grub to the Fat partition. Once its installed it should work just fine, even if  all you OS's are DOS:

[LIST]
[*]The filenames  are   not incompatible with FAT. As I said I used to have  Grub  on FAT partition. The filenames are only incompatible with DOS. But DOS will not be involved in the booting process.

[*]  The only files which need to be on the Grub partition are stage2 and menu.lst and whose filenames are not incompatible with DOS.  The stage1.5file is going to be  embedded in the first few sectors of the hard drives and the actually name of the stage1.5 file  is not going to be used during booting. 

[*]  stage1.5 is optional.  With  stage1.5  one gets  better error messages and maintaining grub is slightly easier, but stage1.5 is not essential for booting 
[/LIST]

So I don't  think there is any real problem  with Grub on a FAT partition.

Have you considered Grub4Dos in place of Grub?

I suppose we are getting a bit technical here but to my way of seeing it FAT existed before Windows and therefore is not peculiar to Windows.  It most definitely uses files names limited to 8 characters with extensions that may be up to 3 characters.  When Windows came along and devised its' own peculiar way of mapping longer names to the 8.3 names, I think of that as a Windows specific feature rather than part of the file system that still requires files to be named with 8.3 names.  If you look the real (8.3 style) names very much exist in Windows.

The problem that I was describing is that the files supplied by GRUB cannot be installed on a FAT partition with DOS.  The installation procedure indicates that they need to be stored (copied) to \boot\grub (using DOS/FAT) notation, which cannot be done with the native FAT software (i.e., DOS).

However, there is some good news.  It seems that the the Stage1.5 is not required, at least in my case, to run GRUB.  Apparently, the Stage1 is capable of finding the Stage2 on a FAT (i.e., true FAT is defined by DOS) file system without the need to use the Stage1.5.  An error is received during setup to the affect that the Stage1.5 cannot be found but GRUB works as desired anyway.

Is it possible that the Stage1.5 isn't really needed in the case of FAT but rather in the case of the Windows specific extensions to FAT that would also include FAT32?  If so my problem has more to do with the documentation than the design of GRUB.  It is still curious why an incompatible name is used when a compatible one could just as easily have been chosen.

Thankfully, the Stage1 and Stage2 files have names that conform to native DOS/FAT requirements and everything seems to work fine and it can be installed with DOS (i.e., neither Windows nor Linux is required).

---

### Post by meierfra. on 2009-03-30
> However, there is some good news. It seems that the the Stage1.5 is not required, at least in my case, to run GRUB.

Yes, I already said so in post 5.

> Is it possible that the Stage1.5 isn't really needed in the case of FAT but rather in the case of the Windows specific extensions to FAT that would also include FAT32? If

Grub can be always be installed without the stage1.5 files, this has nothing to do with the file system.  But (as I said in post 5) installing with the stage1.5 files has a couple of advantages:

1.  If (for whatever reason) Grub is  not able to reach Stage2,  stage1.5 will display some meaningful  error message.

2.  With stage1.5 Grub can find the Stage2 by its filename. So for example, if the grub partition is resized, you won't have to reinstall grub.

But for the normally daily use, grub works just as well without stage1.5.


I should have  mentioned this  earlier:

The filenames of the stage1.5 files are not hard coded. So you can rename the stage1.5 files do something compatible with dos, as along as you let grub know the new file names during installation.

---

### Post by aajax on 2009-04-02
> **meierfra. said:**
> 
I should have  mentioned this  earlier:

The filenames of the stage1.5 files are not hard coded. So you can rename the stage1.5 files do something compatible with dos, as along as you let grub know the new file names during installation.

Are you saying the file names can be specified without recompiling?

---

### Post by dandnsmith on 2009-04-02
Yes, it is all a question of notation.
A file which is specified to grub as /boot/grub is subject to interpretation for the filesystem on which it exists.

For example, a file hierarchy which is on a FAT filesystem may be seen as
  c:\system\myfolder\other

while, mounted on /oddone by a linux system it would appear as
  /oddone/system/myfolder/other

and the representation for grub is deemed to follow the linux/unix pattern

---

### Post by meierfra. on 2009-04-02
> Are you saying the file names can be specified without recompiling?

Yes. But I'm assuming that you are  somehow   able to rename "fat_stage1_5" to say "stage15" before you copy it to your fat partition.

This is the basic idea:

```
root (hd0,0)
embed /stage15 (hd0)
install /stage1 (hd0)  (hd0)1+16 p /stage2 /menu.lst 
```

This assume that your grub partition is the first partition on the boot drive(otherwise you need to adjust   the numbers).
You might also have to adjust the "16". It is  the size of stage15 in  terms of sectors. The output of "embed" will tell you the exact number you have to use.

One might even be able to install the stage1.5 files  without copying them to the Grub partition.   To give you more details, I would have to know how  you installed  grub. Did you use a Grub Floppy or CD? Or is there a version of the grub shell which runs on Dos?

---

### Post by aajax on 2009-04-08
Oh I see!

Yes I put it there using "stage1_5" for the name.  I've been using the Super GRUB Disk and have found it very useful, which I expect should include using it to perform such an install.

Many thanks to meierfra for unsticking my mind.  He's been most helpful.

---

### Post by meierfra. on 2009-04-08
> I've been using the Super GRUB Disk and have found it very useful, which I expect should include using it to perform such an install.

Boot from Super Grub and press "c" to get to the grub command line.
Then use the commands from my previous post.  (I don't think any of the automatic Super Grub features let you do this)

> Many thanks to meierfra for unsticking my mind.

You are welcome.

---

