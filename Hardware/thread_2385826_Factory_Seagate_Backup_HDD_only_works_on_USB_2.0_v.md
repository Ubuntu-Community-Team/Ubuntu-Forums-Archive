---
title: "Factory Seagate Backup HDD only works on USB 2.0 via VirtualBox"
date: 2018-02-25
forum: Hardware
---

### Post by mav-tek on 2018-02-25
I am running Ubuntu 16.04.4 LTS on a VM through VirtualBox 5.2.6. My goal is to transfer 3TB worth of data from an external 3TB HDD formatted in XFS to a different 6TB external HDD formatted in NTFS. When I connect a "6TB Seagate Backup Plus Drive" that has not been formatted (loaded with factory partitions), Ubuntu does not detect it on any of my 4 USB 3.0 ports, only 2.0 ports. I have confirmed that another external 2TB HDD formatted in NTFS works on the USB 3.0 ports and verified it wasn't a cabling issue (swapped cables from the 2TB that worked on 3.0 to the 6TB that did not). I also confirmed my windows 10 host PC detects the "6TB Seagate Backup Plus Drive" on the 3.0 ports.

My assumption is it has something to do with the fact that the factory loaded Seagate has a small "Partion 1" that is some kind of Microsoft Reserved partition which is causing Ubuntu or VirtualBox issues on the 3.0 port only.

Other than formatting the "6TB Seagate Backup Plus Drive", anyone have any ideas? I started trying to transfer the data over the USB 2.0 port, but data transfer slowed down from 30 mb/s to 16 mb/s.

Below you can see screenshots. On the left, 2 HDDs are connected to the 3.0 USB port. VirtualBox detects them but only one shows up on Ubuntu. On the right, I moved 1 of the HDDs (the "6TB Seagate Backup Plus Drive") to a 2.0 port and it now shows up on Ubuntu.

[ATTACH=CONFIG]278651[/ATTACH][ATTACH=CONFIG]278650[/ATTACH]

---

