---
title: "SSD - BIOS does not have AHCI option - does this matter"
date: 2016-03-03
forum: Hardware
---

### Post by mark-reddin on 2016-03-03
Hi
I have also posted this question on the Crucial forum, because it's a Crucial SSD.

I thought I would also ask you guys the question in case it's Ubuntu specific.


I have an 8 year old Sony Vaio VGN-NS10E running Ubuntu 14.04
I have just installed a Crucial BX200 SSD in it and it works great so far.
I read here
 
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

 
that I should change the BIOS setting to AHCI
 
Unfortunately, my BIOS doesn't seem to contain such a setting.  Is this important?
 
Since I am running Ubuntu, updating the BIOS is difficult, but looking at the Sony website, I am not sure if any of the BIOS releases subsequent to mine would give me this setting anyway.
 
Thanks for any advice
Mark

---

### Post by mark-reddin on 2016-03-03
Just to note that I've discovered I am already on the latest release of the BIOS that Sony have available (albeit from 2009).

---

### Post by mark-reddin on 2016-03-03
And I think I've found the answer 

[http://askubuntu.com/questions/254339/am-i-using-ide-or-ahci](http://askubuntu.com/questions/254339/am-i-using-ide-or-ahci)

In my case the output showed ahci, so I think I don't have an issue

---

### Post by weatherman2 on 2016-03-03
I wouldn't worry about it if you've already installed it successfully.  AHCI can be faster and is preferred if you have the choice.  I know I have at least on SSD running in old laptop without AHCI and no issues at all.

---

