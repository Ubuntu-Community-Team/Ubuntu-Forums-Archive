---
title: "Cannot start X. xorg.conf seems to be gone!?"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by MrMinit on 2005-05-14
Hi,

I *think* I got some problems here. For some weeks ago, I tried to enable full NVIdia GFX-card support on my computer - which is running Hoary (I dist-upgraded from Warty). As far as I can remember, I ran this commands;

```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
```

But, here comes the problems. After I did that (and I can't remember that I got any errors), restarted the computer (or, only GNOME/X actually) my computer won't boot. I only got errors and X would not start anymore. And when I took a closer look, to check about xorg.conf looked OK I don't find it. I think I have deleted xorg.conf - in a mysterious way. I also tried to run xorgconfig a couple of times, but it don't worked properly.

What can I do to start X again? If you need some more information about the system just answer in this topic. :)

*And at last I have to excuse my english, which actually is extremely bad.*

---

### Post by Xian on 2005-05-14
If you ran this step:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Then you can just rename that back to xorg.conf and boot with that as your configuration. It won't load your nvidia drivers but it should work since you didn't mention it was giving you any problems before making the back-up.

---

### Post by MrMinit on 2005-05-14
[QUOTE=Xian]If you ran this step:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Then you can just rename that back to xorg.conf and boot with that as your configuration. It won't load your nvidia drivers but it should work since you didn't mention it was giving you any problems before making the back-up.[/QUOTE]

I know, but I can't find this file either. :| So, the problem is in fact a little bit complicated at the moment. The file is not in /etc/X11/, so I'm out of ideas now.. is there any way I can search after a specific file (xorg.conf/xorg.conf in this case) on the system without involving X?

All answers are welcome! *And again, my english sucks.*

---

### Post by Xian on 2005-05-14
[QUOTE=MrMinit]is there any way I can search after a specific file (xorg.conf/xorg.conf in this case) on the system without involving X?[/QUOTE]
Sure, just log in and then issue these commands:

$ updatedb
$ locate xorg.conf

and then 

$ locate xorg.conf_backup

---

### Post by MrMinit on 2005-05-16
[QUOTE=Xian]Sure, just log in and then issue these commands:

$ updatedb
$ locate xorg.conf

and then 

$ locate xorg.conf_backup[/QUOTE]

Excuse me for the late answer, but I could not find any file called xorg.conf or xorg.conf_backup (the file I meant I made). So, what do I do now?

I would be glad if anyone could help me.. :grin:

---

### Post by mortensn on 2005-05-17
Generally you could search for xorg.conf (or any other file) with **find** 

[FONT=Courier New]find /usr -name xorg.conf[/FONT]

Searches for the file named xorg.conf in the folder /usr incl. subfolders.

or 

[FONT=Courier New]find /etc -name xorg.\*[/FONT]

Searches for the file named xorg.* in the folder /etc incl. subfolders.

One has to backslash the * or else the shell will replace it with filenames. Here we need to make find understand the *.

BTW rember that Linux i case sensitive. To make a case insensitive search use -iname
[FONT=Courier New]find /etc -iname xorg.\*[/FONT]


Morten

---

