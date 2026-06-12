---
title: "DDrescue and trying not to commit suicide :/"
date: 2013-07-17
forum: Hardware
---

### Post by ad5os on 2013-07-17
So for the past week or so I have been working on recovering a 1.5TB Hitachi (POS) drive that has been failing on my windows workstation.  So I took a 2TB drive and systemrescueCD distro on a USB stick with a backspace.  Well it started off slow as I figured and after 375Gig the drive just is giving all sorts of I/O buffer errors and the Bytes coming are slow in the range of just several K a Second if that.... And quite honestly I am not sure how accurate that is anyway.  

I am just looking for the best command lines to give DDrescue to do whatever it would take to rescue this drive... i dont care if it takes months... I just need to know whats the best way to eventually get back all that data... time is no object.  I just dont want to spend several weeks waiting on a drive only to get NOTHING on the rescue disk. 

Right now I just run it as 

ddrescue -f -n -v -v -v -v /dev/sda /dev/sdb logfile 

I have tried -d and -R and they only messed things up more making the drive even that much more slower...

When I cntrl-alt 12 and view the kernel messgaes I am getting a lot of I/O logical block errors and whatnot... does that mean that the Bytes that I am getting are actually being read off the disk or just junk?  The only way I can get thigns to work is setting AHCI in bios but would IDE be better?  Also I have a J-Micron Raid SATA raid card.. would that be better than the ICH9 SATA controller for errors and commands?  I dont see what the difference would be.



On a side note... Could it be just a faulty logic board?  I took off mine and the other drive that is nearly identical and the bad drive was missing the thermal pad to connect it to the body of the hard drive.. I am nearly certain this drive has been very hot since it has been in a non cooled USB cradle.

Any advice would be appreciated! :D

---

