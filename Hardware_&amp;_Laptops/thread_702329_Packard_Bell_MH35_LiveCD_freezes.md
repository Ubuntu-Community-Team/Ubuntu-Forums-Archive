---
title: "Packard Bell MH35 LiveCD freezes"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by cichlid on 2008-02-20
Hi All,

I received a new laptop Packard Bell Easynote MH35(-U-031) and when booting ubuntu live cd, it stops and the loading bar freezes. I am sure that the live cd is alright as i have tested him on other computers.

I have tried solutions mentioned in thread [http://ubuntuforums.org/showthread.php?p=4351066&highlight=MH35#post4351066](http://ubuntuforums.org/showthread.php?p=4351066&highlight=MH35#post4351066). 

Is it so hard to get Ubuntu running on a Packard Bell?  
It would be greatly appreciated as i am an ubuntu user for two years and now forced to use vista on this laptop. 
Thanks in advance !

---

### Post by RavanH on 2008-02-20
> **cichlid said:**
> I have tried solutions mentioned in thread [http://ubuntuforums.org/showthread.php?p=4351066&highlight=MH35#post4351066](http://ubuntuforums.org/showthread.php?p=4351066&highlight=MH35#post4351066). 


So you tried to add boot options at the end of the line after pressing F6 (remove the "quiet splash --" to see more info at boot time) ? And have you tried to preselect a screen resolution? I have found that on older systems, one or more (try all at once to begin with) of the boot options **noapic nolapic acpi=off apm=off ide=nodma** usually do the trick. See more options on [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had this problem with a Linux Mint XFCE live CD on an Asus laptop while i knew the CD was good and other live CD's also worked on that particular system. All very strange and I never fiound out why...

> Is it so hard to get Ubuntu running on a Packard Bell?  
In my case, only the screen resolution was a problem. I had to preselect one (don't remember which) to make it at least visible on the 1280x800 wide screen.

---

