---
title: "Care and Feeding of SSD specific to Intel 520 series?"
date: 2012-04-23
forum: Hardware
---

### Post by jcllings on 2012-04-23
I'm looking for information specific to this very new hardware, if anyone has it. Machine is a System76 build out. According to the product info, it has a MTBF of 5 years and a 5 year manufacturer's warranty, so I guess they actually believe their own statistic. It's a 240G drive. I've never run one of these on Windows before, so I don't know what the maintenance toolkit does exactly, but if we could figure that out or if someone had already done it, the results might be enlightening. 

Thanks guys. Tho me a bone if you can.

---

### Post by Mykro on 2012-04-30
Very interested in this question as I too am considering buying this drive (120GB) to use with 12.04.

This link is not promising :(   [http://askubuntu.com/questions/124632/what-would-cause-ssd-to-become-not-detectable](http://askubuntu.com/questions/124632/what-would-cause-ssd-to-become-not-detectable)

---

### Post by jcllings on 2012-04-30
> **Mykro said:**
> Very interested in this question as I too am considering buying this drive (120GB) to use with 12.04.

This link is not promising :(   [http://askubuntu.com/questions/124632/what-would-cause-ssd-to-become-not-detectable](http://askubuntu.com/questions/124632/what-would-cause-ssd-to-become-not-detectable)

Regarding the link above, System76 would probably know if the above is a problem since they are a Ubuntu Pre-install shop and do testing and stuff. If I had such a drive though, I would contact Intel and ask if it needs to be RMA'ed. They would seem to have a vested interest in answering such questions since they are trying to sell through all the FUD that is out there regarding SSD's. Also the warranty for Intel 520 series drives is pretty good. See below. 

After much poking about and research and asking, what I came up with is that:

1. They (the Intel 520 series SSD's) come with a 5 year manufacturers warranty which seems to indicate that the manufacturer believes the average user can't mess up the product without doing something that is really bad.

2. You should be using the cloud and keeping good backups for stuff that isn't in the cloud and checking in frequently for any code you are writing. This is per Standard Operating Procedure, however. 

3. The technology has evolved as rapidly as one might expect so there is a lot of old information out there. What Intel and System76 told me is that these days you can treat em just like regular drives for the most part.  I also read a white paper written by a storage pro that in a nutshell said that modern SSD's he tested are good for 51 years of being completely overwritten 3 times a day by real time recording software. ...and that is every single bit and byte. 

There are some things I'm not yet clear on but this seemed to be the gist.

Cut 'n paste from Intel's response to my questions:

>Thank you for contacting Intel Technical Support.
>We understand that you would like to know how to manage an Intel SSD, in 
>Linux*
>Please note that after kernel 2.6.33 TRIM is natively done by Linux*, it
>depends from one distribution to the other if they set the flags to work
>or not.
>To verify how to enable or disable this flags you should verify with the
>Ubuntu* communities, also note that HDPARM* and hdat2* are programs that
>can be set to apply TRIM in an SSD.
>HDPARM information is available at:
>[http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/)
>HDAT2/CBL Hard Disk Repair Utility
>[www.hdat2.com/](www.hdat2.com/)

---

