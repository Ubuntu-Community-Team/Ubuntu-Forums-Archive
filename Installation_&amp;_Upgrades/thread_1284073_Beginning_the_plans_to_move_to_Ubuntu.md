---
title: "Beginning the plans to move to Ubuntu"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by lvirden on 2009-10-06
I've a Sony Vaio laptop that I've left running the original OS while the warrenty is active. That time is about over now and I'm ready to make a move.

While I have been attempting to make copies of important bits off the drive, as well as doing normal Windows backups, I am relatively new to the move from one OS to another and was wondering.

In an ideal world, what I would really like to be able to do is install Ubuntu beside the existing files, using the existing folders as my data folders. I could delete some of the applications from that area that I had installed for testing, but keep it around so that if there were some problem that resulted in me needing to send the laptop in for repair, the original OS was still on it. 

The laptop didn't come with install disks, so it isn't like I'd be able to reinstall it if there were some big issue.

The problem with all of this, of course, is that there's only so much space on the disk anyways. I can off load the pictures and music and that's going to free up quite a bit. I'm just not certain whether there will be enough for both Ubuntu to run comfortably or not.

I'd love to hear from others who have considered similar situations, to hear what you decided and how things went.

Also, I've been hearing wonderful things about this upcoming release of Ubuntu. I've been considering holding off the move until it is out and "settled in". Any comments on that idea?

---

### Post by enomis on 2009-10-06
Hi lvirden,

A few comments:

1. I would strongly recommend that you do not only backup "bits of important data", but all your data. You never know what you could miss in the future should you lose your data. An external hard drive is the best choice for this purpose. If you do not have one, buy one. You can always use it in the future to store your pictures or other data that you do not access on a regular basis.

2. It is definitely possible to install Ubuntu beside your existing data and even beside your current OS. In fact, especially if you are new to the ubuntu world, I would recommend a dual boot ubuntu/old os (which might be vista or winxp). In this way you should have at least four partitions: one for your old os, one for your data, and two for ubuntu (/ and swap). If you do this, then you are able to 1. choose the os you want to use at boot, 2. access your data from both os.

3. Even if you do not have install disks for your netbook, there should be a hidden partition or hidden directories that should enable you to restore the original os. Just make sure that you do not touch them when you install ubuntu, as you might need in the future if things go bad.

4. Free space. Ubuntu needs much less space than vista. I would say that you need approximately 10-15GB for the main ubuntu partition and about 1-2GB for the swap, depending on the size of your RAM (if the swap is too small, you might not be able to hibernate the pc). Given the size of the hard drive of current notebooks, it should not be hard to free that space!

5. If you are not in a hurry, I would wait for the next release. It will spare you an upgrade when it comes out. Just wait for a couple of weeks after it comes out to make sure that there are no major problems with your notebook and then give it a go.

Basically, the previous comments come from my own experience of switching from winxp/vista to ubuntu. I now happily use ubuntu and have almost forgot that win is still on my hd... it might seem a waste of space, but I feel safer this way (given the fact that unfortunately ubuntu is not 100% compatible with my notebook).

Best of luck with your switch!

---

### Post by lvirden on 2009-10-06
> **enomis said:**
> Hi lvirden,

A few comments:

1. I would strongly recommend that you do not only backup "bits of important data", but all your data. You never know what you could miss in the future should you lose your data. An external hard drive is the best choice for this purpose. If you do not have one, buy one. You can always use it in the future to store your pictures or other data that you do not access on a regular basis.

2. It is definitely possible to install Ubuntu beside your existing data and even beside your current OS. In fact, especially if you are new to the ubuntu world, I would recommend a dual boot ubuntu/old os (which might be vista or winxp). In this way you should have at least four partitions: one for your old os, one for your data, and two for ubuntu (/ and swap). If you do this, then you are able to 1. choose the os you want to use at boot, 2. access your data from both os.

3. Even if you do not have install disks for your netbook, there should be a hidden partition or hidden directories that should enable you to restore the original os. Just make sure that you do not touch them when you install ubuntu, as you might need in the future if things go bad.

4. Free space. Ubuntu needs much less space than vista. I would say that you need approximately 10-15GB for the main ubuntu partition and about 1-2GB for the swap, depending on the size of your RAM (if the swap is too small, you might not be able to hibernate the pc). Given the size of the hard drive of current notebooks, it should not be hard to free that space!

5. If you are not in a hurry, I would wait for the next release. It will spare you an upgrade when it comes out. Just wait for a couple of weeks after it comes out to make sure that there are no major problems with your notebook and then give it a go.

Basically, the previous comments come from my own experience of switching from winxp/vista to ubuntu. I now happily use ubuntu and have almost forgot that win is still on my hd... it might seem a waste of space, but I feel safer this way (given the fact that unfortunately ubuntu is not 100% compatible with my notebook).

Best of luck with your switch!


Thank you for your comments.

1. While I have an external hard disk, it is being used right now for the windows machine's backups, so there really isn't room for everyone on the window machines. However, I certainly understand your point. If I'm waiting anyways, I'll save up to buy one of those nifty 1-2 terabyte external drives then spend a couple of days copying all that windows stuff over. When I talked about copying over bits of stuff, what I meant was copying the folders containing the pictures, videos, mp3s - stuff like that which I really really don't want to lose. I ought to just create some sort of separate disk to hold that type of stuff that any machine could access...

2. If I create the / and swap partitions for ubuntu, where does the user's disk usage go? I presume I need a third partition for it, right?

3. Thanks for the comment. If from Ubuntu I can access the area where windows keeps its data, then the only reason I might need to touch the files is to see if I can throw enough stuff away to get more space for the ubuntu partitions, and I'll probably try to do that before hands anyways.

4. The machine has 4 gb of memory, so i'll need at least 4 gb for swap, right? Should I plan on more than that?

5. The only hurry is that I'd like to get ubuntu on and become comfortable with it before some stupid trojan/spyware/virus gets by the various programs I'm now using and does real damage to my stuff. I really hate the idea that at any time I could end up with a paper weight instead of a usable machine.

I really appreciate your comments - getting feedback from someone living with this type of setup makes it easier to move forward.

:guitar:

---

### Post by Bartender on 2009-10-06
You got some spare cash?  

I have an Acer laptop that I dual-booted with 8.10.  The original drive was 240GB @ 5400 rpm.  On a whim, I bought a bigger and faster laptop HDD, plugged it in, and installed 9.04.  Swapping the drives only takes about five minutes.

For a while I was swapping back and forth, but I began to worry about stripping out the tiny screws that secure the laptop's bottom panel.  So I've just been running the faster Linux drive lately.  We have an XP desktop for things that "must" be done in Windows, so leaving the Ubuntu drive in the laptop has not been a big deal.

Just wanted to toss that idea out there.  It's one way to avoid any chance of messing up the vista drive.

---

### Post by avacado on 2009-10-06
I have the luxury of both laptop and desktop.
I left windows on the laptop for my wife but to be honest I never use it now.
I started double booting ubuntu within windows but it stopped working twice and I felt the instability was caused by windows . works better on its own anyway.
 
Why would you need to keep the old OS for services? Out of warrantee...
There will be a license sticker somewhere and the repairer can reload windows using that.
I was in the habit of reloading windows from scratch every six months or so when a virus slipped past Norton - takes HOURS!
 
You May be able to load ubuntu onto a USB drive and then boot from that.
Better still, chuck windows altogether.
I figure if it won't work in ubuntu, it isn't worth having.

---

### Post by LinLux451 on 2009-10-06
In an ideal world of desktop computers, you could have two drives, and not mess with partitions... AGHAST! Ubu can read fat files, so if you had a desktop with a small drive, just install ubuntu on the small drive, then just read all of your old files, off the old drive with your windows still 100% intact. Indeed, the bad part of partitioning is not being able to mount one drive twice...

---

### Post by PrePenguin on 2009-10-06
By the way the laptop enables you to make your own install disk A.K.A Recovery disk its just embedded on a hidden partiotion . Another way for these computer companies to save money not sending disk.. Hit F-10 repeatedly on boot-up will give you this option depending on the laptop brand this could be F-11 etc.

---

### Post by enomis on 2009-10-07
I would advise against replacing the hdd to change the os, as this may cause physical and possibly irreversible damage.

I agree that the best thing would be to have two hdd instead of partitioning one single hdd. However, I am afraid that this is impossible on a notebook. Therefore, partitioning is the only solution (actually, not the only, but the best in my opinion).

Speaking of partitions, you do not need a separate partition for user's data. You can use your old partition where you were storing your data under win, as ubuntu can read and write on fat and ntfs. For example, my notebook had two partitions when I bought it: one for vista and the other for user data. To install ubuntu, I shrank the vista partition and I created only two other partitions: the swap and the root. Now I have four partitions and I use the original user partition as my current user partition under ubuntu. Note that I can still access this partition from vista if I boot from win. There are more "sophisticated" set-up for the partitions for ubuntu, but this one works fine (and it has worked on my old notebook with dual boot with xp as well).

The only tip I would give in this case is to shrink the vista partition before starting the installation wizard of ubuntu. Just run ubuntu from live cd, shrink the vista partition and leave empty the newly freed space. Then run the installation wizard of ubuntu and tell him to use all the empty space and dual boot. The wizard will take care of creating the swap and the root partition for ubuntu. In theory you could shrink the vista partition from the wizard as well, but it never worked very well for me.

About the size for the swap: it is unlikely that alle the four gb of ram will be in use when you will hibernate. I would say that a swap of 2gb should be enough. In any case I think that it should be possible to resize the swap partition even after the installation, but I've never done it, so I can't guarantee...

Hope this helps, cheers

---

