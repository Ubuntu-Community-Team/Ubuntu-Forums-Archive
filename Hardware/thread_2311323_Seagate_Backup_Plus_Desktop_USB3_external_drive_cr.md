---
title: "Seagate Backup Plus Desktop USB3 external drive crashes kernel"
date: 2016-01-26
forum: Hardware
---

### Post by jmgallag on 2016-01-26
Hi,

I have a new install of Ubuntu 14.04.3 LTS. In this PC, I have a PCIe USB3 expansion card. Plugged into the card are two external USB3 drives. One is a Seagate Backup Plus Desktop, the other is a Seagate GoFlex Desk. Both are 3TB drives. These drives hold the backups from all the computers in the house, as well as videos and music. Almost 2TB of stuff. The intention is that one of the drives is a backup of the other.

The Backup Plus was just formatted as ext4, and I am trying to copy all the stuff from the GoFlex to the Backup Plus. Writing to the Backup Plus causes a hard crash. Not immediately, but usually in less than 10 minutes. I can read the entire contents of the GoFlex without a problem. When the crash happens, the screen freezes. I have to cycle power to reboot. I do not see anything interesting in the logs after the crash. 

I found some threads reporting that the uas module sometimes causes problems, so I blacklisted it. With it blacklisted, the Backup Plus does not mount.

The HW combo works fine under Win7, which was previously loaded on this PC.

Looking for recommendations.

Thanks,
Jim


Update: After additional testing, the crash only seems to happen when I reading from the Go Flex and writing to the Backup Plus.

---

