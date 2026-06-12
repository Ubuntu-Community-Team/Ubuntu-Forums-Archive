---
title: "Install two Server editions"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by piccoloprincipe on 2009-06-17
Hello, I have a laptop without cd and monitor, that runs a Ubuntu Server 9.04. I'd like to install another copy of Ubuntu along to it; I can resize the current partition to provide the needed disk space, with parted. The plan is to run apache with php 5.3 in the second distribution, while keeping stable php 5.2 on the first.
The current distro was installed via netboot; what is the fastest way to having another copy up and running? I have only ssh access on this machine. Is there some .tar that can be decompressed on the new partition? Or something that installs on it by chrooting? I can download iso on the server via wget.

---

### Post by Mighty_Joe on 2009-06-17
How about using [virtualbox]("http://www.virtualbox.org/") or [vmware]("http://www.vmware.com/") to run another instance of Server in a virtual machine?  That would be easier than dual booting and give you a lot more flexibility.

---

### Post by dstew on 2009-06-17
Since you installed your first system using netboot, you probably do not have an install .iso on your disk. But, it doesn't take long to get another server install over the internet, so why not do netboot again?

Another way is to use debootstrap. It creates a skeleton system that is a clone of the one you already have, and then you then fill it in with the software using apt-get update. See [this document]("https://help.ubuntu.com/community/Installation/FromLinux"), the "Without CD" section.

If you have an installer .iso on your hard disk, the document also shows how to install from that. Basically, you create a small partition to hold the .iso, a larger partition that will be the install target, then boot the .iso partititon, and it will install as if you had a CD, only faster.

You could also try duplicating your root partition. [Here]("http://ubuntuforums.org/showthread.php?t=316237") is one way to do it, but I don't see the command to copy the partition. He just says "copy the partition". Two methods I have seen are using the cp (copy) command, or using the dd ("data dump") command. See [this thread]("http://www.linuxquestions.org/questions/linux-hardware-18/how-to-duplicate-a-partition-using-dd-636291/").

There is also a program called [partimage]("http://www.psychocats.net/ubuntu/partimage") that is for making an image file of a parition. You would make an image file of your root partition, then "restore" it to your new empty partition to duplicate your system.

---

### Post by piccoloprincipe on 2009-06-17
Thanks for the replies, I will check out these methods :) I can't use netboot again because I have no longer a tftp server set up on a machine, it's an overkill to reinstall it.

---

