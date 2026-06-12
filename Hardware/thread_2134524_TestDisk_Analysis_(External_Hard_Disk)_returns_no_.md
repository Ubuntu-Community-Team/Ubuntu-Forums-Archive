---
title: "TestDisk Analysis (External Hard Disk) returns no partition, what next?"
date: 2013-04-11
forum: Hardware
---

### Post by alph257 on 2013-04-11
[FONT=sans-serif][COLOR=#000000]Here is the results from running TestDisk's Analyse tool on my external hard disk:

[/COLOR][/FONT][COLOR=#333333][FONT=Ubuntu Beta][B]Disk /dev/sdb - 500GB / 465 GiB - CHS 476940 64 32
        Partition                         Start       End             Size in Sectors[/B][/FONT][/COLOR]

This means, they found no partition right? 

The only option I'm given are: [I]A: add partition, L: load backup, Enter: to continue.
[/I]
And a little history of what happened:
My external hard disk (a relatively backward model that requires 2 cables) was plugged into a Macbook Air, but my friend realised the cable is not long enough to stretch across the computer. So, it was plugged in for a while, powered up, but it did not show up on the Mac, and hence, it never got dismounted/removed properly.


So, I went home and plugged it into my Windows 7 notebook, and suddenly the disk prompts me reformat, which I didn't of course. Also, I ran crystal disk management tool very recently, and the disk was/is in perfect health. So it must be the brief interaction with the Macbook that caused it.


It doesn't read anything in Windows 7. But on my dual-boot WUBI-installed Ubuntu, I can see the folders on the disk: just that all the folders are empty.

What should I do next? And what are the next steps towards recovering the lost partition and files? Add Partition? Load Backup? Or, Enter to continue? I was advised on another forum to try to use it on my friend's Macbook again. But, if Ubuntu doesn't recognise the partition, what is the chances that the Mac OS will?

And, does anyone still have mal_conductor's guide around? Because its no longer available on mediafire.


Thank you for any inputs!

---

### Post by bcbc on 2013-04-11
This is a great tool, but requires a bit of manual labour to check what it recovers. You should limit the recovery file types to only the ones you are interested in. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It's also read-only, so won't cause additional damage unlike some other recovery methods.

---

### Post by alph257 on 2013-04-11
> **bcbc said:**
> This is a great tool, but requires a bit of manual labour to check what it recovers. You should limit the recovery file types to only the ones you are interested in. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

It's also read-only, so won't cause additional damage unlike some other recovery methods.

Thanks. I've read about this in many pages that were introducing TestDisk, but I was thinking that would be the last resort. 

From my really basic understanding, if Ubuntu could read the folder names, it means that there is just something wrong with how it is reading the partition, not that the disk is actually damage. Am i right to say that?

In any case, I think I will attempt to run the hard disk on a mac again. Is it okay to run on any random Mac, or must I plug it back to the one that caused the trouble in the first place? Then I will try PhotoRec if that fails.

Many thanks!

---

### Post by bcbc on 2013-04-11
I can't explain the differences other than the drivers Ubuntu uses are different to those that Windows uses and therefore respond differently to the data. In this case, Windows refuses to show anything as it believes it is corrupted, but Ubuntu shows the folders (but no data).

I don't think opening it under different computers will fix the problem. If you've done the 'deep' analysis that testdisk offers and found nothing, then I'd move on to photorec.

---

### Post by alph257 on 2013-04-11
Actually, I'm kind of stuck with TestDisk.

After the Analysis got to here:
[IMG]http://i.imgur.com/DxvJFRT.png[/IMG]

Since no partition is detected, I don't even know if I should "add", or press enter to continue. 

Thanks again. :)

---

### Post by bcbc on 2013-04-11
Press Enter and select "Deeper search".

---

### Post by alph257 on 2013-04-11
Sure, doing that right now. Already got 2 warnings within seconds.

[IMG]http://i.imgur.com/m6NKRek.png[/IMG]

Will post back when the search is done (probably will take a day or so i suppose).

---

### Post by mal_conductor on 2013-04-11
I do have it.
It has been a long time.  I quickly read the guide, but I am unsure if it will help you.
You can read it and follow along to see if it will help.

I will try to upload on mediafire again. Else, we'll figure out how to send by email.

---

### Post by mal_conductor on 2013-04-11
reloaded the guide. [http://ubuntuforums.org/showthread.php?t=1082417](http://ubuntuforums.org/showthread.php?t=1082417)

---

### Post by alph257 on 2013-04-12
Thank you so much. I will try to follow it and figure something out.

(Meanwhile, at 38% with deeper search.. So it'd be another 15 hours or so to go.)

---

### Post by alph257 on 2013-04-12
Update from "Deeper Search":
> [B]
Warning: the current number of heads per cylinder is
but the correct value may be 255.
You can use the Geometry menu to change this value.

It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partition overlaps.[/B]

After clicking Continue, it is listing the partition and a bunch of files in Red. I'm going to slowly try to figure out what to do.

---

### Post by alph257 on 2013-04-12
I'm at the page that they list all the directories. I should select **C** to copy the selected files, but... a real juvenile question, nothing happens when i do that. It says something like some files have been copied, but i just couldn't figure out where to.

---

### Post by zrdc28 on 2013-04-13
Put it back into the mac and reboot, then tell it to unmount, Then you should be able to do whatever you want!

---

### Post by alph257 on 2013-04-13
Since I'm kind of stuck using TestDisk, I am going to give this a go. Someone at another forum said the same thing!! Damn, i worried for a few days for nothing!

Anyway, just to clarify. I should plug it in -> reboot the mac -> then unmount?

---

### Post by alph257 on 2013-04-17
That didn't work unfortunately.

Going to try testdisk again after attempting EaseUS Partition Recovery software. But it is taking even longer that TestDisk.

---

