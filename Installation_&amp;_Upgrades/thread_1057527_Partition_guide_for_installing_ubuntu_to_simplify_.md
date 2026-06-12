---
title: "Partition guide for installing ubuntu to simplify future upgrades"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by illurim on 2009-02-01
I'm after a guide (or simply just someone to say do it like this because...) on how to partition my new 1TB drive for a clean install of Ubuntu 8.10 in such a way that I can reduce future upgrade hassles. That is, when the next upgrade of Ubuntu comes out, I want to minimise my pain on upgrading from 8.10 to it.

I have done a fair amount of reading on the topic and I understand some of it, but this really isn't my forte. I freely admit I lack technical understanding of how partitions **really** work and I certainly have very limited understanding of how the Linux file system likes to run (and I don't really want to understand all the ins and outs of it - don't hate me for not caring about the details enough).

I recently installed Ubuntu 8.10, dual booted with my Windows XP installation. I have 2 hard drives and needless to say, it's all a bit messy. I have crap everywhere. 

(Side note for those interested - yes the installation was a breeze and I'm exceptionally satisfied with Ubuntu. There have been so many improvements since my last install 3 or so years ago - kudos to everyone that's helped get it where it is, it really is perfect for me and I cannot thank you enough!)

I have purchased a new 1TB drive to replace the existing 2 drives I have. I'll be using those 2 drives for my Mythbuntu machine.

I want to maintain a dual boot of Ubuntu and Windows **for the moment**. I want to be able to upgrade Ubuntu as easily as possible without having to re-install every time. I understand to do this I should use multiple partitions for various mount points, but I don't really understand sizes or why you use certain mount points. I've tried to understand but I haven't been able to find explanations that make sense in my brain. So, here's what I'm thinking of doing and I'm wondering if someone can either:

a) give me some guidance as to whether I'm totally off base and should rethink and **why - in simple terms!**
or
b) gimme a link to read (I'm happy to read, but as I've said, I'm having trouble finding posts that make it clear to me)

_Proposed Partition Scheme_
**Windows **50GB
**/** 5GB
**/swap** 2GB
*[INDENT]I have 2GB RAM. I've read the 2xRAM rule and I've also read it's not as necessary anymore, but that /swap is still a good idea but you may not get huge benefit from it and it could be wasted space. I'm happy to give up 2GB and be done with it.[/INDENT]*
**/home** *Unsure how much to allocate*
*[INDENT]I'm thinking "what's left" is a good enough way to approach it, but I've also read I could allocate X and simply extend the partition later if I need it so long as it's at the end of the partitions... [/INDENT]*
**/usr** *Is this necessary? What are the benefits? Are there any? I haven't been able to find anything that tells me in a way that makes any sense. I've read this is where some things get installed, but I've also read you can use /home to install apps.*


**Questions**
[LIST]
[*]Have I missed any mount points that I really should use for their own partition?
[*]Should I reconsider sizes of any of the partitions I've listed, and if so do you have any suggestions and why over what I've posted?
[/LIST]

Otherwise, if everything looks good, I guess I'm just after a good old fashioned "Looks fine, don't stress, go for it!".

---

### Post by tuxxy on 2009-02-01
Your windows will be fine at 50GB with NTFS partition.  To make Ubuntu upgrades and future installs hassle free you need 2 partitions, one for your filesystem one for your /home dir.

So at partition stage you will create 2 partitions for Ubuntu both EXT3 format, one will be 10GB for filesystem, this is a generous size for just system files but with 1TB drive you may disagree ;) at installation you will give this partition the mount point / from the drop down menu.

Next is your /home partition this is the big one where you will save all personal files like multimedia files so you make this one as large as possible really, mine currently is 200GB+ :)

---

### Post by illurim on 2009-02-03
Thanks Tuxxy. :)

---

