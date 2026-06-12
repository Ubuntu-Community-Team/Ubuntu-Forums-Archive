---
title: "Raw format iso file"
date: 2008-08-16
forum: General Help
---

### Post by DeMus on 2008-08-16
Hi, I just downloaded a raw format iso file and I can not extract it. The programs I use can't handle the format. Which program can do the trick and where can I find it?
Thanks for all the help.

DeMus

---

### Post by cdtech on 2008-08-16
This is a CD image which is used to burn to a CD-ROM. Just use a burn program such as GnomeBaker or whatever you prefer to burn the CD Image to disk.

[http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

> The name "ISO" is taken from the ISO 9660 file system used with CD-ROM media but the term ISO image can refer to any optical disc image, even a UDF image.

---

### Post by bingoUV on 2008-08-16
I don't know what a raw format ISO file is, but file-roller is generally able to open all ISO files I have encountered so far.

---

### Post by Garratt on 2008-08-16
Edit: wrong info

---

### Post by DeMus on 2008-09-04
> **DeMus said:**
> Hi, I just downloaded a raw format iso file and I can not extract it. The programs I use can't handle the format. Which program can do the trick and where can I find it?
Thanks for all the help.

DeMus

Once more I have some files which are described as RAW ISO files. If that is true I have no idea. One thing is for sure, I can not do anything with them:
I can not extract them,
I can not burn them on a DVD,
I can not use them as a virtual CD-rom.
Nothing works.

Can somebody help please. I sure would like to see the movies hidden in those files.
Thanks in advance.

DeMus

---

### Post by bingoUV on 2008-09-04
You make it difficult for people to help you, but I'll try:

**The programs I use can't handle the format**

WHICH programs do you use?

**Once more I have some files which are described as RAW ISO files**

The files are described as raw by WHOM?

Have you tried file-roller? 
Where did you find the files? 
Any similar example so that someone here might have seen it somewhere and might point you to some method of opening the file?

---

### Post by DeMus on 2008-09-06
> **bingoUV said:**
> You make it difficult for people to help you, but I'll try:

**The programs I use can't handle the format**

WHICH programs do you use?

**Once more I have some files which are described as RAW ISO files**

The files are described as raw by WHOM?

Have you tried file-roller? 
Where did you find the files? 
Any similar example so that someone here might have seen it somewhere and might point you to some method of opening the file?

Sorry for the missing info. You're right, I should have written down the names of the programs.
I used file-roller, but it doesn't accept the file.
I used Win-Iso, FireBurner, no success.
I used Brasero, K3B and Ashampoo (in Wine) and a dvd is burned but it is unreadable.

I use a program called OpenFTD which is a directory for news groups. From there it is easy to download movies, music and programs. The movie I downloaded Kill Bill 1, and a series of 5 movies called Earth The Biograpy.
I even copied the files to my Windows installation (double boot) and also there I can not open the file or burn with programs like Winrar, Nero and also WinIso and Ashampoo.

Any ideas? I sure hope so.

DeMus

---

### Post by thtrgremlin on 2009-02-26
Realize this is pretty late, but in case anyone else comes by this...

I didn't have any problem right clicking an iso and extracting it, but an alternative to extracting it would be to mount it. Our type we know as 'iso9660' and since this is not a "block" device, but a file, we use something called a loopback. So if your image was say foobar.iso

1. sudo mkdir /media/iso

gives a place to mount it

2. sudo mount foobar.iso -t iso9660 -o loop /media/iso

filename, -t to specify type, -o for an extanded option, in this case, we want to use loopback, and then where we want to mount it.

Once you are finished with whatever you needed, unmount it.

sudo umount /media/iso

(notice it is umount, and not unmount. I used to make that mistake)

Also, just to note, without doing anything else, the iso will be mounted after you restart, so you may wish to copy the files off the "disc" to somewhere on your computer.

Hope this helps  :)

Oh, final thing just because we can over look these things at times, if you downloaded this iso off the web, there should have been a 'md5 checksum' to ensure the image was downloaded correctly / not corrupted. Had it only happen a few times, but checking the sum at the first sign of trouble can save a lot of unnecessary grief.

---

### Post by Slim Odds on 2009-02-26
Depending on the ISO image file, it may or may not be ISO9660

It could also be UDF

Or a hybrid.....

---

### Post by ephestione on 2009-08-22
> **thtrgremlin said:**
>  2. sudo mount foobar.iso -t iso9660 -o loop /media/iso
  This appears to be a universally accepted assumption, which sometimes is wrong... and around which is based gmount-ISO as well, without any possibility of setting the correct parameters. In the age of (high-capacity) DVDs, iso9660 sometimes is outdated, so I had to waste half an hour worth of digging, until I tried out of curiosity "udf" in place of "iso9660" in that commandline, and the mount magically went fine. By the way, the ISO type was recognized by nautilus as "raw CD image (application/x-cd-image)" as well in my case, so it is probably the same thing DeMus has to do, since usually HD movies are files greater than 2GB, thus needing a UDF file system to be stored on a DVD. Thank you for putting up this thread anyway, it was opf great help in the end! ;)

---

### Post by mazz0 on 2009-09-17
I'm having a simliar prolem.    When I try to mount the ISO I get told "CD-ROM is NOT in ISO 9660 format", but how do I fimd out what format it is?  It's not udf either, I tried that.  Any ideas?  It's an old windows game, if that helps.

---

### Post by Superpelican12 on 2011-02-19
Hello, everybody I would like to convert one of my Xubuntu 10.10 Live CDs in a Xubuntu 10.10 ISO image, just like the one that you can download. Because I can't find my original downloaded ISO and downloading it again will take quite long. So I used Brasero' s 1:1 copy function. I changed the to copy to in a .iso file. But It asks what kind of file I would like to choose. But I don't no what to choose. So I chozen ISO 9660, because then the extension changes in .iso. But will this give me a raw CD ISO, like if I download it?

Greetings,

Superpelican:P

---

