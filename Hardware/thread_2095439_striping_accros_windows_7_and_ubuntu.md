---
title: "striping accros windows 7 and ubuntu"
date: 2012-12-16
forum: Hardware
---

### Post by cwrubiophysicslab on 2012-12-16
Hello! I previously had an issue with raid bios, but as that does not seem to be working I am trying to set up a raid 0 configuration that both windows and linux can use.
My setup is that I have 2 SSDs and 3 Spinning Disk Drives in my new computer. Right now, One SSD has windows, the other linux. The 3 spinning disk drives I would like to be in a raid 0 configuration, with half of each disk available to each OS.
But, if I try to set up a striped raid 0 configuration with the windows 7 software, it wants to make each disk dynamic. This means it no longer works with linux, and gparted no longer recognizes the partitions I create in the windows disk management. If I go into gparted and redo the partitions there, windows can see those partitions (and I can create simple partitions) but when I try to make a striped partition, it converts the disk to dynamic which ruins what linux did.
Does anyone know a way to create a striped partition in windows between simple volumes, or a way to get linux to work with dynamic disks? Either one would solve the issue.
Thanks!

---

