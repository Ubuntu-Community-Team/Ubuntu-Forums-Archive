---
title: "Need Drivers Not on Laptop Provider's Website"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by Matand009 on 2007-01-28
Can someone help me find the drivers for a Toshiba Satellite 4060CDT....

also i remember reading somewhere that you can use some windows drivers?

can someone point out to me how...

thx...

---

### Post by xmastree on 2007-01-28
Drivers for what?
My Toshiba 4300 works right out of the box, as it were. What are you having trouble with? Sound? Video? USB?

---

### Post by Matand009 on 2007-01-28
video and sound...

my internet driver works fine tho...

---

### Post by xmastree on 2007-01-28
According to [this page,]("http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAS406U") your sound is ESS ES1978. Searching the forums for ES1978 doesn't help much :( 

For the video, it's a Trident 9525, and according to [this thread]("http://ubuntuforums.org/showthread.php?t=167355"), setting vesa as the driver does the trick.

---

### Post by Matand009 on 2007-01-29
sorry but i dont have the permissions to change the xorg.conf file....

how do i change them if i cant use the login screen to login as root:confused:

---

### Post by finer recliner on 2007-01-29
enter this in a terminal:
```
sudo gedit /etc/X11/xorg.conf
```


for more information about 'sudo' i strongly recommend reading this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Matand009 on 2007-01-29
thx...

I'll have to write that down....

---

