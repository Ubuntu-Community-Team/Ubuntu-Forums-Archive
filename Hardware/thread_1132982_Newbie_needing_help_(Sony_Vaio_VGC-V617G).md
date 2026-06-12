---
title: "Newbie needing help (Sony Vaio VGC-V617G)"
date: 2009-04-22
forum: Hardware
---

### Post by F4rrari on 2009-04-22
Hi all,

I have a Sony Vaio VGC-V617G Desktop. Just downloaded Ubuntu 9 and everythings works except I notice that my display won't go higher than 800x600. I have a Nvidia GeForce Go5700. Please help. Thanks

---

### Post by chrisinspace on 2009-04-22
Have you installed the proprietary Nvidia driver?  Ubuntu has a utility that can automate the process for you.  It's under the 'Administration' menu.

---

### Post by F4rrari on 2009-04-22
Nvidia X-Server setting says my driver version is 173.14.16.

---

### Post by chrisinspace on 2009-04-22
Have you installed all available updates?  If not, I would try that first.

Where are you trying to change the resolution?  There are a couple of alternatives you can try.  Either in the 'Nvidia X Server Setting' utility or in the 'Monitor Resolution Settings' utility.  If you can't change it in either, you maybe have to edit your xorg config file.

---

### Post by F4rrari on 2009-04-22
Yes, All the update are installed. Anything else I should check? Thanks.

---

### Post by F4rrari on 2009-04-22
Never mind. Did a recovery mode and reinstall Nvidia driver, it works now. Thank you.

---

