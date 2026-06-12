---
title: "Conflicting grubs"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by bullet15963 on 2009-10-08
ok so i have 2 HDDs in my laptop and i had Vista on the 320GB and my music on my 160 with a 10GB partition for linux.  Now i have removed windows completely, yay! lol I installed Ubuntu onto the entire 320GB drive, the installation completed fine, but when i restart, i get the GRUB menu from my other linux install. that has on it the old linux and vista to choose from, of course the vista one doesnt do anything, as expected. so my problem is that i have installed Ubuntu just fine i just cant boot into it. Thanks in advance for any ideas

---

### Post by louieb on 2009-10-08
Thats weird - last OS installed usually takes over the MBR of the boot drive. 

1st thing I'd try is switching the boot order so the other drive boots 1st. 

2nd thing I'd try is the   [Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html") - 

If that doesn't work then I'd need to see the output from the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by bullet15963 on 2009-10-08
ok fist thank you for your very fast response. Second i feel embarrassed now because i forgot to check the boot order of the physical HDDs, and that did solve the solution. Now its back to installing drivers and changing config files lol

---

