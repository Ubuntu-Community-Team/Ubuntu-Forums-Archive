---
title: "Which best velocity in hard drive? 7200 or 5400 rpm"
date: 2018-12-22
forum: Hardware
---

### Post by sed_faster on 2018-12-22
Hello folks,

I watched this video: [https://www.youtube.com/watch?v=k4Faau_r7Rs](https://www.youtube.com/watch?v=k4Faau_r7Rs)
Now I know which difference exist between this two velocity. But when I should I choose 7200 or 5400? In other words when I have interesting send all information, all at once (5400), rather than, make small submissions?

Ok, If I be worried with energy, heating and noisy I will choose a 5400 rpm. But if I'm not worried about it!? The main factor will be the performance the write and read of the data. I haven't knowledge enough to can find the environment where I need send the information in small package instead send the information in unique package.

I intend use the WD (Western Digital) Blue to ubuntu server. I know the WD Red the best option to system NAS. But I don't have money to invest in this segment :(

Thanks

---

### Post by pqwoerituytrueiwoq on 2018-12-23
This is probably a lot more technical than you were expecting, but...

There is more than just RPMs to determine read/wires speeds of mechanical drives
The density of the platters (the disk that stores data) also matters, think about it like a record player
so if you make the disk spin at 2x you have doubled the read speed, however if you instead shove 2x data into the same space you have done the same thing
just cause a drive is 7200RPM does not make it faster than a 5400RPM drive, same for 10,000RPM, you also want a denser platter, this is why a old 40GB 7200 RPM HDD is slower than a 1TB 5400RPM HDD
there is also the form factor of the disk and the larger the diameter of the platter, the outer edge holds more data than the inner sections as there is more surface area, this gives the 3.5" form factor a advantage over the 2.5" form factor, and there is more vertical space to fit platters
hard drives also have multiple platters, less platters means there is more space between them if something goes a hair out of spec it will not hit a platter and damage the drive

given equal platter density/diameter, firmware, cache, flash nand, and controller this will give the best performance
Pure SSD > SSHD (7,200RPM) > SSHD (5,400RPM) > 10,000RPM HDD > 7200RPM HDD > 5400RPM HDD

SSDs have become much more affordable lately and are expected to becomes even cheaper over the 1st quarter of 2019

when comparing SSDs the Que depth of 1 matters the most for normal users
lots of SSD will show numbers higher than what intel's optane SSDs offer, but the Que depth of 1 and access time is far better it also claims to handle more wire cycles (not sure what has more wire cycles per dollar at this time, which is more important, the controller also plays a factor here)
for most consumers a SSD is a SSD, they will not notice a difference in performance outside of extremes like loading a 60GB game on a sata II SSD verses a PCIE x4 M.2 SSD

If you want a product recommendation, a budget, use case, and needed storage capacity would be needed

---

### Post by Autodave on 2018-12-23
+1 with  [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("https://ubuntuforums.org/member.php?u=865458").  Get a smaller SSD (120G) and install the operating system on that.  Get a bigger spinner drive to keep all your pics, music, documents, etc on.

---

### Post by sed_faster on 2018-12-23
> **pqwoerituytrueiwoq said:**
> This is probably a lot more technical than you were expecting, but...

There is more than just RPMs to determine read/wires speeds of mechanical drives
The density of the platters (the disk that stores data) also matters, think about it like a record player
so if you make the disk spin at 2x you have doubled the read speed, however if you instead shove 2x data into the same space you have done the same thing
just cause a drive is 7200RPM does not make it faster than a 5400RPM drive, same for 10,000RPM, you also want a denser platter, this is why a old 40GB 7200 RPM HDD is slower than a 1TB 5400RPM HDD
there is also the form factor of the disk and the larger the diameter of the platter, the outer edge holds more data than the inner sections as there is more surface area, this gives the 3.5" form factor a advantage over the 2.5" form factor, and there is more vertical space to fit platters
hard drives also have multiple platters, less platters means there is more space between them if something goes a hair out of spec it will not hit a platter and damage the drive

given equal platter density/diameter, firmware, cache, flash nand, and controller this will give the best performance
Pure SSD > SSHD (7,200RPM) > SSHD (5,400RPM) > 10,000RPM HDD > 7200RPM HDD > 5400RPM HDD

SSDs have become much more affordable lately and are expected to becomes even cheaper over the 1st quarter of 2019

when comparing SSDs the Que depth of 1 matters the most for normal users
lots of SSD will show numbers higher than what intel's optane SSDs offer, but the Que depth of 1 and access time is far better it also claims to handle more wire cycles (not sure what has more wire cycles per dollar at this time, which is more important, the controller also plays a factor here)
for most consumers a SSD is a SSD, they will not notice a difference in performance outside of extremes like loading a 60GB game on a sata II SSD verses a PCIE x4 M.2 SSD

If you want a product recommendation, a budget, use case, and needed storage capacity would be needed

Thanks to your reply.

> 
Pure SSD > SSHD (7,200RPM) > SSHD (5,400RPM) > 10,000RPM HDD > 7200RPM HDD > 5400RPM HDD

According to your text the parameter velocity depends on various (more complex) factors. But in this phrase I put order growing all technology. I can assume the 7200rpm will be best 5400rpm?

> 
If you want a product recommendation, a budget, use case, and needed storage capacity would be needed

The difference price between 7200rpm and 5400rpm it is $20. This hard drives will storage documents (pdf and office), movies, images and other stuff. I will use this hard drives under SO Ubuntu Server. This solutions will works in a home network and the resquest from and to server will be very small. But the velocity to access data (write and read) this is an important factor.

Thanks

**Edit1**
My native language isn't English. Therefore I may not perceive very well certain phrases. Thanks

---

### Post by Autodave on 2018-12-23
First of all, your English is quite understandable. :-)

I think that you are over-thinking this way too much.  The differences in these are going to be so small that I doubt that you will be able to tell the difference.

---

### Post by pqwoerituytrueiwoq on 2018-12-23
You did not mention how much storage space you will need
You can get a 120GB SSD for a mere $20 [https://www.newegg.com/Product/Product.aspx?Item=N82E16820331047](https://www.newegg.com/Product/Product.aspx?Item=N82E16820331047)

The only real case from the content types you mentioned  where speed could be a issue would be moves and this would be very unlikely as i doubt you are dealing with raw 4k videos, then i think you would want 4 drives in raid 10 or a few SSDs as the use or RAW 4k videos would mean you are clearly a content creator and you wold probably want better than gigiabit networking hardware

If your videos are no more than 2.4GB per minute of content it does not matter at all, just get enough storage to suite your needs
for a reference my WDC WD10EZEX-21M2NA0 (WD Blue 1TB 7200RPM) drive would be just fine for video playback of 6GB per minute of content, but this is assuming it is serving a single device, if your moves use that kind of space you would probably want a larger drive
my WDC WD5000AAKX-001CA0 (WD Blue 7200RPM 500GB) drive would much slower a only being reliable for 3.6GB per minute

now my SSD on the other hand would be fine for 48GB per minute, hover this is after it is bottle necked my the M.2 PICe x2 slot it is installed into, its true speeds would be closer to 3 times that
this drive would not be suitable for this use case as 1 minute of content would consume about 100% of the storage capacity :lolflag:

The largest video i have on my system would be about 0.9GB per minute, so lets assume my slower 500GB 7200 RPM HDD was 5400RPM, its speed would drive about 30% it would handle about 2.5GB per minute, well more than enough to handle that 1080p video i have

---

### Post by sed_faster on 2018-12-23
Thanks to your advices.

I will need 2TB. For this I am thinking two of this models WD10EZEX (7200rpm) or WD10EZRZ (5400rpm). After I read your suggest and googled about this topic I am thinking choose version 5400rpm. Because the environment will be an server desktop (with ubuntu server as I said) and I think maybe the version with slowly speed will be better to the system. (my cost with energy maybe reduce :)

Like I was said the difference between price it is $20. And the 1800rpm less (7200-5400) maybe significant in the disc's usage time. I don't know if this subject is related but if the platters spin less the hard drive will last longer. Right?

**Note:**
My knowledge with system raid is it very pour. I am thinking install this two hard drives and implement the DIY system RAID, through rsync. I use a script with rsync program to guarantee the disc have the same (mirror) and after that I use sha256sum to compare all files in both hard drives. I run this command to guarantee all files were well-formed.

In the future I will need read more about routines backup. In this forums I learned which process mirror isn't a process backup. Because if a file is corrupted it will be copy corrupted to second disc. Maybe I need draw a script were I can supervision all healthy files and after backup them to the second drive.

My environment is as follows:

1-laptop to work;
2-Oldest PC as NAS with two hard drives (will be) over ubuntu server in my network;
3-Through my laptop I will send new files to NAS;

In this third step I don't know how should I proceed. But maybe we should finish this thread and after that I will post my question over process to do my backup system :D

---

### Post by pqwoerituytrueiwoq on 2018-12-23
If you are worried with power a SSD uses less, here is a [1TB SSD]("https://www.newegg.com/Product/Product.aspx?Item=N82E16820331115") (cheapest i saw on newegg)
If you are planning on using 1 drive as a backup you would only have 1TB of storage
Also raid is NOT A BACKUP, a proper backup would have the drive not be powered up at all times
you could use a hot swap bay to temporally context a drive for backup, use a external USB 3 enclosure, or e-sata
i have 2 trayless hot swap bays in my system, that i got for around 10 to 12$ each
a really cheap way to temporarily connect a backup hdd for updating a backup would be to put a DPST toggle switch on the power feed, wire it to the Yellow and Red wires to turn the drive on/off, you can cut up a molex to sata cable to do make this
the only cheaper way is to unplug the drive's power while it is not in use after taking the side panel off the system

as far as 5400RPM being more reliable that 7200RPM i do not think that matters, look at the WD black drives with there 2.5 times better warranty, they are all 7200RPM
WD blue 5400RPM are what used to be known as WD green inteli-power drives, these had a worse failure rate as far as know, possibly cause the design was new and in-perfected
i put a Samsung 1TB 7200RPM HDD in my neighbor's system, he leaves the system on 24/7 and the drive has not failed yet (at least 5 years ago)

if you are really concerned with power, you should consider this: [https://www.newegg.com/Product/Product.aspx?Item=N82E16817151198](https://www.newegg.com/Product/Product.aspx?Item=N82E16817151198) ($150 after rebate)
* [https://en.wikipedia.org/wiki/80_Plus#Efficiency_level_certifications](https://en.wikipedia.org/wiki/80_Plus#Efficiency_level_certifications) (92% efficiency has a high premium cost)
of coarse you could use something similar to a raspberry pi in deign that sips power all day (A RPi is not used for a real nas system, due to I/O limitations)

Personally for backup i have my important stuff synced with ownCloud running on my raspberry pi which also syncs with my laptop giving me 3 copies if my data, but i do not have the best backup practices

If the only purpose of your nas is to be a backup for your laptop, it would be more cost effective to use a USB3 HDD and update it weekly/monthly, personally i would do this with cp -a on a live session so if my main drive fails i can copy it to the new drive and install grub and be on my way
I REALLY should quit being so tight and get a 2TB HDD and do this
*the word tight can be used like this to refer to someone who is unwilling to spend money

---

