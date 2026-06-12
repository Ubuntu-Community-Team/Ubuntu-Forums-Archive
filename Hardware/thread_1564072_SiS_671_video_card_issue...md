---
title: "SiS 671 video card issue.."
date: 2010-08-30
forum: Hardware
---

### Post by Baldrick_NZ on 2010-08-30
Looking into /etc/X11, I see no xorg.conf file! I also note that even though I am logged in as admin, Ubuntu doesn't recognise me as the 'owner' so won't let me edit anything. What gives?

Can anyone please help me create an xorg.conf file so that I can do better than 800x600 res, and advise how I can get Ubuntu to recognise me, as admin, as the 'owner'??

Thanks in advance...

---

### Post by mhgsys on 2010-09-26
You want to be root 
to become root;

in a terminal or tty use 
```
sudo bash
```
and type in your password.


To generate a xorg.conf you'll have to switch to tty and stop gdm.
Here's how to do that; 

switch to tty by pressing 
```
Ctrl+Alt+f1
```

note that f2, f3 ,f4 ,f5 and f6 are also tty's and f7 would be x again.


Anyway; log in on tty with your username and password.
username ( press enter) password (press enter)

then stop gdm with 
```
sudo service gdm stop
```

and generate a xorg.conf file with 
```
sudo Xorg -configure
```

this will create a xorg.conf.new in your home directory)

move the auto-generated xorg.conf.new to /etc/X11/xorg.conf

```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

Make changes you want 

```
sudo nano /etc/X11/xorg.conf
```

and start gdm again with

```
sudo service gdm start
```

---

