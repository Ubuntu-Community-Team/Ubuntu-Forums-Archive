---
title: "Black screen after hibernate and suspend"
date: 2013-02-06
forum: Hardware
---

### Post by tigerjack89 on 2013-02-06
Hi all!!
I'm having problems with the suspension and hibernation on Ubuntu. Whenever I suspend or hibernate the laptop, I just get a completely black screen at the restore and I have to mechanically reboot.
The 2 things are different though:
1) When I suspend the pc, he gives me a black screen at the wake up. Then I reboot the pc and everything works fine.
2) When I hibernate the pc, he gives me a black screen again. However, when I reboot the pc, the first time I have this error at the start
```
error: error invalid environment block
Press any key to continue
```
and when I continue and login, I'm in a very unstable unity-2D session!!
If i reboot again, at the login everything works fine!!

I'm using Ubuntu 12.04 64bit, kernel 3.7.4 and nvidia drivers 310.32 with bumblebee.
However, I'm not sure that the problems are in the driver, because they start after I installed the latest updates.
Here is the indicted content of /var/log/apt/history.log
```
Start-Date: 2013-02-05  11:28:57
Commandline: apt-get dist-upgrade
Upgrade: lightdm:amd64 (1.2.1-0ubuntu1.1, 1.2.3-0ubuntu1), libnih-dbus1:amd64 (1.0.3-4ubuntu9, 1.0.3-4ubuntu9.1), liblightdm-gobject-1-0:amd64 (1.2.1-0ubuntu1.1, 1.2.3-0ubuntu1), libnih1:amd64 (1.0.3-4ubuntu9, 1.0.3-4ubuntu9.1)
End-Date: 2013-02-05  11:29:01

Start-Date: 2013-02-05  11:29:33
Commandline: apt-get upgrade
Upgrade: gstreamer0.10-plugins-bad:amd64 (0.10.22.3-2ubuntu2.1, 0.10.22.3-2ubuntu2.2), libgstreamer-plugins-bad0.10-0:amd64 (0.10.22.3-2ubuntu2.1, 0.10.22.3-2ubuntu2.2)
End-Date: 2013-02-05  11:29:35
```

I give you also an attachments of the /var/log/kern.log file after the hibernation

Again, sorry for my bad English and thanks a lot in advance to all those who wants to help :)

---

### Post by tigerjack89 on 2013-02-09
up. Any idea?

---

