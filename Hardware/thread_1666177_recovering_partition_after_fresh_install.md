---
title: "recovering partition after fresh install"
date: 2011-01-13
forum: Hardware
---

### Post by jahau on 2011-01-13
So I have a bit of a problem now. A few days ago my ssd on my laptop gave trouble with the filesystem. I tried a few tips and tricks, but none helped, so I opted to hand the machine over to an "expert" to see if he could recover my data.

Now it turns out that he merely "found" the data on my functioning 16gig SD-card, and made a clean install of ubuntu on my ssd...

Now my question is: can i somehow roll-back the fresh install, or in some other way get to the data that was on my ssd before the guy installed ubuntu, or is the data completly gone from the reformatting of the fs in connection with the fresh install?

Hope you can help - there is quite a lot of data i's rather like to get back.

-Jacob

---

### Post by Kirboosy on 2011-01-13
**Foremost**

 Foremost is a command-line tool which can recover files from a number of filesystems, including fat, ext3 and NTFS. It can be installed and run from the live cd. 
Boot from the live cd and then enable the universe repository and install foremost: 
Use [any method]("https://help.ubuntu.com/community/InstallingSoftware") to install the following package:


Exert taken from [here]("https://help.ubuntu.com/community/DataRecovery")

Its about half way down the page...

---

