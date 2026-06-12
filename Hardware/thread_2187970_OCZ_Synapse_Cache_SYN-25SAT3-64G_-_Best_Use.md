---
title: "OCZ Synapse Cache SYN-25SAT3-64G - Best Use"
date: 2013-11-14
forum: Hardware
---

### Post by dannyboy79 on 2013-11-14
Hello all,
I just received this in a used computer tower and am wondering how best to make use of it. When I looked at it within  a liveusb Ubuntu it only shows up as 32GB, i believe the OCZ software somehow uses the other 32GB and the other 32GB is for caching data. I currently have my Xubuntu 12.04.3 installed on a 40GB HDD, it's split into 14GB for /, 22GB for home and remaining is SWAP. I have read articles like this ([http://www.raid6.com.au/posts/fs_ext4_external_journal/](http://www.raid6.com.au/posts/fs_ext4_external_journal/)) that state to not even mess with flashcache and just use the SSD for external journaling of the ext4 filesystem but I believe my installation is ext3 does that matter? 
Since my main HDD is 40GB I wouldn't be able to clone it onto the 32GB SSD so that's outta the question. Any help or suggestions would be appreciated. 

Or maybe do I do a fresh install and use this new bcache I have read about?

---

### Post by dannyboy79 on 2013-11-22
175 views and not 1 person uses a caching SSD, has setup flashcache or setup bcache? WOW, I guess I may be the first. Going to set it up very soon, bcache that is but first have to see if I can get a 3.10+ kernel for 12.04.3

---

