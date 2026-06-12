---
title: "40Gig HD only allows 34gigs to be seen"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by Stochastic on 2006-04-14
Hi I've actually got two problems with my newly installed Breezy setup:

1) My secondary HD (an IDE, currently empty) is a 40 gig but even after formatting and repartitioning it with only one partition that takes up all the sectors, both the Disk Utilities program and Nautilus tell me that it has 34.7 Gig of free space.  I don't have the jumper to force 33Gig on (I've checked already).  How do I get Ubuntu to see all 40gig of free space?

2) I have two soundcards, an onboard VIA 82c686A/B rev21 soundcard that is currently set as default and works fine, and a M-Audio Delta44 PCI soundcard (ice1712 driver) that I want to have as my main default card as I do tons of audio stuff through the multi channels.  The M-Audio is recognised by ALSA as a second card but I can't seem to get it to work; I'd like to get it to be the primary one but to even just get it working would be great.

Thanks for any help.

-Eric

---

### Post by Stochastic on 2006-04-14
Oh, and one more item that I'm not sure about with the same system as above:

3) My swap space (1.2 gig on a system with 680mb of ram) is not being used at any point from what gkrellm and gnome system monitor tell me.  Is swap space regularly used?  Do I have it formatted right?  Is a config file missing somewhere?

Thanks.

-Eric

---

### Post by RS3York on 2006-04-14
For problem 1..

Do you know what the actual capacity of your disk is?  Understand that *advertised* disk space is always higher than *actual* disk space because HD manufacturers & PC makers like to pretend that bytes, kilobytes, megabytes etc work on a decimal system when in reality they don't.  

Hard drives, and even some (all?) USB memory drives, are advertised on the premise that 1 billion bytes = 1 gigabyte...But this is an inaccuracy (a lie actually).  Each major "measurement level" is based around 1024X = 1Y.  So in the eyes of your computer...1024 bytes = 1 kilobyte, 1024 kilobytes = 1 megabyte & 1024 megabytes = 1 gigabyte.  This means you'd need about 42,950,000,000 bytes to have a full 40GB recognized by your computer.  Conversely, 40,000,000,000 bytes should be seen as approx 37.25GB by your computer.  Since you mentioned that you're looking at your numbers from within Ubuntu that means you've lost some of your free space to Ubuntu itself (software, swap partition etc.).  This should explain why you only have ~35GB left.

Problem 2...
If you have an option in your BIOS to turn off your onboard sound...I would go that route.  If you can't turn off the onboard sound in your BIOS, then there are a couple other things you can try.  First, test that the second card actually works in Linux (I've had SUSE 10.0 think it recognized my Audigy but it only recognized the family of chips it belonged to).

Install audacity ```
sudo apt-get install audacity
```  
Load a sound
Select 'Preferences' from the 'Edit' menu.
The first option should be "Device" 
In the drop down menus Select "/dev/dsp1" (could be "/dev/dsp2" if ALSA picked up a Modem or other sound device)
Play your sound to see if the card works.

IF the card works then you have a couple options.  
1. Upgrade to Dapper Drake.  There's a nice option under the Sound configuration module that lets you set a default card.

2.  Create the ".asound.rc" file in your home directory (you can use gedit or "Text Editor" for this)

The example, ".asound.rc" looks like this
```

pcm.card0 {
    type hw
    card 0
}
ctl.card0 {
    type hw
    card 0
}

```
Although in your case the card number will probably be "1" not "0".
If you want more details on .asoundrc you can take a look at this site
[http://alsa.opensrc.org/index.php?page=.asoundrc](http://alsa.opensrc.org/index.php?page=.asoundrc) .  

In Ubuntu Dapper Drake there's a newer version of ALSA that also uses a file called ".asoundrc.asoundconf" that is referred to by .asoundrc and so both files use a different setup than the one above. 

Finally, note that in Linux a period before a file or folder as in ".file" means that it's hidden.  So you won't be able to see your .asoundrc file after you make it unless you setup Nautilus to show all hidden files.

Problem 3...
If all you've done is install and use Ubuntu, your swap partition is fine.  If you've been mucking around with all manner of system-wide config files...then I guess it's possible. I suppose you'll just have to get used to an efficient use of your system resourses :D.  If you *really* want to get your swap partition involved just throw a memory intensive session at your computer - open a bunch of programs, encode media etc.

Hope that helps,
RS3York

Edit - Clarity, address 3rd problem

---

### Post by Stochastic on 2006-04-16
For Problem 1:  You're probably right about it's actual space being 37gigs or so, but you're wrong about it having Ubuntu, swap, etc.. on it.  This is my second drive (data only) and I just formatted it into one single partition.   When I run df -h it tells me that the drive is 37gigs in size, has 128MB used and has 35gigs available.  Nautilus shows 34.7gigs available on the drive.  I still would like to somehow get back the full 37gigs... any ideas?

I haven't had time to sit down and go through your ideas for problem 2 yet, and I'll accept your problem 3 explanation for now.  Thanks.

-Eric

---

### Post by RS3York on 2006-05-07
Hmm, the problem could be the filesystem you're using.  Filesystems all lose a portion of your useable space by nature of their design.  Some are better than others, for example ReiserFS, XFS & JFS retain over 99.5% of the available capacity after formatting.  

Others (FAT, ext2, ext3) aren't as good.  However you shouldn't lose 2 gigs over that on a 37 gig partition, not since it's pretty much empty.  Linux stores it's "trash" on each drive.  So if you delete anything from drive 2 it stays in a trash folder on drive 2.  That might be where some of your drive space went.  

Finally, as you accumulate files you'll lose extra space due to filesystem design.  Filesystems tend to break up space in "chunks" of a predesignated size.  FAT32 uses 4kb (if I remember correctly) so lets say you have a 5kb file - it would use 2 chunks, both 4kb in size.  Now the file system won't let a 3kb file take up the remaining space on the 2nd chunk, that space just gets wasted.  This means that your 5kb file actually uses 8kb on your disk.  Multiply that problem by multiple files and you can see how you'd lose a lot of disk space.  Again some filesystems are designed to avoid this problem, ReiserFS is known for this.

However, your disk is near empty so that's not your problem.  If this second drive is mounted as /home then you probably have a bunch of hidden config files.

Otherwise, I really don't have any other ideas on this front.  If you can reformat the drive with a more space efficient filesystem then you should reclaim more of the space on your hard drive.  Use ReiserFS if you plan on having a number of small files, XFS or JFS are better choices if you're going to be managing large files.

Sorry for the long delay in following up!
Good luck.

---

### Post by mips on 2006-05-08
What motherboard & HDD are you using ???

---

