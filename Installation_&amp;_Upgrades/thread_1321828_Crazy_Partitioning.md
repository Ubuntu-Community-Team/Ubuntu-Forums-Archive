---
title: "Crazy Partitioning"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by iamgeniusrnti on 2009-11-10
So as a newb, I bought me an Acer One D250 Notebook and downloaded UNR to a thumbrive using Uunetbootin (mispelled?).  My intent was to triple boot XP, Ubuntu and BT3.
 
Booted the thumbdrive and started Parted.  Shrunk my XP partition to 40 GB on my 160 GB HD.
 
Then I mapped out partitions as follows:
 
-SDA 1 - 7G - Premade Rescue for XP
-SDA 2 - Primary 40G - XP
-SDA 3 - Primary 30G - Ubuntu
-SDA 4 - Logical
--SDA 5 - Primary 30 G - BT3
--SDA 5 - Linux Swap - 10G
--SDA 6 - NTFS "Shared" - 10G
--30G Empty space I didn't know what to do with because I added my numbers wrong.
 
Installed Ubuntu UNR using guided partitioning without incident.  Both OSs appear to be happy and bootable in GRUB.  Checked swap using free cmd and the swap is active.
 
I didn't load BT3 yet, as a matter of fact, I still need to go download it and do research on any problems I'll have to get it working on my hardware.
 
Then this morning, I had a nagging feeling to check the partitions again.  I don't now why--I just felt something was wrong.
 
So as I ran up the disk manager tool and looked at the screen, I had a flashback of a book I read as a kid called "Best Laid Plans O'Mice and Men" and I was the mouse and Ubuntu was the farmer.  This farmer not only mowed down my plans but he mowed my harddrive as well.
 
For some reason I can't explain, I now have 9 partitions as follows:
 
-SDA 1 - 7G - Premade Rescue for XP
-SDA 2 - Primary 40G - XP
-SDA 3 - 30 GB - Blank, empty
-SDA 4 - Logical
--SDA 5 - 30 GB - Blank, empty
--SDA 6 - 10 GB Swap, I don't think its using this
--SDA 7 -  10 GB "Shared"
--SDA 8 - 30 GB (ext4) Ubuntu
--SDA 9 - 1.4 GB Swap
 
I am nearly psoitive I selected side-by-side install and presumed it would have installed it to SDA3 and picked up SDA6 for the swap.
 
So now what do I do?  If I run BT3 off the USB, is it going to see Ubuntu and pick another partition?

---

### Post by snowpine on 2009-11-10
You chose "guided", so the installer created the partitions it thought it needed (rather than using existing partitions).

It sounds like you know your way around Gparted, so when the time comes to install BT3, just delete the extraneous partitions and use the "manual" install option instead of "guided."

---

### Post by iamgeniusrnti on 2009-11-10
> **snowpine said:**
> You chose "guided", so the installer created the partitions it thought it needed (rather than using existing partitions).
 
It sounds like you know your way around Gparted, so when the time comes to install BT3, just delete the extraneous partitions and use the "manual" install option instead of "guided."
 
I have a good understanding of partitioning from dealing with Windows since Windows 3.0 so the Gparted program was pretty straight forward but the manual install... never done one... if I delete SDA3 and SDA5, leaving it totally unused, it should just drop new partitions in that gap?

---

### Post by snowpine on 2009-11-10
I have never used the BackTrack installer, so I can't say for sure... if it's the same as Ubuntu's, it should have a "Guided: use largest free space option." In which case, yes, you could just delete the extraneous partitions ahead of time and trust the installer to create the partitions it needs in the empty space.

---

### Post by iamgeniusrnti on 2009-11-15
After rearranging my partitions I made the newbish mistake of rebooting the computer only to find Grub2 wouldn't work.  I then spent a day searching the internet and this forum on how to fix Grub only to find that my particular Grub did not accept any of the commands the internet said I should use.

So to fix that problem, using a USB live, I created a tiny partition on the harddrive just big enough to contain another instance of Ubuntu, let it reinstall Grub and badda big, bada boom, I can boot again.

BTW, BT does not come with installers any more.  The Gods proclaimed we should only use it on thumb drives... I am certainly glad they have decided what is best for me and  bestowed upon me all this extra harddrive space

So now that I have a second instance of Ubuntu, I think I will go out, find all the apps BT3 comes with and just install those in Ubuntu.

As for Grub--I know it hates us to play with the grub.cfg file.  I would like to rename some of the items... can I edit that kind of stuff without pissing it off too much?

---

### Post by darkod on 2009-11-15
It's a lot to read but it seems to have info on everything.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

PS. You can also google with the particular question about what you want to change. More and more forums have answers about grub2 now that it's out.

---

### Post by iamgeniusrnti on 2009-11-15
Thanks for the link--I have seen it before and you're right it's a lot to take in.  I'll have to take it to work for when I'm bored.  

The reason I ask the question is I installed Puppy and although Grub will boot it up, it sees it as an "unknown".  Good thing I only have one unknown with an option to rescue said unknown with a... you guessed it... an unknown rescuer!

---

### Post by oldfred on 2009-11-15
These links also have info. You can also copy your puppy entry into 40_custom and edit it to anything you want. You may want to turn off the osprober to prevent duplicate entries.

Grub 2 Title Tweaks Thread
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

[http://members.iinet.net/~herman546/...0Commands.html](http://members.iinet.net/~herman546/...0Commands.html)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"

Of course after any changes:
sudo update-grub

---

### Post by iamgeniusrnti on 2009-11-24
I forgot to jump back here... I finally did the unthinkable and edited the verbiage to say what I wanted it to say.  It didn't seem to argue with me--I think it was too busy worrying about all the other stuff I was poking at!

---

