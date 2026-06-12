---
title: "Dell Inspiron 910 (Mini 9) Ubuntu Pre-install - READ BEFORE BUYING"
date: 2008-10-17
forum: Hardware
---

### Post by dalrympm on 2008-10-17
Hi,

I want to share my recent experience with my purchase of a Dell Mini 9 that came with 8.04 pre-installed.  Before I get to the bad stuff, let me say that the machine itself is lovely to look at and reasonably well built.  Contrary to some other posts I've seen, the camera functions perfectly well with the Dell included software.  The screen is amazing for the price and size, and hopefully it will become a functional part of my arsenal of computers.

My basic configuration is:
16 GB SSD
1 GB RAM
Built-in Camera

Now for the bad...

Startup was your normal Ubuntu install startup with nothing special to report.  The problem I had occurred when I took a look at my available space.  It read 600 MB available.  For a 16 GB drive, that sure didn't seem right.  A df -h reported that the drive was a 3.5 GB drive.  Quite confused I looked around for additional partitions etc... and found nothing.  

Now it gets worse...

So I call Dell for support and finally get on the line with someone.  They confirmed that I should in fact have a 16 GB drive.  The agent then asked me to go to "Start -> My Computer". Really?  I then explained, "This is Linux, it is not Windows, do you understand that?"  To which the agent replied "Ok, do you mind if I do a remote view of your computer?"  I replied "Of course not, how do we do that?" The agent says "Please start Internet Explorer."  Really?  "Um, I really don't think you understand, this is not a Windows PC!"  

After some debate as to what to do next, the agent decides to send me a replacement SSD.  I emphaticaly ask "This disc will come pre-installed with the OS, right?  There is no CD drive on this machine so I can't easily do a new installation."  The agent replies in a slight miffed tone that "Yes, it will come pre-installed, is that alright?" Ok, sure....

And then it gets ugly...

The part arrives two days later (today).  I crack open the bottom of the Mini (pretty easy, two screws and a little prying), pop out the old drive, pop in the new one and fire it up.  I noticed that the part numbers are the same so I'm not expecting any relief.  At boot, I get that lovely message "Operating System not found".  I wasn't really surprised but I'm a little ticked off.  So, I call Dell support and believe it or not, I'm told that I "have to buy the external CD-ROM drive so I can re-install the OS."  Are you kidding me?  In order to use the system as I bought it, they're saying I have to buy something else.  Sorry but that's just flat out wrong and it definitely shouldn't be the way they're handling this problem.  They're turning a technical problem into a bait and switch and that's just not right.

So, I speak to the floor manager and he finally explains to me what is going on.  When they're building these machines, no matter what the configuration, they're using the same disc image.  So, even though I do have a 16 GB drive, I can't use the 12.5 GB that isn't allocated.  They're apparently working on a solution but don't have one so until then, they want people to buy their external CD drives.  Not cool.

I'm pretty sure I can figure out a way to get my full 16GB by using a USB key to rebuild the system or by repartitioning or something.  But I bought the machine with Ubuntu pre-installed for a reason, I don't want to do this.  They have now arranged to send me a replacement 910 in the next 7-10 days but they make no gurantees that it will be any better.  I have the patience for this and in the meantime, I'll see if I can't get more out of the one I have now.

Conclusion

While I applaud Dell for offering Ubuntu as a pre-installed option, they have some work to do.

- Dell needs to either educate its support staff on Ubuntu or use the Service Tags to route Ubuntu support to properly trained staff.
- Dell should be ashamed of trying to turn their technical issues into a revenue opportunity.
- People out there wanting to buy one of these Mini 9's should probably wait a little while.

---

### Post by aysiu on 2008-10-17
Supposedly the 4 GB issue is fixed for future units:
[http://www.dellideastorm.com/article/show/10093388/Use_the_entire_drive_for_the_Ubuntu_installation_not_just_4_GB_if_the_drive_is_bigger](http://www.dellideastorm.com/article/show/10093388/Use_the_entire_drive_for_the_Ubuntu_installation_not_just_4_GB_if_the_drive_is_bigger)

---

### Post by dalrympm on 2008-10-17
Nice, thanks for the update.  Good to see the lines of communication inside Dell are wide open.  Guess I'll wait for the replacement to come instead of spending time making a LiveUSB key.

---

### Post by bishop9226 on 2008-10-17
Installation issue: Ubuntu and XP are installed easily via USB drive, which are about $5 these days.  You don't need an optical drive.  

It is sloppy of them to send the other 12gigs unallocated, you can still fix it w/o much headache though, just get an ubuntu installation iso, mount the files to a usb stick using daemon tools lite and boot off the usb (set bios to usb boot enabled).

dell support - eh, just be happy they are shipping it with linux, you wont get much support from people who just know how to read from a script

i ordered mine with 512 ram, the 16gig drive (which was a mistake because i couldve spent a little more and got a bigger ssd from newegg), and ubuntu.  i got a sandisk ultra ii sdhc 16gig, 2gigs of g.skill ram, so ill have 32gigs, 2gig ram, and im going to throw xp pro on it via usb:).  

> **dalrympm said:**
> Hi,

I want to share my recent experience with my purchase of a Dell Mini 9 that came with 8.04 pre-installed.  Before I get to the bad stuff, let me say that the machine itself is lovely to look at and reasonably well built.  Contrary to some other posts I've seen, the camera functions perfectly well with the Dell included software.  The screen is amazing for the price and size, and hopefully it will become a functional part of my arsenal of computers.

My basic configuration is:
16 GB SSD
1 GB RAM
Built-in Camera

Now for the bad...

Startup was your normal Ubuntu install startup with nothing special to report.  The problem I had occurred when I took a look at my available space.  It read 600 MB available.  For a 16 GB drive, that sure didn't seem right.  A df -h reported that the drive was a 3.5 GB drive.  Quite confused I looked around for additional partitions etc... and found nothing.  

Now it gets worse...

So I call Dell for support and finally get on the line with someone.  They confirmed that I should in fact have a 16 GB drive.  The agent then asked me to go to "Start -> My Computer". Really?  I then explained, "This is Linux, it is not Windows, do you understand that?"  To which the agent replied "Ok, do you mind if I do a remote view of your computer?"  I replied "Of course not, how do we do that?" The agent says "Please start Internet Explorer."  Really?  "Um, I really don't think you understand, this is not a Windows PC!"  

After some debate as to what to do next, the agent decides to send me a replacement SSD.  I emphaticaly ask "This disc will come pre-installed with the OS, right?  There is no CD drive on this machine so I can't easily do a new installation."  The agent replies in a slight miffed tone that "Yes, it will come pre-installed, is that alright?" Ok, sure....

And then it gets ugly...

The part arrives two days later (today).  I crack open the bottom of the Mini (pretty easy, two screws and a little prying), pop out the old drive, pop in the new one and fire it up.  I noticed that the part numbers are the same so I'm not expecting any relief.  At boot, I get that lovely message "Operating System not found".  I wasn't really surprised but I'm a little ticked off.  So, I call Dell support and believe it or not, I'm told that I "have to buy the external CD-ROM drive so I can re-install the OS."  Are you kidding me?  In order to use the system as I bought it, they're saying I have to buy something else.  Sorry but that's just flat out wrong and it definitely shouldn't be the way they're handling this problem.  They're turning a technical problem into a bait and switch and that's just not right.

So, I speak to the floor manager and he finally explains to me what is going on.  When they're building these machines, no matter what the configuration, they're using the same disc image.  So, even though I do have a 16 GB drive, I can't use the 12.5 GB that isn't allocated.  They're apparently working on a solution but don't have one so until then, they want people to buy their external CD drives.  Not cool.

I'm pretty sure I can figure out a way to get my full 16GB by using a USB key to rebuild the system or by repartitioning or something.  But I bought the machine with Ubuntu pre-installed for a reason, I don't want to do this.  They have now arranged to send me a replacement 910 in the next 7-10 days but they make no gurantees that it will be any better.  I have the patience for this and in the meantime, I'll see if I can't get more out of the one I have now.

Conclusion

While I applaud Dell for offering Ubuntu as a pre-installed option, they have some work to do.

- Dell needs to either educate its support staff on Ubuntu or use the Service Tags to route Ubuntu support to properly trained staff.
- Dell should be ashamed of trying to turn their technical issues into a revenue opportunity.
- People out there wanting to buy one of these Mini 9's should probably wait a little while.

---

