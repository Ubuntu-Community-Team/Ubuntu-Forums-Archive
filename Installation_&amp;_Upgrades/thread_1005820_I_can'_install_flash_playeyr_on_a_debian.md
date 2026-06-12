---
title: "I can' install flash playeyr on a debian"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by nank on 2008-12-08
i can't install flash player on a debian  seems to have problemwith lock files.Can anybody help??/
Thank you
:confused::

---

### Post by binbash on 2008-12-08
did you try downloading the installer from adobe and installing via it ?

---

### Post by cariboo on 2008-12-08
Have you tried copying libflashplayer.so to /usr/lib/mozilla/plugins?

Jim

---

### Post by nank on 2008-12-10
It says permission denies you dont' have permission to write in this folder.
Thanks so much guys for your help.

---

### Post by oldos2er on 2008-12-10
Anytime you're working outside your home directory, you'll need to use "sudo" to give yourself temporary admin privileges.

---

### Post by nank on 2008-12-10
katrina:/home/gabriele# sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
katrina:/home/gabriele#
That's what I get tryng I've tried everithing
Thank you

---

### Post by oldos2er on 2008-12-10
In Ubuntu, Flash is in the multiverse repository. I don't know if you can mix multiverse with Debian, but I suppose you could try.

---

### Post by kerry_s on 2008-12-11
> **oldos2er said:**
> In Ubuntu, Flash is in the multiverse repository. I don't know if you can mix multiverse with Debian, but I suppose you could try.

debian uses multimedia repo:
etch:
```
deb http://www.debian-multimedia.org/ etch main  
```

lenny:
```
deb http://www.debian-multimedia.org/ lenny main  
```

**sudo apt-get install flashplayer-mozilla**

---

### Post by nank on 2008-12-11
> Reading package lists... Done
Building dependency tree... Done
Package flashplayer-mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplayer-mozilla has no installation candidate
katrina:/home/gabriele#



that's what I get tryng to instaal it now, I' really a dummies could you please be very clear and indicate commands for me if poss? thanks so much!

---

### Post by hamlet_42 on 2008-12-11
hello all of you, 
if i`m wrong please correct me. 

@nank: as this is an ubuntu forum, i thought you would be using Ubuntu.

IF:
you`re using Debian, as you write, kerry_n has told you how to do it(afaik).
I had no problem installing the plugin in Debian.
You`ve got to add the repositories into the sources.list and run
sudo apt-get update
(i always forget it).

ELSE:
binbash wrote:  	
> Re: I can' install flash playeyr on a debian
did you try downloading the installer from adobe and installing via it ? 

For _me_ that did work. I'm using 8.04 Hardy, and there seems to be problems with the flashplugin from the repository.

The following isn`t for sure, but it did work.

1)I removed completely the installed versin flashplugin-nonfree
(by adding purge, not just remove in Synaptic).

2)I downloaded the package .deb for Ubuntu_8.04 from 
[http://get.adobe.com/flashplayer/?promoid=DRHWS]("http://get.adobe.com/flashplayer/?promoid=DRHWS")

3)I created the folder:
  home/user/.mozilla/plugins
  by:
```
  mkdir /home/user/.mozilla/plugins
```
4)i installed the package by clicking on it


As that didn`t work, allthough it should: 
5) i copied libflashplayer.so from /usr/lib/adobe.../libflashplayer.so
   into the folder /home/user/.mozilla/plugins and 
   copied the plugins folder into the firefox folder:
   ```

   sudo cp /usr/lib/adobe.../libflashplayer.so /home/user/.mozilla/plugins
```
   ```
cp /home/user/.mozilla/plugins /home/user/.mozilla/firefox
```

After i restarted firefox, it still didn`t work, 
so i installed firefox-2 from synaptic.
I was told that would be wrong, but thats the way i got the flashplugin
running.

If you`re not able to do the operations in the gnome-terminal, you also might do it in the file-browser nautilus. 
If youre not able to copy the files, the permissions have to be set.

It might be that i`m wrong, but i tried for about 12 hours installing 
the flashplugin, and that was the only way it did work. 
If someone else tells you i`m wrong, he might be right.


i hope there might be just one good idea in what i said,
take it easy and have fun, you`re sure going to get rid of the problem
(it might take a while)

hamlet_42

>I' really a dummies .
Sure as hell you`re not. You`re a newbie, just as i am (1-year-old linux child),
who`s asking. A dummy wouldn`t do that.
Is there a single person on earth who doesn`t need help once in a while?

---

