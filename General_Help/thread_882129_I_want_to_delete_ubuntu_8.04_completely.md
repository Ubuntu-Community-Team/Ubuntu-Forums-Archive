---
title: "I want to delete ubuntu 8.04 completely"
date: 2008-08-06
forum: General Help
---

### Post by Millie da kidd on 2008-08-06
I am not dual booting it with nothing.
Ubuntu 8.04 is the only operating system i have on my acer.
i want to delete it completely so i can use my acer system restore disk.
Thank you in advance

---

### Post by mb_webguy on 2008-08-06
When you use your system restore disk, it will reformat your hard drive, overwriting Ubuntu (and everything else on it).

---

### Post by Millie da kidd on 2008-08-06
> **mb_webguy said:**
> When you use your system restore disk, it will reformat your hard drive, overwriting Ubuntu (and everything else on it).

iv the restore cd and it doesnt work. people have told me that the Acer recovery disk may be expecting something on my hard disk that it can't find. It may be something that the Ubuntu installed/wrote to the boot sector

---

### Post by PIPI on 2008-08-06
what is use od recovery disk if you don't have anything on hard drive?

---

### Post by mb_webguy on 2008-08-06
Well, you could use a [GParted]("http://gparted.sourceforge.net/") LiveCD to reformat your hard drive.  That would get rid of Ubuntu, but if the system restore disk is indeed looking for something on your hard drive (which seems pretty dumb, since it's sort of the point of a restore disk that it can be used when your system gets completely fubar'ed), then removing Ubuntu won't magically recover that information...

You are trying to boot from the recovery disc, right?  You need to press a key (it should be either F2 or F10 for an Acer) during startup to bring up the boot menu...

---

### Post by Millie da kidd on 2008-08-06
> **PIPI said:**
> what is use od recovery disk if you don't have anything on hard drive?

Idk thats what the guy from Geek squad told me.
So what do i do?

---

### Post by Millie da kidd on 2008-08-06
> **mb_webguy said:**
> Well, you could use a [GParted]("http://gparted.sourceforge.net/") LiveCD to reformat your hard drive.  That would get rid of Ubuntu, but if the system restore disk is indeed looking for something on your hard drive (which seems pretty dumb, since it's sort of the point of a restore disk that it can be used when your system gets completely fubar'ed), then removing Ubuntu won't magically recover that information...

I dont really know what to do with gparted live cd? or that website?

---

### Post by mb_webguy on 2008-08-06
Download the ISO for the LiveCD, then burn the ISO to a cd using Brasero or some other cd burning program.  Then boot off of the CD.  It's been a while since I've used GParted, but it should be fairly obvious how to go about reformatting your hard drive.

But like I said, I don't see how that would make your recovery disc work...

---

### Post by PIPI on 2008-08-06
and I still don't get your problem. you want to remove ubuntu so you can use recovery dics to recovery what?

---

### Post by cszikszoy on 2008-08-06
I wouldn't really believe something someone that works at geek squad tells you.  There's no point for you to get gparted, it won't solve your problem.  What you need to do is use the recovery disk that came with your computer.  You will most likely have to press one of the F keys to boot from the CD as the system is going through the POST.

I don't think the Acer recovery disk is looking for some file on your harddrive before it will restore your system.  That would be quite asinine on Acer's part.

---

### Post by Millie da kidd on 2008-08-06
> **PIPI said:**
> and I still don't get your problem. you want to remove ubuntu so you can use recovery dics to recovery what?

Once i use it it saids error and then i have to restart computer.Iv tried this like 5 times and nothing....I dont know what to do..

---

### Post by cszikszoy on 2008-08-06
It would help if you told us what the error said.

---

### Post by PIPI on 2008-08-06
look. you want what? remove ubuntu and install vista or what? i still don't see why you want to use receovery disc.

---

### Post by Jouke74 on 2008-08-06
The please tell which error! I am not looking in a crystal ball :-)

I have the feeling that the recovery disk expects a recovery partition ( X: ) where the original Windows install was supposed to be (Vista + all commercial crap absorbs 20 gb on my wife's Acer). The bootdisk probably enables reading & decrypting this partiton. In addition it puts the right parameters and additional hardware config there to restore the full system. 

Problem is that with your Ubuntu install you probably used the full disk, meaning that your recovery partition has also been erased. No way to restore the old system, unless you made a backup on CD, which Acer also tells you to do when you get the laptop and install Vista.

Contact Acer for help or keep using Ubuntu :lolflag:

---

### Post by OutOfReach on 2008-08-06
Maybe the recovery disk is looking for a Windows partition? Taking a wild guess.

---

### Post by Millie da kidd on 2008-08-06
> **Jouke74 said:**
> The please tell which error! I am not looking in a crystal ball :-)

I have the feeling that the recovery disk expects a recovery partition ( X: ) where the original Windows install was supposed to be (Vista + all commercial crap absorbs 20 gb on my wife's Acer). The bootdisk probably enables reading & decrypting this partiton. In addition it puts the right parameters and additional hardware config there to restore the full system. 

Problem is that with your Ubuntu install you probably used the full disk, meaning that your recovery partition has also been erased. No way to restore the old system, unless you made a backup on CD, which Acer also tells you to do when you get the laptop and install Vista.

Contact Acer for help or keep using Ubuntu :lolflag:

Restore failed
reason Oxd0000017
Click ok to restart your computer

That is what it saids.

---

### Post by Millie da kidd on 2008-08-06
> **PIPI said:**
> look. you want what? remove ubuntu and install vista or what? i still don't see why you want to use receovery disc.

Because i used to dual boot both of them.
but then sense i was new to ubuntu i didnt know much.
ubuntu froze and i didnt know what to do so i unpluged it from the back.
Then i took my computer to geek squad and they told me i didnt have nothing on my computer and that i needed the acer restore disk or windows vista.
So i ordered it.
while i was waiting i just installed ubuntu sense i had the cd here.
and now i cant use the recovery cd.

---

### Post by PIPI on 2008-08-06
use vista when you get it and don't buy that crap

---

### Post by Millie da kidd on 2008-08-06
> **PIPI said:**
> use vista when you get it and don't buy that crap

what crap?
i ordered the restore cd sense its $80 cheaper and it doesn work:(:(

---

### Post by HyperHacker on 2008-08-06
Wait, so they told you to install Vista? They probably just meant they can't help with Ubuntu problems.

---

### Post by Millie da kidd on 2008-08-06
> **HyperHacker said:**
> Wait, so they told you to install Vista? They probably just meant they can't help with Ubuntu problems.

Obviously if i didnt have it on my computer. At the time i took it to them i didnt have ubuntu or vista installed.
My computer was empty

---

### Post by mb_webguy on 2008-08-06
I just did a little research, and Acer does use a recovery partition.  When you were installing and reinstalling OSes, you probably reformatted the entire drive, meaning that partition is gone.  Without that recovery partition, the restore disc is useless.

If the computer didn't come with a Windows installation disc (which they should, though many don't), then... well, you can still install Ubuntu.  At least you'll have an OS, and the people here will be glad to help you with any problems you have.

Sorry.

---

### Post by solwic on 2008-08-06
> **mb_webguy said:**
> I just did a little research, and Acer does use a recovery partition.  When you were installing and reinstalling OSes, you probably reformatted the entire drive, meaning that partition is gone.  Without that recovery partition, the restore disc is useless.

If the computer didn't come with a Windows installation disc (which they should, though many don't), then... well, you can still install Ubuntu.  At least you'll have an OS, and the people here will be glad to help you with any problems you have.

Sorry.

Ditto.  My brother has an Acer lappy, and it has a recovery partition on his hard drive.  If you used whole disk, you wiped that partition.  Restore is useless.  

What's funny is that formatting the whole disk and removing Vista probably voided any warranty you had.  

:(  Wish there were better answers here, but....

Good luck.

---

### Post by Millie da kidd on 2008-08-06
> **mb_webguy said:**
> I just did a little research, and Acer does use a recovery partition.  When you were installing and reinstalling OSes, you probably reformatted the entire drive, meaning that partition is gone.  Without that recovery partition, the restore disc is useless.

If the computer didn't come with a Windows installation disc (which they should, though many don't), then... well, you can still install Ubuntu.  At least you'll have an OS, and the people here will be glad to help you with any problems you have.

Sorry.

so what would i need to do to get vista back?
I just need vista because i work with music and need to install
recycle, pro-tools, virtual dj, fl studios, and reason 4.0.
Suggestions?

---

### Post by bodhi.zazen on 2008-08-06
> **Millie da kidd said:**
> Restore failed
reason Oxd0000017
Click ok to restart your computer

That is what it saids.

And windows is so easy :)

> **Millie da kidd said:**
> Obviously if i didnt have it on my computer. At the time i took it to them i didnt have ubuntu or vista installed.
My computer was empty

You need a windows installation CD, you will need to buy one.

Put it in the CD, boot, install Windows. The default is to overwrite everything on the disk.

Can we interest you in a copy of Ubuntu ?

---

