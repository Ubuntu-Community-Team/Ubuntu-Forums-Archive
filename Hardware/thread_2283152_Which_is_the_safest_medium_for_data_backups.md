---
title: "Which is the safest medium for data backups"
date: 2015-06-19
forum: Hardware
---

### Post by papakota on 2015-06-19
Hello!
                              I want to hear your opinion about the  safest way to store backups of data. Let's take 3 mediums -- external  USB3 HD, USB flash drives and DVDs. I personally stick to Verbatim DVD  +RW. The backup costs about twice cheaper than USB3 flash drive (per  GB). Though it's a little bit more hassle with the discs... As per  external USB3 HD's...  First of all, it's a little bit of an investment  upfront. More importantly, what kinda bothers me a little is the notion  that after all, a hard disk is a hard disk. It has mechanical parts,  vacuum inside, integrated electronics. Too many things can go wrong and  magically you can wake up some not so beautiful morning and your disk is  dead!
                              Let's not discuss SSD's here please. They're still a little beyond my budget. 
                              Thx!

---

### Post by weatherman2 on 2015-06-19
Hard drives seem to be the most practical and reliable.  Of course, they can fail.  DVDs can deteriorate over time and become unreadable, too.  No medium is 100% safe.

The key is redundancy.  If you are planning to backup say 2TB of data, buy two 2TB drives (or even three) and make them exact copies of each other.  Don't keep both connected at the same time (in case of an electrical problem) - backup your data to the first one, remove it, and make the same backup to the second (I prefer rsync for file backup).  The chances of both your backup drives failing at the same time is much smaller than one of them failing.

Use S.M.A.R.T. to monitor your hard drives' health.  It could give you an early warning of developing drive problems.

I've always found burning DVD discs a time consuming, error prone process.  Verifying your burned discs immediately to make sure they burned successfully should be a requirement - and that increases the time needed even more.  It seems not worth the effort anymore when hard drives have become so cheap per MB and when DVD discs are still not even 10GB per disc.  If you have a lot of data, it could take days to make backups.  You can backup to hard drive in just a few minutes if you use something like rsync that only copies the changes in data.

---

### Post by v3.xx on 2015-06-19
I have dual HDDs backing up each other and an extra layer of protection using (free) on-line storage.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=free+online+storage&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=free+online+storage&sa=Search&cof=FORID:9)

---

### Post by tgalati4 on 2015-06-19
Stone and chisel is good for at least 2000 years.  Pencil and paper is good for at least 500 years.  Everything else is less than 20 years.  Many recommend the 3-2-1 strategy.  3 copies of really, really, important files.  Use 2 different physical devices.  One backup should be off-site.  

I would read the reviews on the web.  There are lots of opinions.  I would get a professional digital camera, CF card reader/backup system.  They have many slots and I would invest in quality, professional-level CF cards used for digital cameras and video.  Then write some fancy rsync scripts to perform daily/weekly backups.  Monthly backups could be on an internal hard disk.  External disk throughput generally isn't fast enough for large backups.  Rotate your CF cards and keep some of them in a fireproof container or store them offsite.

Many use off-site storage services as well.  You have to weigh your privacy vs the importance of the data before uploading everything to the cloud.

---

### Post by papakota on 2015-06-19
> **tgalati4 said:**
> 
Many use off-site storage services as well.  You have to weight your privacy vs the importance of the data before uploading everything to the cloud.

Uploading truecrypt volumes easily solves any privacy issues. Go open them :-)
The home Internet channel's speed is a bottleneck, I would say...

---

### Post by papakota on 2015-06-19
Thank you all for your opinions! It was interesting to read.

---

