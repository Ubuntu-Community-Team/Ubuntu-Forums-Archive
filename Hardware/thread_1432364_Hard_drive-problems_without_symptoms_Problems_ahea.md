---
title: "Hard drive-problems without symptoms? Problems ahead?"
date: 2010-03-17
forum: Hardware
---

### Post by Demask on 2010-03-17
Just installed Ubuntu 9.10 on my 1-year old laptop the other day. Partioned the disk manually and everything went smoothly. Haven't noticed any hard drive-related problems running 9.10 (or Windows 7, Vista or Linux Mint 8 for that matter). But Ubuntu's disk utility says I've got some bad sectors, 7 of them to be precise. Found some help in the IRC-channels running "sudo fsck -pcfv /dev/sda1" from the live cd. Output looks like this: ```
ubuntu@ubuntu:~$ sudo fsck -pcfv /dev/sda1
fsck from util-linux-ng 2.16
/dev/sda1: Updating bad block inode.

  154111 inodes used (10.10%)
     117 non-contiguous files (0.1%)
     140 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 131146/17
  958626 blocks used (15.71%)
       0 bad blocks
       1 large file

  106606 regular files
   18491 directories
      68 character device files
      26 block device files
       1 fifo
     389 links
   28900 symbolic links (22833 fast symbolic links)
      10 sockets
--------
  154491 files
ubuntu@ubuntu:~$ sudo fsck -pcfv /dev/sda2
fsck from util-linux-ng 2.16
/dev/sda2: Updating bad block inode.

    4594 inodes used (0.03%)
      50 non-contiguous files (1.1%)
       3 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 4573/9
 1381747 blocks used (1.95%)
      44 bad blocks
       1 large file

    4001 regular files
     582 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       2 symbolic links (2 fast symbolic links)
       0 sockets
--------
    4585 files

```

Also got a tip about installing and running "Smartmontools" (and Gsmartcontrol), did that and tried to run a test. But all that happens is that the test result reads "Completed with read failure" and no real output data. This sounded quite dramatic to me, so I downloaded WD's Data lifeguard diagnostics CD. However this CD fails to start properly, something about how it can't find the license agreement and prompts me for the proper disc (and the license is there, burned the disc twice, same problem). 

This boils down to my question: How worried should I be about the state of my HD? New HD's comes cheap today so buying a new one wouldn't be that much of a hassle. But it would be nice to know if this kind of wear-and-tear is normal, or if it's "the beginning of the end", to phrase it a bit more dramatically.... 

Any comments would be appreciated, if this is in the wrong part of the forum, or to incoherent to make sense, then I apologise. It's late, and I should be sleeping...

[Update]
After checking the temperature of the HD i discovered it runs at a reasonably constant temperature of 62 degrees celsius. The recommended maximum from the manufacturer (Western Digital Scorpio Blue 320GB 5400rpm) is 60 degrees celsius. I haven't checked the temperature with any other OS than Ubuntu 9.10, but after a quick look around the forums I belive this high temperature could be caused by Ubuntu itself. Does this make sense? Or am I drawing the wrong conclusion?

---

### Post by quixote on 2010-03-19
I believe recently made hard disks (ie last few years) automatically mark off bad sectors and don't use them.  So the bad sectors are there, but they don't hurt anything.  If you check every once in a while, say once a month, and every time there's a whole new bunch of bad sectors, that is a symptom of a gradually failing drive.  But a bad sector now and again is nothing to worry about unless you start getting filesystem errors.  (Eg messages during bootup to run fsck.)

The temperature issue is a bit more worrisome.  You're not so far out of range that it's an emergency, but the hotter any electronics run the less time they last.  I'd suggest putting an extra fan blowing at it, or putting it on a fan cooling pad, until you can find a way to get it to run cooler.

---

### Post by norseman-has-a-laptop on 2010-03-19
also buy a new one just in case because a extra hard drive is always cool beans broah
lol

---

### Post by Demask on 2010-03-19
Having failed to figure out any other reasonable solution, I ordered a new drive. It should arrive on monday and then I'm afraid it might be back to Windows 7 again. I'm having a really hard time understanding why my HD keeps getting so hot. Even now, when all I'm doing is running Firefox, Empathy and Disk Utility it steadily increases up to and just beyond 60 degrees celsius. I've tried to change the power settings so that it will spin down when possible but this doesn't seem to have any effect at all. 

I really like Ubuntu, but I can't risk having a hard drive-failure because of high temperature. This may just be a problem with the Western Digital-drives, I'll have to wait and see when the new Hitachi-drive arrives, it's supposed to be cooler and more energy efficent, so fingers crossed . 

Strangely enough, the disk maintains the same high temperature even when I boot from a live-CD and turn the swap off. This should mean that the HD isn't being used at all, shouldn't it?

---

### Post by Demask on 2010-04-03
Update - Report after new hard drive installtion:

After installing my new 500GB HD from Hitachi (a model that is supposedly designed to run at low temperature). Installed Windows 7 and have run it pretty much without problems for a couple of weeks now. As I had temperature problems in Ubuntu 9.10 I kept close watch on the harddrive's temperature. In windows and running the laptop in "powersave/balanced"-mode the disk feels rather cool (no software to read out temperature I'm afraid). The only time I notice a high temperature is when I play games like Oblivion or Battlefield 2 on "high performance"-mode. (And I think this is related to a higher average temperature on all the other components inside the computercase.) So thinking the problem is resolved, I pop in the Ubunu 9.10 live-cd. And wouldn't you know it, running idle on a live-cd with the processorc at half power and no partition mounted the disk runs at about 50-52 degrees celsius. 

Yes, this is colder than the WD-disk I had before (62 degrees C in Idle), but this disk is only supposed to run at a maximum of 55 degrees C. So even though the disk is not in use, Ubuntu runs it at a noticeably higher temperature than windows. 

I find this very strange since the disk isn't even supposed to be active when running the livecd. Sorry for dwelling on this subject, but I find this problem strange and fascinating. Could it be related to the graphic-circuits running hotter in Ubuntu due to bad drivers? Could some other component be running hotter than it should? 
Note that the computer I'm using (FS Amilo PA3553) does have dual ATI graphic cards that generate a lot of heat when pushed.

---

### Post by quixote on 2010-04-11
There was talk a year or so back about how linux wasn't as good at cooling components or power-saving or battery usage -- a whole bunch of power related issues is what I vaguely remember.  The discussion was that it had been fixed (more or less?).  Maybe the hardware in your computer is particularly susceptible.  Anyway, the point of this is that if you search for those threads, there was stuff in there about drivers, or patches, or kernel modules, or something.

Or, maybe, you'd rather get on with real life and not turn this into a research project?  :biggrin:

---

