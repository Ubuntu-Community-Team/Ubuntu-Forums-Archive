---
title: "How do we Install another Video Card?"
date: 2014-08-12
forum: Hardware
---

### Post by Rick St. George on 2014-08-12
I've seen a number of posts about installing drivers for various cards, but can not find one about How to Install another Video Card?

So I want to update a Video Card so I can update to a newer version of ubuntu. But how does one do that since the OS has already installed the driver for the existing card! 
Obviously Windows does it automatically ... but,

What is the procedure for removing and installing another Video Card in the Ubuntu OS? 

Thanks for any help for someone begging to learn this wonderful platform.

Rick

---

### Post by mastablasta on 2014-08-13
> **Rick St. George said:**
> 
So I want to update a Video Card so I can update to a newer version of ubuntu. But how does one do that since the OS has already installed the driver for the existing card! 
Obviously Windows does it automatically ... but,

That is incorrect! windows does not uninstall the drivers automatically for you to replace the card. you need to uninstall the drivers replace the card and then reboot and then very likely install drivers for your new card (otherwise you will get vesa "safe mode" only). furthermore too many replacements on certain windows versions will lock you out as the OS will think you are running it on different computer. EDIT: windows does have some drivers included these days but they are pretty bad compared to latest version from manufacturer.

back to Linux. 
opensource drivers are part of kernel. so when you boot linux checks what hardware you have and loads the drivers for it. this happens on every boot. 
proprietary drivers - user has to manually install them and manually remove them. they often (but not always) provide a better experience to the user. the graphics card drivers that are provided like that are only from NVidia and AMD. intel has opensource only.

how to solve your "issue"?
1. if you currently have opensource drivers installed then all you need to do is turn off the PC, stick in the new card and reboot. on new boot opensource drivers will be loaded. you can replace those with proprietary ones.
2. if you currently have proprietary drivers installed you need to remove them first. this could be done via additional drivers app (by reinstalling the opensource driver) or via command line.:
for AMD cards: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
for NVidia: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Rick St. George on 2014-08-13
Thanks Masta ... I'm sure this one will get a lot of reads!

Peace,
Rick

---

