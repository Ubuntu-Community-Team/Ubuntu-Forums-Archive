---
title: "Dell Inspiron 15 5000, specifically Model i5584-5360SLV-PUS"
date: 2019-06-01
forum: Hardware
---

### Post by n4lbl on 2019-06-01
My last couple of Ubuntu installs (years ago) kept me anxious for a while and I'd like to ask about a particular laptop before purchase to look for trouble in advance.  I did go thru the laptop compatibility list back thru mid '16 and didn't learn anything.  Other searches in hardware weren't helpful.

I am looking at a Dell Inspiron 15 5000, specifically Model i5584-5360SLV-PUS.  It can be seen at [https://www.costco.com/.product.100489776.html?&EMID=B2C_2019_0527_MemorialRemail](https://www.costco.com/.product.100489776.html?&EMID=B2C_2019_0527_MemorialRemail)

I need dual boot for infrequent use of Windoze.  My points of concern that I am aware of are 1) it uses an SSD, and 2) it uses Optane memory.  

Is there any advice anyone has for me for my particular points and anything else that I should be asking about?  I am hoping for a very boring install.

Thanks.

---

### Post by cruzer001 on 2019-06-01
Thats a 4core processor with 8 threads, giving you 8 logical cores.  That part I do like :)

With that kind of muscel you should consider taking the time to learn VirtualBox and for a start set up Ubuntu in vBox.

As far as your model goes, I have no experience with it.  My last Dell laptop was a "Precision" with a I7 and it worked great.  Except for the touchpad, which was a pain in the butt to get tweaked out.  And it wasn't a touchscreen.

---

### Post by n4lbl on 2019-06-01
Thanks Cruzer.  I'm not looking for a "seal of approval".  What I wish for is for someone to set my expectations that 1) I likely won't brick it and 2) I won't need a lot of debugging.  The help that I've received here in the past has been wonderful but now I'm both older and less tolerant.

We use Ubuntu >99% of the time.  This machine is for my wife who will only boot Windoze during the Turbotax season and only for a few hours at that.  

If Ubuntu doesn't use the Optane memory at all would be fine with me.  I just want to be sure that it presents no impediments.

thanks,,,

---

### Post by cruzer001 on 2019-06-01
I believe costco has a 30 day return policy.  You can try ubuntu on it without changing anything, using the live dvd.  Maybe thats the route to go.

Edit
I been using Ubuntu since 2008 on Dell/IBM/Lenovo/HP/others and have yet to strike out.  The touch screen on this one would be my main concern.

---

### Post by cruzer001 on 2019-06-02
One last thing, I have seen good reviews about Ubuntu Mate and touch screens.  May want to try it too.

---

### Post by n4lbl on 2019-06-02
Actually my current laptop, a HP Pavilion Notebook 15- Y1N95UA#ABA has a touchscreen that works fine with 18.04 and previous Ubuntus.  In the '60s thru the '80s terminals had CRT coatings that were very distracting if someone left fingerprints on them.  I still haven't made peace with touchscreens!

---

### Post by cruzer001 on 2019-06-03
HP business laptops are solid laptops IMO. I just purchased one about two months ago, a EliteBook.  I have parts laying around, so I turned into a dual SSD setup.  Windows on one Ubuntu on the other.  I did want a touchscreen, but opted for this one instead, the price was right.

Dell 15 3000 series can come with Ubuntu installed.  So I say your good with a 5000.

[https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-3000-series-laptop-ubuntu-edition/spd/inspiron-15-3551-laptop-ubuntu](https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-3000-series-laptop-ubuntu-edition/spd/inspiron-15-3551-laptop-ubuntu)

---

### Post by cruzer001 on 2019-06-03
I just had a look at the dell community.

[https://www.dell.com/community/forums/searchpage/tab/message?filter=location&q=inspiron%2015%205000%20ubuntu&location=category:English&collapse_discussion=true](https://www.dell.com/community/forums/searchpage/tab/message?filter=location&q=inspiron%2015%205000%20ubuntu&location=category:English&collapse_discussion=true)

---

### Post by n4lbl on 2019-06-03
Thank you again Cruzer.  I hadn't seen that, but I'd bet that anything >2 years old, no matter what the label say it is, is really a different machine.

thanks again,,,

---

### Post by cruzer001 on 2019-06-03
Please post back with the results of this venture :D

---

### Post by oldfred on 2019-06-03
Dell typically works.
If very new with newer hardware, it takes a bit before all drivers are included in distribution. And then you may need newest kernel & version of Ubuntu.

All Dells seem to need UEFI update & SSD firmware update. (Even new systems)
And drives changed from RAID/Intel SRT to AHCI.
Some may need boot parameter(s). particularly if nVidia video.
       Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)

---

### Post by cruzer001 on 2019-06-03
Just last year I stumbled across a Ubuntu compatibility package at the Dell site and installed that to my then in use Dell.  As I recall it had touchpad and touchscreen modifications.  I can no longer find that package.

---

### Post by oldfred on 2019-06-03
Dell has or used to have Sputnik which was the new drivers for a new system. Those were then included in later kernels or Ubuntu versions.
Not sure if newer Sputnik available or not.

       Dell XPS 13 9380 Developer Edition Now Available, Shipping With Ubuntu 18.04 LTS
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-13-9380-Developer](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-13-9380-Developer)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by n4lbl on 2019-06-03
> **oldfred said:**
> Dell typically works.
If very new with newer hardware, it takes a bit before all drivers are included in distribution. And then you may need newest kernel & version of Ubuntu.

... 

That is what I was looking for.  I'm willing to work and agonize until it works, but I wanted my expectations set that I'm likely to succeed.

Oldfred, you've helped me before and I thank you again.

And Cruzer, thank you too,

---

### Post by gpfdave on 2019-08-18
Cruzer:
Another option is if you're running Win 10 Pro you'll have hyper-v manager and they've included a base install of Ubuntu 18 that uses native proc, ram, video etc.  Instead of running a virtual instance of a processor and an assigned amount of RAM through V-box.

I've really enjoyed this option.

---

