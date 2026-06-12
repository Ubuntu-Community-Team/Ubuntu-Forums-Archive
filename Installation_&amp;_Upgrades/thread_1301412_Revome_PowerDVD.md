---
title: "Revome PowerDVD"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by zach4618 on 2009-10-26
So I bought my aunt one of those Dell Inspiron 15n laptops... it came with Ubuntu 9.04 as well Dell Power DVD. I wanted to try the DVD software out on my Ubuntu 9.10 beta machine, so I inserted the disk, installed the dependencies, etc. To make a long story short, it didnt work. The DVD playback was choppy (I tried a couple different movies) and the audio was off by half second or so. So I went to uninstall using computer janitor, but it ended up just breaking the software and not removing the package. By itself this wouldnt be a problem, but now if I try to do any updates, I get the following message:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

So I opened up terminal and ran the command:

```
zach@zach:~$ sudo apt-get install -f
[sudo] password for zach: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pdvdlinux
0 upgraded, 0 newly installed, 1 to remove and 71 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115156 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
/var/lib/dpkg/info/pdvdlinux.postrm: 41: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Ive tried using synaptic as well, but I get another error. Short of doing a clean install, does anyone have an idea for how to fix this?

---

### Post by hvackevin on 2009-11-21
Same problem. Solutions?  Anybody?

---

### Post by hvackevin on 2009-11-22
Solved!

sudo gedit /var/lib/dpkg/info/pdvdlinux.postrm

# Comment out the last three lines & save

sudo gedit /var/lib/dpkg/info/pdvdlinux.postinst

# Comment out the last three lines of this also & save

sudo dpkg -P --force-all pdvdlinux

sudo apt-get update

sudo apt-get upgrade

Now, all errors will be resolved.  You can add and remove packages again through apt and synaptic and update-manager.

---

### Post by epicoder on 2009-11-23
Works perfectly! Thank you so much.

---

### Post by GregFuess on 2009-12-05
Not sure what comment out means, but I am experiencing the same problem, and would appreciate any help.  I ran the commands recommended, but get 
dpkg: error processing pdvdlinux (--purge):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux

Recommendations and advise appreciated.

Regards

Greg

---

### Post by caro on 2009-12-13
> **GregFuess said:**
> Not sure what comment out means, but I am experiencing the same problem, and would appreciate any help.  I ran the commands recommended, but get 
dpkg: error processing pdvdlinux (--purge):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux

Recommendations and advise appreciated.

Regards

Greg

Greg, I had the same problem and the solution above solved it.  

To comment out means to insert the pound sign or hash mark "#" (without the quotes) at the beginning of the line.  Then save the file and follow the directions given above.

---

### Post by boygenuis on 2011-01-12
Excellent post.  This worked for me as well.

---

### Post by PerplexedPangolin on 2012-09-07
This solved my issues with my Dell Inspiron when I upgraded to Ubuntu 12.04, thank you!!!

---

