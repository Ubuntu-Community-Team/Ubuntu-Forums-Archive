---
title: "problem detecting hard drive on boot"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by axlan on 2008-12-20
I've had ubuntu 7.04 server edition running for about a year. Worked fine with no issues. Recently Grub stopped detecting the drive. Repartitioning would fail, so I figured the drive was dead. 

I decided to install 8.10 server edition on a WD400 drive. There were some odd problems. For a while the drive wasn't detected at all by the installer. Messing around with the bio's and disabling the master IDE bus inexplicably led to it installing without further incident.

One problem that hasn't gone away was the message "ata1: LSRST failed (errno=-16)"

Now after grub selects Ubuntu these messages pop up and then I get "Gave up waiting for root device" and it starts BusyBox

If I just type exit it finishes the boot correctly, but since this is a server and I won't be there most of the time this is a significant nuisance. Any idea of how to fix the problem or at least ignore the error.

I apologize if this is the wrong subforum... I started writing it when the install wouldn't work and added as I figured work around.

---

