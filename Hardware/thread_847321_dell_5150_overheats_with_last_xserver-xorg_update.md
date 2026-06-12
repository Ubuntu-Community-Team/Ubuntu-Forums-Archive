---
title: "dell 5150 overheats with last xserver-xorg update"
date: 2008-07-02
forum: Hardware
---

### Post by cfischer on 2008-07-02
Overheating has been a problem in ubuntu on since dapper. Finally, Hardy seemed to have it under control. Then after this:
> Upgraded the following packages:
xserver-xorg-core (2:1.4.1~git20080131-1ubuntu9) to 2:1.4.1~git20080131-1ubuntu9.2
the cpu temperature shot from 52 C to 70 C - and nothing was running (not even Firefox, which usually gets things heated up). I downgraded and the temp fell back into the 50s. So I've just locked the xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9 version, and my laptop is happy.

Currently running an (other than xorg) updated Hardy system with the following apt sources:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

My system: lshw listing attached.

Hope this helps someone else with an old laptop ...
Charlotte

---

