---
title: "Unity not lauching after login in"
date: 2014-08-22
forum: Hardware
---

### Post by egomezcana on 2014-08-22
Hi everybody.

I just installed Ubuntu 14.04 and after the login screen Unity never launches or freezes in the middle of it. The weird part is that if I go to one of the terminals and stop lightdm with
```
sudo service lightdm stop
```
and start it again with
```
sudo service lightdm start
```
Unity launches without any issue. I'm suspicious of the video card, a Radeon HD 3450, since it had some issues with linux before. I tried to glxgears to check the render but I just got a black square and block after it, so I guess that's a clue. I really have no clue on how to solve it. Any suggestions??

Thanks in advance.
Eduardo.

---

