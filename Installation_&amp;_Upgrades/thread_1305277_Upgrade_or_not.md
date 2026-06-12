---
title: "Upgrade or not?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by ex-windowuser on 2009-10-29
I have been reading the post about the upgrade and there seems to be alot of bugs on 9.10.  I just got into Ubuntu @ 2 weeks ago and finally got everything running the way I want so I don't need a "clean" install.  Should I wait for all the bug to be remedied and just stay with 9.04 since I have no problems with it.  Also what is the big benefit with 9.10?

---

### Post by flipper9 on 2009-10-29
If you installed 9.04 with the EXT4 disk format, then you could probably wait awhile and then do an upgrade and receive all the speed benefits that Karmic brings since it uses the EXT4 format.

If you didn't use EXT4, but chose the default EXT3 disk format, when you upgrade to 9.10 you won't have the disk upgraded automatically to EXT4.  You can manually convert it, but you still won't see the speed benefits.  In this case, I'd recommend doing a clean install of 9.10 either now or later, in which case you'll start fresh with the EXT4 format and gain all of the speed benefits that it provides.

---

### Post by skompier on 2009-10-29
> **ex-windowuser said:**
> I have been reading the post about the upgrade and there seems to be alot of bugs on 9.10.  I just got into Ubuntu @ 2 weeks ago and finally got everything running the way I want so I don't need a "clean" install.  Should I wait for all the bug to be remedied and just stay with 9.04 since I have no problems with it.  Also what is the big benefit with 9.10?

If 9.04 is setup and working as you like...then there's no compelling reason to upgrade. I never upgrade immediately when a new version gets released. I always wait a few weeks or months. Enjoy 9.04 for awhile...I know I am.

---

### Post by ex-windowuser on 2009-10-29
I believe I went with the default ext3.  How can I change it to ext4 later?  Can you tell me how?  I am still learning on the "command" area where you use the terminal.  Also how can I check if I did use the default ext3?  Thanks in advance.

---

### Post by cwbar_1 on 2009-10-29
My 2 cents worth.  9.04 is a long-term supported release.  With that said, if you have the system as you like it, and you are a short time user, stick with what you have until you are totally comfortable with Ubuntu.  Then, and only then, venture out and try the newer versions.
Good luck!

To see your ext status.  System > Administration > Disk Utility  Click on your Ubuntu partition and read the info.

---

### Post by skompier on 2009-10-29
> **ex-windowuser said:**
> I believe I went with the default ext3.  How can I change it to ext4 later?

You can only change from Ext3 to Ext4 by re-formatting. Then you'll have to do a clean install again.

---

### Post by flipper9 on 2009-10-29
> **cwbar_1 said:**
> My 2 cents worth.  9.04 is a long-term supported release.  With that said, if you have the system as you like it, and you are a short time user, stick with what you have until you are totally comfortable with Ubuntu.  Then, and only then, venture out and try the newer versions.
Good luck!

To see your ext status.  System > Administration > Disk Utility  Click on your Ubuntu partition and read the info.

Sorry, but 9.04 (Jaunty) is not an LTS release...8.04(Hardy) was the last LTS release. 

Though, if you are happy on whatever particular release you are on, then no need to upgrade unless you want to.

---

### Post by cwbar_1 on 2009-10-29
Ext3 to Ext4 info.
[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

---

### Post by flipper9 on 2009-10-29
> **skompier said:**
> You can only change from Ext3 to Ext4 by re-formatting. Then you'll have to do a clean install again.

No; you CAN do an in-place upgrade of a disk from Ext3 to Ext4...however, the existing data structures will not take advantage of the speed improvements.

---

### Post by cwbar_1 on 2009-10-29
> **flipper9 said:**
> Sorry, but 9.04 (Jaunty) is not an LTS release...8.04(Hardy) was the last LTS release. 

Though, if you are happy on whatever particular release you are on, then no need to upgrade unless you want to.

I stand corrected!

---

### Post by flipper9 on 2009-10-29
> **skompier said:**
> If 9.04 is setup and working as you like...then there's no compelling reason to upgrade. I never upgrade immediately when a new version gets released. I always wait a few weeks or months. Enjoy 9.04 for awhile...I know I am.

Honestly, the only real reason I jumped on 9.10 (Karmic) was the graphics performance with Intel graphics on 9.04 (Jaunty) was horrible.  We were forced to upgrade to have a stable system.  But if Jaunty is working, stick with it unless you like to install operating systems (and reinstall potentially, like me...hehe)

---

### Post by skompier on 2009-10-29
> **flipper9 said:**
> No; you CAN do an in-place upgrade of a disk from Ext3 to Ext4...however, the existing data structures will not take advantage of the speed improvements.

That's kind of what I meant. I just didn't explicitly state that. So the only way to get ALL the benefits of Ext4 is to reformat.

---

### Post by dhavalbbhatt on 2009-10-29
> **cwbar_1 said:**
> My 2 cents worth.  9.04 is a long-term supported release.  

Ubuntu 9.04 is NOT a Long Term Support release and neither is Ubuntu 9.10. The next LTS release will be Ubuntu 10.04 - the last one was Ubuntu 8.04. 

With that being said, if you like your current system don't worry too much about disk performance and keep using Ubuntu 9.04 for a while - at least till the time you really want to move to the next version of Ubuntu. The move to ext4 should only be worthwhile to you if you have extremely large files or you perform a lot of read/write to your disk. The boot up times are somewhat faster in ext4, but they are fast enough in ext3 as well - again, understand, "fast" is relative. If you have been used to the Windows environment, then you know, Ubuntu ext3 is a lot faster booting up than Windows NTFS. 

I would say, use Ubuntu 9.04 till 10.04 comes out next year - that will be a LTS version and will have addressed most bugs.

---

### Post by ex-windowuser on 2009-10-29
Thanks for all the info guys.  I think I will stay with 9.04. Like one of the reply, I like to upgrade also BUT on this one, I am going to wait.

---

### Post by Clancy_s on 2009-10-29
> **flipper9 said:**
> If you didn't use EXT4, but chose the default EXT3 disk format, when you upgrade to 9.10 you won't have the disk upgraded automatically to EXT4.  You can manually convert it, but you still won't see the speed benefits.  In this case, I'd recommend doing a clean install of 9.10 either now or later, in which case you'll start fresh with the EXT4 format and gain all of the speed benefits that it provides.

To get those benefits I take it I'll have to reformat all my data partitions, not just the / and /home ones?

Oy!

---

### Post by flipper9 on 2009-10-29
> **Clancy_s said:**
> To get those benefits I take it I'll have to reformat all my data partitions, not just the / and /home ones?

Oy!

Backing up your data is pretty easy nowadays with USB Keys and external drives.  Formatting takes but a minute or two.  I find it better sometimes to just "bite the bullet", backup your data, remove everything from the hard drive (delete all partitions) and just start over.  Saves all the headaches of "upgrading" and trying to make stuff work.  Sometimes a fresh start is better.

---

### Post by Orfintain on 2009-10-29
Oh goody ! I get to back everything up and see if any new problems get fixed and what new ones arrive ...

I really need to buy a external hard-rive

---

### Post by pablo180 on 2009-10-29
> **ex-windowuser said:**
> I have been reading the post about the upgrade and there seems to be alot of bugs on 9.10.  I just got into Ubuntu @ 2 weeks ago and finally got everything running the way I want so I don't need a "clean" install.  Should I wait for all the bug to be remedied and just stay with 9.04 since I have no problems with it.  Also what is the big benefit with 9.10?

If everything is working you should definitely stick with it, if I had more sense I'd still be using Hardy, or at least Intrepid. 

As for the bug fixes, they are rarely fixed until the next release, which as a few people have mentioned, tend to bring in more problems as well as fix bugs.

---

### Post by 65 mustang on 2009-10-29
I would wait a month or 2 before upgrading.  See how the forums look then upgrade.  The big annoyances will be fixed by then i bet.

---

### Post by prj44 on 2009-10-30
I would avoid the Upgrade option.  My sound card is toast and I can't get to my Network or the internet.  Now I have a choice: fresh install of 9.10, or a fresh install of 9.04.  I'm going for what worked well.

I have been impressed with successive versions of Ubuntu.  Now, I'm not so sure.  I don't think this release is quite cooked yet. I would beware.

---

### Post by plurworldinc on 2009-10-30
Since this is the first day 9.10 is finally out, I recommend you play it by ear and wait a few days. Now I have found that 9.04 was a wonderful distro and easy to learn with. 9.10 on the other hand has a couple of tiny things that you may have to get use too. But since your new and will have support up to 2010, wait and see what happens !!!.

  I did a fresh install today, and I can tell you since I am somewhat a noob myself , it has been a very , very long and slow day.

   But that is to be expected when everyone is downloading at once....

---

### Post by raven01 on 2009-10-30
yea well i have been having issues with the live cd reconizing my monitor settings. sooo i think ill wait until some bugs get fixed  :/ to bad. i was really looking forward to having it up and running tonight. not to mention that my new netbook will have to wait as well.

---

