---
title: "No Disc-At-Once For Compaq Presario SR5219UK?"
date: 2008-04-27
forum: Hardware
---

### Post by Mark76 on 2008-04-27
I looked it up on the cdrdao website and I can't find any mention of Compaq CD/DVD hardware.

Is there any way to get it working?

---

### Post by andrew.46 on 2008-05-15
Most modern drives work quite well with the generic-mmc driver. Have a look at the 'howto' I have just written on cdrdao copying:

[http://ubuntuforums.org/showthread.php?p=4964807](http://ubuntuforums.org/showthread.php?p=4964807)

and with any luck this will get you started :).

        Andrew

---

### Post by Mark76 on 2008-05-16
Thanks Andrew. But now I'm confused.

I thought DAO was a method for writing tracks to a CD, but from what I can tell it's actually for copying CDs (which I assume means you need two CD/DVD players, one of which has to be a burner).

Is that right?

---

### Post by andrew.46 on 2008-05-16
Hi,

I can sense some confusion here :-)

> **Mark76 said:**
> I thought DAO was a method for writing tracks to a CD, but from what I can tell it's actually for copying CDs (which I assume means you need two CD/DVD players, one of which has to be a burner).

To quote from the excellent [YoLinux Tutorial: Burning a CD or DVD]("http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html"):
> 
CD's can be burned in DAO (Disk At Once) or TAO (Track At Once) mode. The only reason to use DAO mode is when burning audio CD's. Audio CD's burned TAO will have 2 second gaps between tracks

To copy an audio cd using this DAO *method* the best way is to use the *program* cdrdao. And you do not need 2 drives, if there is only one drive an image is created on your computer's  disk and then copied back to the writeable cd / DVD.

          Andrew

---

### Post by Mark76 on 2008-05-16
And if you have a folder full of (non copyrighted) tracks pulled from the internet that you want to burn to a CD for safe keeping, it'll do that as well, right?

---

### Post by andrew.46 on 2008-05-16
Hi again:

> **Mark76 said:**
> And if you have a folder full of (non copyrighted) tracks pulled from the internet that you want to burn to a CD for safe keeping, it'll do that as well, right?

I *believe* that cdrdao will do this, but I have never investigated this aspect of the program. I suspect you will need to create your own TOC. This is discussed briefly:

[http://www.togaware.com/linux/survivor/Audio_CD.html](http://www.togaware.com/linux/survivor/Audio_CD.html)

but again I must admit I have never tried this :confused:.

    Andrew

---

### Post by Mark76 on 2008-05-16
Okay. I'm using a small app called RoxDAO, which is basically a GUI for cdrdao. This is what I got when I tried to burn an album of wav files with it.

---

### Post by andrew.46 on 2008-05-16
Hi,

> **Mark76 said:**
> Okay. I'm using a small app called RoxDAO, which is basically a GUI for cdrdao. This is what I got when I tried to burn an album of wav files with it.

The error seems to be:

```
Error trying to open /dev/sg5 exclusively (Permission denied)...
```

Try running as sudo, or umount the cd. But better still try [GCDMaster]("http://cdrdao.sourceforge.net/gcdmaster/") which is the official frontend for cdrdao.

    Andrew

---

