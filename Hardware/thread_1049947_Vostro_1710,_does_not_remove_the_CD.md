---
title: "Vostro 1710, does not remove the CD"
date: 2009-01-25
forum: Hardware
---

### Post by blaite on 2009-01-25
Hey 
I have been using xUbuntu for 1,5 year on my old laptop. Now I have new one. Everything works great beside multimedia keys and the CD.  
It is Dell Vostro 1710 and to get the CD out, you can 
press Fn+F10 or 
special button in multimedia line, 
and in ubuntu by right click on the CD/DVD which pops up on the desktop. 

The first two methods do not do anything. The last one unmounts the CD, makes some sounds, but at the end does not remove it. 
On Vista the first two ways worked perfectly. 

From the multimedia line, the sound keys works, but the play/pause and stop do not either.  
 
I have xUbuntu 8.10 here. And beside having it for some time, I never had any problems so I didn't really have to learn much. I am green. Typical Internet/Office user. 

Any suggestions?

---

### Post by teaker1s on 2009-01-25
possibly not the best way, but 

```
sudo eject
```

Works for me if I leave a cd in and it mounts as root at boot

also have you checked keyboard shortcuts to see key is mapped to eject

---

### Post by blaite on 2009-01-25
> **teaker1s said:**
> possibly not the best way, but 

... but works, great! 
Thanks

But strange thing happened. Now the eject on right-click menu works :)

---

### Post by teaker1s on 2009-01-25
welcome:popcorn::popcorn:

---

