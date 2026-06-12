---
title: "Multiple Hard Drives and Operating Systems?"
date: 2010-06-08
forum: Hardware
---

### Post by Nick_Jinn on 2010-06-08
The first part might sound like a noob question, the rest of it less so.


How does one go about having multiple hard drives without using RAID? Completely separate hard drives? Not splitting up the same files between them.

how does this affect the load order when you have multiple operating systems on multiple hard drives?

My other question is this.....Can I have two operating systems operating at once, like in virtual box or some other program, and have one running from one HD and the other from the other? Use the Swap areas as virtual memory to load the desktops?

Have one show up as a windows inside the other? Maybe dedicate a certain limited amount of RAM to one and then to the other?

---

### Post by Revolutionary101 on 2010-06-08
You just plug your hard drives into your computer and make sure RAID settings are turned off in your BIOS. That will let you access the hard drives as separate drives.

The rest I have no clue about so I will let someone else handle that part.

---

### Post by Nick_Jinn on 2010-06-08
Thanks. I wouldnt have thought to disable RAID in the bios. That was a help.

---

### Post by Nick_Jinn on 2010-06-08
I like your tag line. I dont know if I would call it a virus so much as a scam though. Its a big money making scam where they sell you solutions to problems they create just to sell them to you.

Instead of making the best OS for the consumer, they make the best OS for the corporations to market to you, disabling and interfering with anything free. They even have a media player that will report you for playing downloaded songs, even if you already heard them on the radio or owned the CD before you downloaded it (legally entitling you to downloading a backup)...and the annoying advertisements and constant pop ups. **** microsoft.

---

### Post by Revolutionary101 on 2010-06-08
> **Nick_Jinn said:**
> I like your tag line. I dont know if I would call it a virus so much as a scam though. Its a big money making scam where they sell you solutions to problems they create just to sell them to you.

I call it a virus because once new computer users use it all their life they develop a need for it (or a so called infection). That is why Microsoft gives so many discounts to schools on Windows so they can "indoctrinate" kids into using Windows. Once people get used to it businesses add to the problem by making their products "Windows only". I would continue on with my rant about the evil Microsoft empire, but I feel it would distract from the point of this thread.

---

### Post by cascade9 on 2010-06-09
> **Nick_Jinn said:**
> 
How does one go about having multiple hard drives without using RAID? Completely separate hard drives? Not splitting up the same files between them.

Pretty easy really, just install the drives, boot up, and then put whatever OS you want on whatever drive. 

> **Nick_Jinn said:**
> 
how does this affect the load order when you have multiple operating systems on multiple hard drives?

This where it gets fun. Depending on what order you install things, and what OSes you are running, it can be complex...or easy. 

(just making this up an example) Lets say you have 3 HDDs- sda (A seagate ST-XXXX), sdb (A western digital WDC-XXXX) and sdc (a hitachi HT-XXXX). 

You install ubuntu 10.04 on sda. If you adjust the boot order from 'boot from CD' to 'boot from sda' then on booting up, you will boot 10.04. (BTW, it wont be 'boot from sda' in the BIOS, it will be 'boot from ST-XXXX'). 

Next up, you install winXP on sdb (WDC-XXXX) WinXP wont know anything about the linux system, even if 10.04 is installed on sda and the drive connected, and the only way to boot into winXP would be to change the boot order from sda to sdb. 

Now, just to finish things off, you decide to install 10.10 on sdc (HT-XXXX). If sda and sdb are conencted, 10.10 should detect 10.04 and WinXP nd put options to boot from them into grub.  

So, when you go into the BIOS and change boot order, if you boot from sda you will only get 10.04, sdb you will only get winXP, and with sdc then you will get the option (VIA grub) to boot to 10.04, winXP or 10.10). 

If all the drives are hooked up, no matter what you boot from, 10.04 WinXP and 10.10 should see all the drives/partitions. 

> **Nick_Jinn said:**
> 
My other question is this.....Can I have two operating systems operating at once, like in virtual box or some other program, and have one running from one HD and the other from the other? Use the Swap areas as virtual memory to load the desktops?

Have one show up as a windows inside the other? Maybe dedicate a certain limited amount of RAM to one and then to the other?

As far as I know, the only way to have 2 OSes at once is one within the other with virtualbox, etc. There is no way I know of to load 2 seperate OSes at once as seperate entities.

---

