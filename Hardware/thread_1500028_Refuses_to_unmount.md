---
title: "Refuses to unmount"
date: 2010-06-02
forum: Hardware
---

### Post by duke.tim on 2010-06-02
I have an external usb hardisk that refuses to unmount. Power went out (to the USB drive) and I get the following message after trying to unmount it [http://img694.imageshack.us/img694/4495/blahbb.png](http://img694.imageshack.us/img694/4495/blahbb.png)
when I use ```
umount /disk/location
``` 
it gives me the same error message, just in text :p . so I try
```
sudo umount /disk/location
``` and get a terminal freeze, e.g. ctrl+c won't send a kill signal. so How Do I Unmount it? 
(I haven't tried a reboot but can't currently)

---

### Post by Isaacgallegos on 2010-06-02
killall5 might do it... It's like a killall all command that kills everything. Err... sorry that's my best... :(

---

### Post by duke.tim on 2010-06-06
bump

---

### Post by duke.tim on 2010-06-07
bump

---

### Post by duke.tim on 2010-06-08
So anyone? any Ideas? ...bueller....bueller...bueller....bueller

---

### Post by luigi_mb on 2010-06-08
Make sure it is not locked by any program such as bash, nautilus, etc. 
For example, if in a terminal you have something like

[your user name]@[your machine name]:/media/[name of USB drive]$

return home

```
$ cd ~
```

etc...

/luigi

---

