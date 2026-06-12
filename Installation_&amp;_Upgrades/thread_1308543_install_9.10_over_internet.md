---
title: "install 9.10 over internet"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by cliffk on 2009-10-31
i am currently running 9.04 from a usb bootable flash. i used parted to partition the hard drive to provide me with a 32G ext4 partition. i have a functioning wired ethernet connection.

is there a way to install 9.10 directly on my system? i tried upgrade, but i assume it tries to upgrade the usb drive (it reports not enough room). i was hoping there was an option to install elsewhere (like my hd partition) but there wasn't.

next i tried to install the 9.04 from the usb flash, using administration/install. i figured to install 9.04 and then upgrade it. install brought up the partition editor as one of the install steps. i selected the partition i wanted, hit forward,  and then it froze. i couldn't even close the install window. all i could do was shutdown the entire system, and try again. it didn't work. i can  only imagine there is a bug in the install for it to freeze.

is there a direct way to install 9.10? absent that, is there another way to install a live cd that doesn't involve a buggy install application? i don't mind opening a terminal window if that's an option, but my search of forums doesn't hit on anything (or for any of the problems i listed above). nor could i find a bootable usb image for 9.10 or i would try that too as a fallback to the two attempts above.

thanks

---

### Post by zvacet on 2009-10-31
Is [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") of any help to you?

---

### Post by cliffk on 2009-11-02
thanks for your response, i don't think this helps. the only linux system i have access to is running from the usb, so i don't think i can overwrite the system on the usb.  

i am successfully running linux 9.04, i just can't get it to install to hard disk. the menu adminstration/install freezes whenever i try to use it.

i see however that [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) is available. maybe they fixed something between versions. i'll post any results.

i just thought there would be a way to install over the internet onto a functioning system. all i can find available for starting from windows on the ubuntu website is live cd installations.  my laptop does not have a functioning cd player.

---

