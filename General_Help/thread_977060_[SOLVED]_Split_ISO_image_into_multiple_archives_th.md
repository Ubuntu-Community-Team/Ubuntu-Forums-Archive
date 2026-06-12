---
title: "[SOLVED] Split ISO image into multiple archives that can later be extracted to the fu"
date: 2008-11-09
forum: General Help
---

### Post by noerrorsfound on 2008-11-09
How do I create a multi-part archive (tar.gz, tar.bz2, 7z, rar, anything) of an ISO image or some other file that can later be extracted to produce the full ISO?

I don't have DVD-Rs, only CD-Rs, and I have an ISO that is a few gigabytes. I'd like to be able to burn the multiple parts of the archive, then later rip them from the CD-Rs, and extract them once they're on the hard drive, which will give me my ISO back in one piece.

Example of how they'd be stored on the discs:
**CD 1**
part1.tar.bz2
part2.tar.bz2
part3.tar.bz2
**CD 2**
part4.tar.bz2
part5.tar.bz2
part6.tar.bz2
**CD 3**
part7.tar.bz2
et cetera, depending on how many parts I split it into and how large the file is.

---

### Post by stinger30au on 2008-11-09
you can use file roller do do belive to this

or you can install rar and do it form command line with

sudo apt-get install rar

or you can install wine and run izarc, it runs fine in wine and will do it in what ever archive format u want in a gui format

[http://www.izarc.org/](http://www.izarc.org/)

install wine here

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by noerrorsfound on 2008-11-09
> **stinger30au said:**
> you can use file roller do do belive to this
**How?** I hope I've been descriptive enough. What I want to do is:

[LIST=1]
[*]Pack ISO image in an archive
[*]Split archive into multiple parts
[*]Burn all parts of archive
[/LIST]
And then I must be able to simply take them from the CD later, extract, and get my full ISO.

---

### Post by noerrorsfound on 2008-11-16
Clearly this is an impossible task on Linux...

---

### Post by oldsoundguy on 2008-11-16
best to spend 20-30 bucks and get a dual layer burner and get into the 21st century.

---

### Post by keyshawn on 2008-11-18
I was wondering this myself, and a simple search on the forums brought this - [http://ubuntuforums.org/showthread.php?t=804796](http://ubuntuforums.org/showthread.php?t=804796)

Just install the rar package first. 



>  rar a -v2000M example.rar example

The '2000M' parameter means the size of the archive that you want each part to be. 

So for the dvd image that you have you should use:

```
rar a -v698m mydvdromimage.rar nameofmydvdromimage.iso
```

This worked for me :)

regards,
keyshawn

---

### Post by Amedee on 2008-12-31
> **noerrorsfound said:**
> How do I create a multi-part archive (tar.gz, tar.bz2, 7z, rar, anything) of an ISO image or some other file that can later be extracted to produce the full ISO?

I don't have DVD-Rs, only CD-Rs, and I have an ISO that is a few gigabytes. I'd like to be able to burn the multiple parts of the archive, then later rip them from the CD-Rs, and extract them once they're on the hard drive, which will give me my ISO back in one piece.

Example of how they'd be stored on the discs:
**CD 1**
part1.tar.bz2
part2.tar.bz2
part3.tar.bz2
**CD 2**
part4.tar.bz2
part5.tar.bz2
part6.tar.bz2
**CD 3**
part7.tar.bz2
et cetera, depending on how many parts I split it into and how large the file is.

I have a much better solution for you, and it's really easy! Just use the default GNU tools **tar**, **split** and **cat**. There is absolutely no need for any fancy gui tools or (god forbide!) software that you have to run in Wine!

Just type the following in a console window:

```
tar cvzf - filename.iso | split -d -b 700m - filename.iso.tar.gz.
```

This wil produce the following files:
filename.iso.tar.gz.1
filename.iso.tar.gz.2
filename.iso.tar.gz.3
...

Burn to CD with your favorite burner, one file per disk.

Then later if you want to restore the iso, first copy all te parts in one directory, and then type

```
cat filename.iso.tar.gz.* | tar xvzf -
```
That will give you back your original ISO.

I needed this a few days ago for a >10G backup that I wanted to put on a FAT32 external drive (maximum file size: 2G). Worked like a charm!

If you are concerned with space, replace the 'z' option in tar with 'j', and replace 'gz' in the filenames with 'bz2'. Bz2 compression is usually a bit better than gz compression, but it's slower.

And if you really want to save disk space, install the console version of 7-Zip, create a .7z archive, and pipe this trough split. I leave the exact syntax as an excercise to the reader. ;-)

---

### Post by noerrorsfound on 2008-12-31
I actually have DVD+Rs now for my DVD burner, but maybe that will help someone in the future. Thanks.

> **oldsoundguy said:**
> best to spend 20-30 bucks and get a dual layer burner and get into the 21st century.
Best to read the first post and see that a lack of a DVD burner wasn't my problem. :rolleyes:

---

### Post by MartyBuntu on 2008-12-31
If you already have the full .ISO, why you would want to split it up, *only to put it back together?*

Do you mean you want to move this .ISO to another computer?

---

### Post by koepked on 2009-05-11
> **MartyBuntu said:**
> If you already have the full .ISO, why you would want to split it up, *only to put it back together?*
 
Do you mean you want to move this .ISO to another computer?
 
If you're storing a large .ISO ( > 4 GB I think) on a FAT32 partition instead of on a disc, there is a perfectly good reason to want to do this. That's what I'm trying to do, and it looks like this thread's gonna give me the solution, thanks Amedee!

---

### Post by noerrorsfound on 2009-06-11
> **MartyBuntu said:**
> If you already have the full .ISO, why you would want to split it up, *only to put it back together?*

Do you mean you want to move this .ISO to another computer?
Old thread, but since it's been bumped recently I guess I'll answer this.

I wanted to back up an ISO but lacked a DVD to do so (at the time I lacked a large flash drive as well) so the only other option was multiple CDs.

---

### Post by 4ebees on 2009-08-21
> **Amedee said:**
> I have a much better solution for you, and it's really easy! Just use the default GNU tools **tar**, **split** and **cat**. There is absolutely no need for any fancy gui tools or (god forbide!) software that you have to run in Wine!

Just type the following in a console window:

```
tar cvzf - filename.iso | split -d -b 700m - filename.iso.tar.gz.
```

This wil produce the following files:
filename.iso.tar.gz.1
filename.iso.tar.gz.2
filename.iso.tar.gz.3
...

Burn to CD with your favorite burner, one file per disk.

Then later if you want to restore the iso, first copy all te parts in one directory, and then type

```
cat filename.iso.tar.gz.* | tar xvzf -
```
That will give you back your original ISO.

I needed this a few days ago for a >10G backup that I wanted to put on a FAT32 external drive (maximum file size: 2G). Worked like a charm!

If you are concerned with space, replace the 'z' option in tar with 'j', and replace 'gz' in the filenames with 'bz2'. Bz2 compression is usually a bit better than gz compression, but it's slower.

And if you really want to save disk space, install the console version of 7-Zip, create a .7z archive, and pipe this trough split. I leave the exact syntax as an excercise to the reader. ;-)

Very nice. Thanks for this :)

---

### Post by cheshirekow on 2010-04-16
Sorry. I know this is going to bump the thread... but man, that was useful. +1 Thanks! Amedee.

---

