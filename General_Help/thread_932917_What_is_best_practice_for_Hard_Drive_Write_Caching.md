---
title: "What is best practice for Hard Drive Write Caching &amp; Standby Timeout"
date: 2008-09-28
forum: General Help
---

### Post by cyauch on 2008-09-28
Ok, so I have Ubuntu 8.04 Server edition running in the closet.  I use Webmin to admin the box, but am hoping someone can either provide a little more detail, or maybe some 'NO, DON'T DO IT!' experiences on the best to way to configure of these settings.  I'm a Windows Server person, so this is kinda new (the applying of the settings and how they react in Linux, not what they mean / do :-)  )  

First, the drives are all IDE drives (two of them).  One is a 20GB Maxtor, and contains the Linux install.  The other, is a 200 GB drive, and partitioned off into a 4 partitions.  One is for our personal docs, pics, music, etc.  The second is for backup's for the previous.  The third contains misc stuff that can be accessed via FTP, and the 4th partition is currently empty for now.  The server is for home use, and occasionally family / friends will download / upload to the FTP partition, or connect with their laptop when they are visiting.  Other than that, not allot of traffic. 

When I had windows 2003 server installed, I was able to manage the power settings.  What I'd like to do is the same for Linux.  With Webmin, there are settings for adjust Standby Timeouts, Write Caching, Using DMA, etc.  I've looked at Webmin's site, but I know what the terminology means.  I'm looking for real world experience, and what is the best practice for these.  could to great of a standby time out cause info loss or corrupted files?  Etc.  I've compiled a short list of questions.  If anyone could provide their thoughts, I would appreciate it.  Thanks in advance.  

1.  With respect to using DMA (and I'm not a hardware guru), default is OFF, and as Write Caching.  In Windows Server 2003, I've always GPO'd Write Caching to Enabled.  Should I do the same for a Linux network?  (No Windows machines here in the house anymore :-) ). 
 
2. Standby Timeout (i.e Windows Drive Power Save).  Are there any known issues about this?  I'm worried about attempting a write to a drive that has powered down, and doesn't spin up in time to prevent a possible error.  I'm sure this wouldn't happen, but any caveat's I should know about?  

3.  I've read some have had issues with Linux clients reading / writing to a NTFS share, and in some cases, files were corrupted.  Since my server partitions are all Linux, do I have to worry about Windows clients reading / writing to the share(s) and possibly corrupting them?  Is this a non-factor with the latest Linux kernel's? 

I basically want my server to keep its power consumption as low as possible.  Right now, its running wide open.  Linux is new to me, but have played with it for a couple of years.  The past few months I've decided to dump Windows from all our home PC's, and have Unbuntu 8.04 Desktop installed.  Now, I'm attempting to forget my Windows Server 2003 knowledge and optimize a Linux server.  Thanks to anyone who can give some pointers.  Thanks.

---

### Post by fiatguy85 on 2008-12-12
I came across this thread looking for something else and figured I'd give it a shot since no one had.  

> 1. With respect to using DMA (and I'm not a hardware guru), default is OFF, and as Write Caching. In Windows Server 2003, I've always GPO'd Write Caching to Enabled. Should I do the same for a Linux network? (No Windows machines here in the house anymore  ).


I don't know a lot about this myself but here is the community documentation, which explains it and some of the issues [U][here.]("https://help.ubuntu.com/community/DMA")
[/U]
> 2. Standby Timeout (i.e Windows Drive Power Save). Are there any known issues about this? I'm worried about attempting a write to a drive that has powered down, and doesn't spin up in time to prevent a possible error. I'm sure this wouldn't happen, but any caveat's I should know about?

Ubuntu with the laptop mode has this enabled, I believe.  I have been running my laptop with it with no problems.  I don't believe there would be any issue with a server other than that desktop hard drives are not designed to be spun up as many times.  The appropriate time period would be similar to a windows machine.  

> 3. I've read some have had issues with Linux clients reading / writing to a NTFS share, and in some cases, files were corrupted. Since my server partitions are all Linux, do I have to worry about Windows clients reading / writing to the share(s) and possibly corrupting them? Is this a non-factor with the latest Linux kernel's?

If you're also sharing with windows computers, I assume you would use samba.  I haven't heard of any issues with samba and ext3.  I started using nfs for file sharing between linux machines because I think it is much easier to set up, but it is not natively supported by windows if you want your friends to be able to connect from the network.

---

