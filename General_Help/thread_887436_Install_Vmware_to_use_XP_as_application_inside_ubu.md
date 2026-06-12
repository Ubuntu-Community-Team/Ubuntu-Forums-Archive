---
title: "Install Vmware to use XP as application inside ubuntu"
date: 2008-08-12
forum: General Help
---

### Post by 2on2on on 2008-08-12
Hello Friends,
I had a problem with my laptop, i had the damned vista on it and i installed ubuntu 8. But now, Ubuntu doesn't boot, it gives me error. So I've decided to format the HD and install Ubuntu, but I heard about Vmware, from which i can open windows xp as an application, anyone knows how can i do this operation? coz i don't want to choose which OS upon reboot, I want Ubuntu to be the master OS and to be able to work on XP as an application.

Many Thanks,
Rony

---

### Post by null byte on 2008-08-12
VMWare? Why don't you want to use an open-source, free one?

Give VirtualBox a try :)

```

sudo apt-get update
sudo apt-get install virtualbox-ose virtualbox-ose-source
sudo apt-get install module-assistant
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo modprobe vboxdrv
sudo gedit /etc/modules #add boxdrv
sudo adduser `whoami` vboxusers

```

---

### Post by 2on2on on 2008-08-12
Thanks for the reply, Someone told me about vmware, but i'll try VirtualBox, once I install it, i must install windows xp? coz i donnow the procedure about how to install and use this software.

---

### Post by null byte on 2008-08-12
[http://www.youtube.com/watch?v=ch8X86R6d-g](http://www.youtube.com/watch?v=ch8X86R6d-g)

Follow this guide, skip the VirtualBox installation part, you already did it.

---

### Post by 2on2on on 2008-08-12
I visited the site [http://www.virtualbox.org/wiki/Screenshots](http://www.virtualbox.org/wiki/Screenshots)
they explain everything :D many thanks for your help!!

---

### Post by hyper_ch on 2008-08-12
vmware and vbox let you both run a virtual operating system inside another one. So you wil have to install Windows XP (or VISTA or 2000 or ...) inside a virtual machine.

---

### Post by 2on2on on 2008-08-12
Ok, I watched the video, this is what i was searching for, since 2 weeks!
Thanks for your help!

---

