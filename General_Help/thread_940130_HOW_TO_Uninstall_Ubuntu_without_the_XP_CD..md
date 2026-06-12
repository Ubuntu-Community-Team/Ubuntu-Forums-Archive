---
title: "HOW TO: Uninstall Ubuntu without the XP CD."
date: 2008-10-06
forum: General Help
---

### Post by MyNameIsDerek85 on 2008-10-06
**[CENTER]How To: Completely remove Ubuntu manually (no XP disc required)[/CENTER]**

[I]The following tutorial assumes that you are running Windows XP and that Ubuntu is dual booted along side of Windows XP.
[/I]

It&#8217;s a common scenario. You want to uninstall Ubuntu from your hard drive and return to the comfort of XP, but there&#8217;s a problem. It seems the dog ate your XP disc (stupid dog). You call up a friend to borrow his XP disc but it turns out your dog ate his XP disc too! (hungry, why wait?)

Fortunately, there&#8217;s a solution and it&#8217;s not as complicated as you might think! In this tutorial, we&#8217;re going to completely remove Ubuntu manually (and I&#8217;m not talking about sticking our hands up Fido&#8217;s butt, either. Gloves or no gloves, that&#8217;s dirty). 

We&#8217;re going to need to be in XP. If you aren&#8217;t already in XP, restart your computer and boot into XP.

**STEP 1 &#8211; &#8220;No, I don&#8217;t want no Grub&#8221;**

First, we&#8217;re going to need a very tiny program called &#8220;MbrFix&#8221; which can be found at [http://www.download.com/MbrFix/3000-2094_4-10485990.html](http://www.download.com/MbrFix/3000-2094_4-10485990.html)

Download the .zip file and extract the files to your desktop. 

That was simple. Ready for some fun? Great! 

Now, press the start button and go to &#8220;Run&#8221;. Type &#8220;CMD&#8221; in the box and click &#8220;OK&#8221;. Bet you didn&#8217;t think you&#8217;d have to see one of these again. 

Drag the MbrFix.exe file from your desktop into the MSDOS box.

type in &#8220; /drive 0 fixmbr  /yes&#8221; and hit enter. (note: &#8220;drive 0&#8221; is usually the &#8220;drive&#8221; that XP is installed on. If you have any doubts, type in &#8220; /?&#8221; to see a list of help features or type in &#8220; /drive 0 driveinfo&#8221; for information on &#8220;drive 0&#8221;).

Restart your computer. If you followed these instructions correctly, You should not see the &#8220;Grub&#8221; screen at the beginning. That was painless. 

**STEP 2 &#8211; &#8220;It&#8217;s so hard to say Goodbye to what we had&#8230;&#8221;**

Now, we&#8217;re going to remove Ubuntu from your hard drive. So, head on over to the start menu and click &#8220;Run&#8221; again. This time, we&#8217;re going to type &#8220;compmgmt.msc&#8221; into the box and click &#8220;ok&#8221;. 

Go to &#8220;Storage&#8221; then &#8220;Disk Management&#8221;. Try to navigate the partition that Ubuntu is installed on. Usually, it&#8217;s anything that doesn&#8217;t say &#8220;NTFS&#8221; after it. Right click on the partition(s) that Ubuntu is stored on and click &#8220;Delete&#8221; until you have a single box/partition. Then right click the box/partition and click on &#8220;Format&#8221;. 

Restart your computer.

**Step 3 (Optional) &#8211;** &#8220;How do I merge the Ubuntu partition with the C:/ drive or a second drive?&#8217;&#8217;

One way to accomplish this task is to use Partition magic, which I&#8217;m unfamiliar with so I&#8217;m not going to go into too much detail.

If you have a &#8220;second hard drive&#8221; that you want to merge with the new partition (for example a DATA (D:/) drive) then there&#8217;s a simple solution. Make sure all the data you want to keep in your second hard drive is backed up to your C:/ drive or your desktop. Go back to your &#8220;Computer Management&#8221; screen > Storage > Disk Management and right click on the &#8220;DATA (D:/)&#8221; drive. Then click &#8220;delete&#8221;. Do the same with the new partition that once had Ubuntu on it. This should make it come up as &#8220;Unallocated space&#8221;. Right click on the &#8220;unallocated space&#8221; and click &#8220;Format&#8221;. Then it will ask you if you want it to be a &#8220;primary drive&#8221; (or something like that). You do want it to be. Click next. Choose the letter that you want the drive to be (&#8220;D&#8221;) and make sure it&#8217;s a &#8220;NTFS&#8221; file system. Click next. Write in &#8220;DATA&#8221; in the text field if you want it to mimic your old drive and click next. After it&#8217;s done formatting, restart and you&#8217;re finished.

**Step 4** (Optional) &#8211; &#8220;The Ubuntu Live CD left behind an option in my Windows boot menu&#8221;.

This is once again a simple fix. 

Go to &#8220;My computer&#8221; and click on &#8220;C:/&#8221;. Go to Tools > Folder Options > View. Make sure that &#8216;Show hidden files and folders&#8221; is selected and that &#8220;hide protected operating system files (Recommended)&#8221; is unchecked. 

Find &#8220;boot.ini&#8221; in the &#8220;C:/&#8221; (note: It would be safe to make a back-up of this file in case you mess something up. Screwing up here could cause Windows to not even load, so be very careful to read these instructions carefully) Right click on the file and go to properties. Make sure that &#8220;Read only&#8221; is not checked. Open the file (with notepad if asked) and delete the line that says &#8220;C:/wubilder.mbr = &#8220;Ubuntu&#8221; (or something similar to that). It&#8217;s usually the very last line. File > Save, Close and Restart. 

**Step 5 &#8211; Enjoy Windows, Traitor.** (Extremely Optional) Just Kidding, but seriously, hope this helps.

---

