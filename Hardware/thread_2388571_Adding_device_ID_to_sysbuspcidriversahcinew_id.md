---
title: "Adding device ID to sys/bus/pci/drivers/ahci/new_id"
date: 2018-04-04
forum: Hardware
---

### Post by vkmaxx on 2018-04-04
After almost 3 years I'm still trying to solve problem with Marvell Controller drivers:
[https://ubuntuforums.org/showthread.php?t=2275966](https://ubuntuforums.org/showthread.php?t=2275966)
> I wanted to install Ubuntu on my Marvell 9182 RAID 0 but I can't see my drive under Ubuntu. I tried to follow solution from here:
[http://ubuntuforums.org/showthread.php?t=2116826](http://ubuntuforums.org/showthread.php?t=2116826)
[http://en.wikipedia.org/wiki/List_of..._Linux_support]("http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE91xx_chipsets_Linux_support")

** But it doesn't work in newer kernels **. After entering:
     Code:

     [COLOR=#000000]sudo /bin/echo 1b4b 91a2 > /sys/bus/pci/drivers/ahci/new_id[/COLOR] 
I get "permission denied" or "bash: echo: write error: File exists" :/
All I found was that in kernel 3.16 there was a small interface change to new_id:
[URL="https://www.redhat.com/archives/libvir-list/2016-June/msg02132.html"]https://www.redhat.com/archives/libvir-list/2016-June/msg02132.html
[/URL]
Similar problem:
[https://bugzilla.redhat.com/show_bug.cgi?id=735251](https://bugzilla.redhat.com/show_bug.cgi?id=735251)

But still don't know how to access my drive under Ubuntu :( Is there any hope some of you guys know how to fix this - how to add new device ID under newer kernel?

---

