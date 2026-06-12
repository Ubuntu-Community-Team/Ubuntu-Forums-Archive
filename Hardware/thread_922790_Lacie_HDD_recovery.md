---
title: "Lacie HDD recovery"
date: 2008-09-17
forum: Hardware
---

### Post by caligula2 on 2008-09-17
i have a 600gb LaCie external hard drive that doesn't work any more. Through roaming the internet it has become very clear to me that the problem is that, while the hard drives are fine, the chip in the case is no longer getting enough power. i then decided to put the hard drives into my own computer and try to recover the files using raid2raid (considering that that is the only program that i have found that can actually read my hard drives), but i've only been able to recover about 12% of my 600gb. what i'm wondering is, is there any other program that you think will help my recovery, or have you found any cheap external cases for 2 hard drives.

---

### Post by pytheas22 on 2008-09-17
photorec is useful for recovering files.  You can install it with:
```

sudo apt-get install photorec
```

And run it with:
```

sudo photorec
```

Even if you can't mount the drive, it will work.  The downsides are that it can only recover certain types of files, and it dumps them arbitrarily into a recovery location without preserving the original file names (which it has no way of knowing).  But at least it will get most of your stuff back.

Keep in mind that you will need another 600 gigabyte hard drive for photorec to copy the recovered files to.

---

### Post by caligula2 on 2008-09-17
thanks for the quick reply, but i have my computer set up with 3 400gb hard drives (it was cheaper than buying a 1tb hard drive). i also have it set up so that ubuntu is actually only on about 10gb of space so if it crashes i don't have to try and save any of my files, but, in the photorec menu, i wasn't given an option to go to my media folder in root. any ideas?

thanks in advance!

---

### Post by pytheas22 on 2008-09-18
By default, photorec will save recovered files into the present-working-directory from which it's started.  So just cd into the location where you want to save your files and it should save them there.  I think it also asks you at some point where you want the files to be saved, but the way it asks you is somewhat convoluted and unclear.

---

### Post by caligula2 on 2008-09-18
unfortunately, the only thing on my hard drive are a bunch of movies that i ripped from my brothers, so when i recovered the movies with photorec, all the movies were broken and unwatchable. Any other ideas?

your responses are much appreciated.

---

### Post by pytheas22 on 2008-09-18
Can you mount your drive inside Linux at all?  What kind of filesystem did it use?

---

### Post by caligula2 on 2008-09-19
i can't mount it in linux, and in windows it says it isn't formated, and i don't have a mac to test it on. it was using the NTFS file system.

whenever i try to mount it in linux, i get the error:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by pytheas22 on 2008-09-19
Did you try running chkdsk on it from Windows as the error message says?  Also you might be able to force-mount it in Linux (I think the argument is '-f').  You would risk making it worse doing that, but not necessarily.

---

### Post by hessiess on 2008-09-19
try using the 'dd' command to dump the contence to a file.

---

### Post by timcredible on 2008-09-19
look online, there's plenty of hd cases available, you can get them with usb interfaces pretty cheap.  if you think the drives are ok, this is the easiest way to go.  probably $10-$30 for a case.  i bought one on ebay for my old ps3 drive, works fine, i think i paid $11 or so for it.

---

### Post by caligula2 on 2008-09-19
i did the thing in windows with no effect (or is it affect), and i tried the force mount, also didn't do anything. i tried the dd thing, but i think i did it wrong because now i cant mount one of my 400gb hard drives (in the terminal i typed in 'dd if=/dev/sda1 of=/dev/sde1' where sda1 is my LaCie hard drive). as for the case thing, i can't find any no-super expensive cases that hold 2 hard drives.

---

### Post by pytheas22 on 2008-09-19
Unfortunately I don't have any other suggestions in that case.  If photorec doesn't help, chkdsk does nothing (did it even say the drive was dirty or anything?), you can't mount the file system in Linux and you can't fix the hardware, I'm not sure what else to do.

---

### Post by caligula2 on 2008-09-19
that is unfortunate because my brothers live much too far away for me to be able to rip their movies and i am way too poor to buy any myself (darn college loans).

anyway, thank you for your speedy replies, and yes, windows said that it was broken.

---

### Post by pytheas22 on 2008-09-19
Yes, sorry that we couldn't figure it out.  You could always try to start a new thread and hope to grab the attention of someone who knows more about these things.

Since you say that Windows reported the file system as dirty, however, I thought I'd ask if you had also told chkdsk to try to repair it?  I think you would do this using the '/r' argument, or in other words, type:

```
chkdsk E: /r
```

where E is the drive letter assigned to the drive you're trying to fix.

As a disclaimer, I've yet to see Windows actually successfully fix anything using chkdsk, but [Microsoft claims]("http://support.microsoft.com/kb/315265") that it can.

Unfortunately, the Linux file-system recovery utilities can't do much on an NTFS drive (since Microsoft never published any documentation on NTFS).  Next time, if I were you, I'd format it in ext3 or reiserfs...they're faster and waste less space on overhead than NTFS anyway, and 'fsck' in Linux can repair them with a high rate of success if they get corrupted.

---

### Post by caligula2 on 2008-09-20
i tried the repair thing and, though it sayed it fixed about 6 items, it didn't have enough room to fix the other 1890.

i figure i'll keep checking this regularly for another week and then just give up on the matter and reformat the hard drives.

---

