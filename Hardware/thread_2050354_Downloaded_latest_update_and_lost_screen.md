---
title: "Downloaded latest update and lost screen"
date: 2012-08-30
forum: Hardware
---

### Post by Lemuel111 on 2012-08-30
Hi folks, 
Using 12.04 and updated/installed latest updates. However on reboot I've lost my desktop screen. I can get into to full screen terminal but when trying sudo apt-get ubuntu desktop I just get the error message 'monitor not found' even though the monitor is displaying terminal. Any help appreciated.

---

### Post by BrianBlaze on 2012-08-30
For me this happens once and a while after updating, from the terminal I go to /etc/X11/xorg.conf.d/00-vboxvideo.conf in it is:

```

#Section "Device"
#	Identifier "Videocard666"
#	Driver "vboxvideo"
#EndSection

```

I have to hash (comment) out each line and then reboot and I am back to a graphical environment... I am not sure what updates I do to cause this but it happens sometimes and is an easy fix for me :)

---

### Post by Lemuel111 on 2012-08-30
> **BrianBlaze said:**
> For me this happens once and a while after updating, from the terminal I go to /etc/X11/xorg.conf.d/00-vboxvideo.conf in it is:

```

#Section "Device"
#    Identifier "Videocard666"
#    Driver "vboxvideo"
#EndSection

```I have to hash (comment) out each line and then reboot and I am back to a graphical environment... I am not sure what updates I do to cause this but it happens sometimes and is an easy fix for me :)

Can you explain how to do that in more detail please as I struggle with terminal?
Thanks.

---

### Post by BrianBlaze on 2012-08-30
type this: (notice the sudo so if you log in as root you do not need to sudo and also I am assuming you have VIM installed you can also use vi or emac or whatever CLI text editor you want I can't teach you how to use it but VIM is my favorite!)

```

sudo vim /etc/X11/xorg.conf.d/00-vboxvideo.conf

```

then you can edit the file... maybe it would be easier if you could tell me what is the output in your /etc/X11/xorg.conf.d/ folder like this:

```

ls -al /etc/X11/xorg.conf.d/

```

Basically what happens for me anyways is when it updates X11 it chooses my vm display driver instead of my actual one so I need to make it unable to see the vm one by hashing it out. Let me know whats up!

I just realised I am stupid and it happens on my fedora box... So for you to check it on ubuntu you go:

```

cat /etc/X11/xorg.conf

```
and please let me know what the output is :)

---

### Post by Lemuel111 on 2012-08-31
> **BrianBlaze said:**
> type this: (notice the sudo so if you log in as root you do not need to sudo and also I am assuming you have VIM installed you can also use vi or emac or whatever CLI text editor you want I can't teach you how to use it but VIM is my favorite!)

```

sudo vim /etc/X11/xorg.conf.d/00-vboxvideo.conf

```

then you can edit the file... maybe it would be easier if you could tell me what is the output in your /etc/X11/xorg.conf.d/ folder like this:

```

ls -al /etc/X11/xorg.conf.d/

```

Basically what happens for me anyways is when it updates X11 it chooses my vm display driver instead of my actual one so I need to make it unable to see the vm one by hashing it out. Let me know whats up!

I just realised I am stupid and it happens on my fedora box... So for you to check it on ubuntu you go:

```

cat /etc/X11/xorg.conf

```
and please let me know what the output is :)


I typed the first command & all I have is a flashing cursor at the top of the screen, single line ~ in blue down the rest of the screen and "/etc/X11/xorg.conf.d/00-vboxvideo.conf" [New directory]        0,01 All

at the bottom of the screen.

---

