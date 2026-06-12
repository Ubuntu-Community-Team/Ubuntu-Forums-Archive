---
title: "Replacing 2 hard drives with SSD"
date: 2013-03-23
forum: Hardware
---

### Post by dannyvanderzande on 2013-03-23
I am currently running a linux server, mainly for downloading and backup services, and I'm thinking about buying an SSD drive to replace my root drive.
I have a separate temp drive where downloads are being processed before they are moved to their final destianation on a storage drive.

The root drive contains just the linux system which runs servives like sabnzbd, headphones, etc so I think it doesn't have that much read and write operations once it's booted up. My temp drive just contains temp download data but it does have a lot of read and write operations.
My root drive is 110 GB, my temp drive is 147 GB. I was wondering wether it would be a smart thing to combine these two drives on one SSD?

What do you guys think? Should I combine the two drives on one SSD (which saved me quite a lot of money) or should I buy two separate drives?
Thanks in advance

---

### Post by ahallubuntu on 2013-03-23
Why do you need to replace either drive?  Speed?  Your cheapest best is to buy a 120GB SSD (fairly cheap now) to replace the root drive and leave the other one alone.  You'll get the biggest speed boost of an SSD by replacing the operating system drive and not the temp drive.

If you want to spend a little more money and simplify your life - sure, buy a 500GB SSD and combine drives.  But you probably won't see a big speed benefit vs. replacing only the root drive.

---

### Post by dannyvanderzande on 2013-03-23
I want to replace my drives for the following reasons.
My root drive for speed, and my temp drive because it's one of those old noisy drives. So I thought I'd save myself some money by buying a 256 GB SSD and splitting it into two partitions of 128 GB.

---

### Post by oldfred on 2013-03-23
I only have a desktop, so I do not run any server processes in / that might take more space. But my SSD is 60GB, has two installs each about 27GB. And I use about 9GB of the 27GB for / including /home. But all data is on other drives including some of the hidden data files in /home like thunderbird and firefox. 
If you are running database or other apps form / you may need more space, but a standard install does not need 128GB.

---

### Post by dannyvanderzande on 2013-03-23
My installataion uses about 45 GB including some databases for my server at the moment so I know 128 is a lot of space. Fact is however that if I want to buy one SSD for the two drives together it will have to be a 256 GB because I want at least 100 GB of temp space. So in that case I just simply divided the numbers in two but I could also go for 64 GB main drive and the rest temp..

---

### Post by Scott Goodgame on 2013-03-24
Your money might be better spent this way...
1) keep your existing root drive.... like you said once it's booted you don't use it much
2) create yourself a spinning raid setup for your storage needs
3) use the money you save to make sure your network is fast (gigabit ethernet everywhere)

---

### Post by tgalati4 on 2013-03-24
Another option is to buy more RAM and run freenas or nas4free from a USB stick and buy a cheap green drive that spins down when not in use.  You would be running completely in RAM and only write to the disk when you have files to save.

The configuration is stored on the USB disk, so with a power outage, your system would reboot properly with your mounts intact.

---

