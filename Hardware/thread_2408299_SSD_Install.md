---
title: "SSD Install"
date: 2018-12-16
forum: Hardware
---

### Post by vikrantalmelkar on 2018-12-16
Hi All,

I have a Acer Aspire E15-512-C0GA laptop

I am changing the HDD to an 256GB SSD.

is there anything special that I need to do while installing ubuntu 18.04?

thank very much and appreciate all your support

Vik

---

### Post by CatKiller on 2018-12-16
The defaults are fine for SSDs now.

---

### Post by ubname on 2018-12-17
Someone say that it is better to add "noatime" in fstab,
but I do not have the knowledge to say it is true, it will however prevents many writes,
maybe some more experienced SSD user can say some more.

---

### Post by oldfred on 2018-12-17
SSD life is now considered comparable to HDD life. But that can be anywhere from very short to very long.
       [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[URL="http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead"]http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead
      [/URL]hard drive life 
[https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/](https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/) 
    
I do make a few changes, but started with a small SSD in 2011 where many more settings were suggested and still do some of those, whether really needed or not.

I add noatime to fstab mounts.
I do leave some space not used, newer drives may be able to manage that.
I run my own trim daily, but then any recovery of data is lost. I use SSD as boot drive and can reinstall Ubuntu and have good backups. Data is on HDD.
I have lots of RAM (8 on one system and 16 on other), so mount /tmp into RAM with fstab. (can do whether SSD or HDD).
And with lots of RAM, I never use swap, so all the discussion of where swap partition should be is moot. But now Ubuntu uses a swap file.

       [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 
            Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022) 
    [URL="http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead"]
[/URL]

---

