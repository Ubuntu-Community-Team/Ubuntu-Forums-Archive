---
title: "Windows Dual-Boot Issue with Acer Aspire One"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by CheshireMac on 2009-10-18
Hey folks. I'm just dipping back into the Linux world after a stint in Windows land, and I'm already enjoying the options. I am having some issues though. Namely, not being able to boot XP (The system that came with the machine). Here;s the story:
I had to use a thumb drive to install, since it's a netbook with no optical drive. I had no issues with that, and the drive had no faults. 
I installed with no drama, and the only problem I had was that I've never performed a dual-boot installation, and when I was in the install process, I clicked on manual partition option, choosing to install Ubuntu 9.04 on a new EXT3 partition made from the extra space, as well as the swap. The install went well, and I was happy as can be to be back in Ubuntu. Then I went on to setting up XP for everything I needed. 
When I selected XP from the GRUB, it went to the load screen and then continued on to Acer's "erecovery management" tool, asking if I'd like to revert to factory default. I did this, thinking that might help (I'm an idiot, I know). It didn't help. It still goes to that screen, and I haven't found any solutions I'd feel comfortable attempting without someone viewing my machine's information.
If anyone has experience in this area, I'd be grateful for any help you could provide.

---

### Post by wilee-nilee on 2009-10-18
So are you sure you didn't over write the main operating XP partition. I have a Acer Aspire it has the recovery as the 1st partition then the main operating XP then Koala then swap. If you can install gparted in ubuntu and take a screen shot of what the partitioning looks like. This can all be fixed so hopefully others will get in on the fun.

---

### Post by CheshireMac on 2009-10-18
[http://1.bp.blogspot.com/_Zj2vLYyDEhU/StqiTvD6_sI/AAAAAAAAAAM/USAy4Uhghk8/s1600-h/Screenshot.png](http://1.bp.blogspot.com/_Zj2vLYyDEhU/StqiTvD6_sI/AAAAAAAAAAM/USAy4Uhghk8/s1600-h/Screenshot.png)[IMG]http://1.bp.blogspot.com/_Zj2vLYyDEhU/StqiTvD6_sI/AAAAAAAAAAM/USAy4Uhghk8/s1600-h/Screenshot.png[/IMG][IMG]http://file:///home/mac/Desktop/Screenshot.png[/IMG]
So here's the shot of gparted. I'm pretty sure I didn't write over Windows, but looking at it now, it seems strange. Any thoughts? Sorry I had to link to another spot for the image. Having trouble linking directly to the post.[IMG]http://ubuntuforums.org/home/mac/Desktop/Link%20to%20Screenshot.png[/IMG][IMG]http://file:///home/mac/Desktop/Link%20to%20Screenshot.png[/IMG][IMG]http://ubuntuforums.org/home/mac/Desktop/Screenshot.png[/IMG]

---

### Post by wilee-nilee on 2009-10-18
> **CheshireMac said:**
> [IMG]http://file:///home/mac/Desktop/Screenshot.png[/IMG]
So here's the shot of gparted. I'm pretty sure I didn't write over Windows, but looking at it now, it seems strange. Any thoughts?[IMG]http://ubuntuforums.org/home/mac/Desktop/Link%20to%20Screenshot.png[/IMG][IMG]http://file:///home/mac/Desktop/Link%20to%20Screenshot.png[/IMG][IMG]http://ubuntuforums.org/home/mac/Desktop/Screenshot.png[/IMG]

 Repost the screen shot I see nothing. Oh I see it is at the top of the line.

---

### Post by wilee-nilee on 2009-10-18
So it looks like you overwrote the xp sda6 which should have been the main xp is now ext3 which I assume is jaunty. So you have to be a little careful here in that you have grub controlling the boot now. I am not an expert in this sort of thing but if it was me I would install ubuntu in the the large free partition so that you still have grub control then reformat the sda6 to ntfs and use the grub choice of reinstalling the xp in that spot. There are probably easier ways of doing this so you might wait for more qualified help, but I think your basically okay in that the reformat partition for xp is still there. The only thing I notice is that the sda6 is rather small so if you plan to use xp you might need to exspand it a little bigger, which can probably be done before you start the whole process. you will have to use your live usb and unmount swap to adjust the partitions sizes. I hope this makes sense and that others will help in this endeavor.

---

### Post by CheshireMac on 2009-10-18
Okay, sorry for the wait. I was doing some more reading. I've found a lot in regards to rearranging the Grub's priorities. Something to do with Windows not liking second place or something like that.
The fix is done in Gedit, and it looks like something that would mess things up if it's not the right fix, so let's work this issue, yeah?
Thanks again for any help.

---

### Post by CheshireMac on 2009-10-18
Okay, so just to be clear, XP is still on this machine, from what you can tell? That would be a relief. As much as I don't like using Windows for my main purposes, it does have it's uses. Plus, I'd like my wife to be able to use it when her laptop isn't in reach. 
I don't know exactly what I've done here, so if anyone could walk me through what needs to be done to fix it, that would be fantastic . . . apparently for all my reading and research, there's still more to be had.

---

### Post by wilee-nilee on 2009-10-18
So as I looked at the screen shot again I had missed that sda6 was part of sda3, I don't know about just rewriting sda6, Probably what should be done is to shrink sda3 to the right leaving a empty space for xp, now reinstalling with the reformat on my aspire didn't rewrite the MBR and left grub in place but I overwrote not reinstalled. I think you have a pretty easily fixed problem but a little better advice then mine is needed.

---

### Post by wilee-nilee on 2009-10-18
> **CheshireMac said:**
> Okay, so just to be clear, XP is still on this machine, from what you can tell? That would be a relief. As much as I don't like using Windows for my main purposes, it does have it's uses. Plus, I'd like my wife to be able to use it when her laptop isn't in reach. 
I don't know exactly what I've done here, so if anyone could walk me through what needs to be done to fix it, that would be fantastic . . . apparently for all my reading and research, there's still more to be had.

 Yes the 1st partition is the reformat, but I notice that it is a little smaller then mine, the good thing is that you have purchased the licence for xp it is rightfully yours so even if the reformat is broken I am pretty sure ethier acer or MS will provide a copy to get you set back up, probably Acer. This is a worse case scenario which I think your not at yet. This is the sort of problem that you will learn from and me to now isn't this just slightly frustrating but yet kind of exhilarating, in that the control is in your hands in the end. So I would see if we can get some others involved as far as getting the simplest solution.

---

### Post by CheshireMac on 2009-10-18
Okay Wilee . . . you sound like you know what;s going on here .  . , Unfortunately, I'm quite new to harddrive issues, and there's always a ton of new acronyms when you get into new areas. 
I hope you don't mind my asking, but could you walk me through what you think is the best course of action here? Thanks very much for the help, by the way. You're leading the blind right now. ;)

---

### Post by wilee-nilee on 2009-10-18
You also might have the option of if your still in the return period to just return it play dumb and start with a new aspire and stay away from that manual partitioning let the install usb  do the voodoo that it does so well. When I installed the 1st linux I shrunk the xp to 40 gigs left the rest open and did a side by side install using the slider on the GUI to set the partitioning. I have never had much luck with editing grub and manually partitioning basically because I know the computer programs are set up to auto-partition for you. Your problem is fixable and is a good learning situation but if your like me in wanting ease of travel and just getting it done this scenario is a possibility. So if you decide to do this make sure you boot back into xp after resizing letting it do the disc check then restart into xp and defrag before you install Jaunty or even better I like the Koala netbook remix, but I would wait until the koala is a released and a little more stable.

---

### Post by wilee-nilee on 2009-10-18
> **CheshireMac said:**
> Okay Wilee . . . you sound like you know what;s going on here .  . , Unfortunately, I'm quite new to harddrive issues, and there's always a ton of new acronyms when you get into new areas. 
I hope you don't mind my asking, but could you walk me through what you think is the best course of action here? Thanks very much for the help, by the way. You're leading the blind right now. ;)

 So not knowing if the reformat needs something that was in the the main xp which would have been the second partition, I am not sure as what to do. If it was me in your position I would play dumb and get a new one if your in the return period. The problem I see here is that not knowing much more then you having the partition numbers go up but not in a logical order seems counterintuitive in my as usual semi-pseudo-logical thinking.   I suppose you could shrink sda3 to the right leaving a open space format it to ntfs then restart the computer say a few hail mary's and click on the rewrite and see if it installs in the ntfs partition, I feel though that there was probably some of linking between the reformat partition and the main xp which makes it all work, so I am not sure if this will work. The main thing I would do is make sure you don't mess with the jaunty install as far as rewriting it unless you install another linux setup in that grub is the main controller for your boot now and personally I would want that ease of travel.  You might wait to call acer help and ask them about the rewriting the main XP running system with the reformat, but I suspect finding somebody there that will understand the conundrum your in and be sympathetic beyond telling you to send it in to have them redo it at a cost and wait is unlikely. That is why I suggest the just play dumb idea, not something I would appreciate as a business owner myself but I suspect you bought your computer from a giant retailer who can deal with it.  I reformatted my acer but I did it from the reformat option in grub rather then from inside XP, and it was a rewrite of the original stock ntfs partition.

---

### Post by wilee-nilee on 2009-10-18
[http://ubuntuforums.org/attachment.php?attachmentid=132285&stc=1&d=1255849173](http://ubuntuforums.org/attachment.php?attachmentid=132285&stc=1&d=1255849173)  I have never attached on the forums but here is what my gparted pic looks like.

---

### Post by CheshireMac on 2009-10-18
Okay, so I've attempted the menu.list changes to no avail. I'm wary of playing with gparted without a little guidance here. 
Wilee, your guidance was appreciated, but I'm not sure what you meant for the partition alterations.
Just to clarify, as it stands right now, I don't have an XP cd, nor do I have a cd drive, even if I had the cd. 
I'm just hoping that I'm able to get XP back up without spending any cash or bringing in any materials other than what I have. 
Again, thanks to Wilee, and if anyone else has thoughts on this issue, I'd love to hear them.

---

### Post by CheshireMac on 2009-10-18
Here's my readout, by the way, for my partitions:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         764     6136798+  12  Compaq diagnostics
/dev/sda3             765       19457   150151522+   5  Extended
/dev/sda5           19436       19457      176683+  82  Linux swap / Solaris
/dev/sda6             765        2631    14996614+  83  Linux

Partition table entries are not in disk order

```
Hope this helps

---

### Post by wilee-nilee on 2009-10-18
So if you look at my screen shot you will see that we both have that 1st fat32 partition that is the recovery information. What I don't know is if the partition that you overwrote had a date link to the 1st one that gives it the authorization to overwrite; IE recover the partition you over wrote. I know this seems confusing but I think your xp is still there I just think you need a ubergeek on the forums or a professional who knows what to do in this situation.  Editing the grub file will not fix the problem the 1st partition has the information to reinstall xp I believe, I just don't know how that works in the way Acer has it set up. With my recovery all I had to do was click on that recovery partition in grub because I had the correct NTFS partition intact with a slightly borked xp original install.  So I think the over writing of the NTFS partition is the problem, as I suggested it may be that all you need to do is setup a NTFS partition right after the fat32 recovery and hit the recovery in grub and it will write to the NTFS partition, but I suspect that this will not work because of lost data in the overwrite. Also when I did a recovery it overwrote the original xp install and left grub as the MBR controller, it didn't revert to the windows bootloader.   I wish I could be of more help here but I have limitations in this area. To a person who knows this stuff it is a easy fix. I believe it is finding somebody who can do it but while worrying about the cost this is a drawback. If I was a professional it looks like a 100$ job about a hours worth of work at the most. Hopefully somebody on the forums will be able to help you for free though, I wish I could give you a definitive set of answers but I am not that skilled.

---

### Post by wilee-nilee on 2009-10-18
So I gave a call to my friend who is certified in MS, Apple, and Linux, and described the problem, everybody needs a friend like this. What he said was that it is possible that there may be a key combination at start up that will get that fat32 partition to boot up and that it may be as simple as getting a ntfs partition right after the fat32 one and have the fat32 recovery write to the ntfs. He described this as a sort of Ninja like skill level of hacking though that he himself is not able to get it done every time or efficiently every time when it does work. So if your computer is in the refund or return time frame; if it was me I would get the Linux stuff off and return it for a new aspire and play dumb. I suspect since nobody has chimed in to help that this is a fairly complex problem since you overwrote the usable ntfs xp partition. There is a mod on here I forget which one who is a netbook user maybe they will see the situation and have a magical answer, I wouldn't hold your breath though. Also I noticed that your fat32 partition is smaller than mine which is 7 gigs I wonder if somewhere in the process that this fat32 partition was resized, my friend said if that is the case then it probably is not going to work as a recovery partition.

---

### Post by wilee-nilee on 2009-10-18
So I went ahead and joined the acer aspire forum and posted your problem there hoping that there might be help there here is a link to the thread. [http://www.aspireoneuser.com/forum/viewtopic.php?f=67&t=18112](http://www.aspireoneuser.com/forum/viewtopic.php?f=67&t=18112)  In the end we all are trying to help each other and this forum has a linux section so check it out. So here is a link to the main page if you want to join. [http://www.aspireoneuser.com/forum/](http://www.aspireoneuser.com/forum/)  And here is the linux section if you can't find it. [http://www.aspireoneuser.com/forum/viewforum.php?f=67](http://www.aspireoneuser.com/forum/viewforum.php?f=67)

---

### Post by wilee-nilee on 2009-10-20
Check the thread at the aspire forum I found a link which may take care of your needs.

---

### Post by sandy8 on 2009-10-20
Hello Willy and Mac.
I always found Linux an interesting technical subject or topic of discussion for me. At first instance even my basic knowledge of Linux also says that some part of memory in windows might be over written that MBR might lost and Windows can't be boot in Mac's Acer. I found this topic very interesting.

---

### Post by wilee-nilee on 2009-10-20
> **sandy8 said:**
> Hello Willy and Mac.
I always found Linux an interesting technical subject or topic of discussion for me. At first instance even my basic knowledge of Linux also says that some part of memory in windows might be over written that MBR might lost and Windows can't be boot in Mac's Acer. I found this topic very interesting.

 It appears that the partition for the acer recovery is still on the HD, the question here is did it get resized so that it is usable at all, and who has the ninja hacking prowess to get it to work. Fortunately I found a free download of the acer xp from acer that looks to be a easy install and can get everything up and running. If the reinstall is done correctly it will probably leave the original restore partition usable again if it is still intact, and leave the OP with a usb set up reinstall that is legit and legal.

---

