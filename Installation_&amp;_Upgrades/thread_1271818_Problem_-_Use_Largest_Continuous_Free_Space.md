---
title: "Problem - Use Largest Continuous Free Space"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by Footbag on 2009-09-21
I'm working on my 4th Ubuntu 9.04 dual boot install.  This one is a Vista/Ubuntu dual boot.  That said, all dual boot systems are doing some funky things during install at the prepare disk space. 

I did use Vista's partition tool to free up 30GB of space.  Then I go to install. Maybe I'm not understanding something, but if I highlight "Use largest continuous free space", it appears to give Ubuntu 2.5GB and give vista back all of the free space I had assigned as free space.  

I had a laptop do the same thing and had to go back and fix all of the partitions.  So I'm not going to make the same mistake.  With this install, I'm going to go in an set up my partitions manually, but shouldn't the installer be figuring this out on its own, right?  It seems like most of the walkthroughs use this option, yet it hasn't worked for me yet.  Is this some sort of bug, or am I misusing it?

Right now...
<------Vista 203.6-------><----fre space 29.3GB---->

How the installer is attempting to install it with use largest continuous...
<------Vista 230.4GB--------><--Ubuntu 2.5GB-->

---

### Post by drs305 on 2009-09-21
This problem sounds very similar to, or work the same as, a problem with the "side by side" option in Step 4. If the user accepts the default (does nothing), a 2.5GB partition is created. This default is a known bug that is being worked on.

In Step 4, if "side by side" is selected the user must click on the partition depiction at the bottom of the page and slide the pointer left (increasing the size).

Here is a pic of the slider, and a reference to a post I made about this:
[Step 4, Side by Side, Slider]("http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874")

[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

---

### Post by Footbag on 2009-09-21
So if I use the "use largest" option, and slide the slider, will it re-partition the free space?  The use largest selection doesn't seem to recognize that the free space is on the drive even though it shows up on top.

---

### Post by drs305 on 2009-09-21
> **Footbag said:**
> So if I use the "use largest" option, and slide the slider, will it re-partition the free space?  The use largest selection doesn't seem to recognize that the free space is on the drive even though it shows up on top.

I would not do this until some more users reply. I brought up the "side by side" issue since you mentioned a 2.5GB partition, which is what that option creates. The slider is meant to be used with "side by side" - I can't verify it can be used with any other option.

Using the slider with an option that is supposed to recognize the largest partition isn't something I would do. I would make the partitions outside of the installer in this case and then use the manual option to identify the partitions which I created.

---

### Post by Footbag on 2009-09-21
> **drs305 said:**
> I would not do this until some more users reply. I brought up the "side by side" issue since you mentioned a 2.5GB partition, which is what that option creates. The slider is meant to be used with "side by side" - I can't verify it can be used with any other option.

Using the slider with an option that is supposed to recognize the largest partition isn't something I would do. I would make the partitions outside of the installer in this case and then use the manual option to identify the partitions which I created.

Yes...  I still plan on doing the manual partiiton, just trying to figure out what I did wrong last time.  Or to more thoroughly understand the bug.

---

### Post by D3mon_Spawn on 2009-10-11
same thing with the slider is happening to me to...I go and choose the use continuous free space and by default it puts the Ubuntu portion at 2.5 and makes me use the slider....this whole situation is preventing me from installing ubuntu...is there a way around this??

---

### Post by drs305 on 2009-10-11
> **D3mon_Spawn said:**
> same thing with the slider is happening to me to...I go and choose the use continuous free space and by default it puts the Ubuntu portion at 2.5 and makes me use the slider....this whole situation is preventing me from installing ubuntu...is there a way around this??

I knew about the slider issue with the "side by side with Windows" option but didn't know it affected other options as well. Doesn't the slider move to the left? I think in the original bug reports it *defaulted* to 2.5GB but would let the user move it to make the partition larger (if they knew to do it).

Which version are you trying to install? The 'bug' with the slider was fixed in the Karmic Beta iso but there are indications the devs aren't going to fix the Jaunty iso. You could try using the Karmic Beta iso if that is an acceptable option for you and you can't resolve the slider problem any other way.

Of course, not recognizing any free space isn't a slider issue and the Beta version of Karmic may not fix this problem either. On the other hand, it may have.

---

### Post by D3mon_Spawn on 2009-10-11
> **drs305 said:**
> I knew about the slider issue with the "side by side with Windows" option but didn't know it affected other options as well. Doesn't the slider move to the left? I think in the original bug reports it *defaulted* to 2.5GB but would let the user move it to make the partition larger (if they knew to do it).

Which version are you trying to install? The 'bug' with the slider was fixed in the Karmic Beta iso but there are indications the devs aren't going to fix the Jaunty iso. You could try using the Karmic Beta iso if that is an acceptable option for you and you can't resolve the slider problem any other way.

Of course, not recognizing any free space isn't a slider issue and the Beta version of Karmic may not fix this problem either. On the other hand, it may have.

I'm trying to install Jaunty 9.04. It seems logical that if I just move the slider to the same amount of free space I have it would work, but I don't really wanna risk it, what if something goes wrong.

---

### Post by bulldog on 2009-10-11
Hi D3mon_Spawn,

I should go for the manual way,so you have it in your own hands.
Choose the manual option and create a new partition for / and make it 5-8 GB
Create a small partition for the swap file 1 GB should do it,and if you have room left on your hdd,create a partition for your /home.
If you don't want to create a separate /home,it's recommended to increase the / partition with some GB's. 
If done,select the new partition and mount it as / set to format ext3,mount swap as swap and if you made one,your /home as /home and format it only this time to ext3.
The benefit of a separate /home can be very useful when you have to reinstall or install a new version of ubuntu.

---

### Post by D3mon_Spawn on 2009-10-11
Hmmm...well, I kinda was just going to wait for the next LTS Distro but if I do instal the beta would it be easier to upgrade to Lucid Lynx (10.04 LTS) when it comes out from the beta 9.10?

---

### Post by drs305 on 2009-10-11
> **D3mon_Spawn said:**
> Hmmm...well, I kinda was just going to wait for the next LTS Distro but if I do instal the beta would it be easier to upgrade to Lucid Lynx (10.04 LTS) when it comes out from the beta 9.10?

Are you currently running Hardy? If so, you could upgrade directly to Lynx. If you are trying to install Jaunty as a new install, you would have to upgrade first to Karmic, then to Lynx unless you do a clean install of Lynx when it comes out. 

If you install Karmic beta now, updates would take you to the normal release version of 9.10 when it comes out at the end of the month.

You can upgrade from LTS to LTS, or one release at a time if they aren't LTS.

---

