---
title: "aptitude not installing packages help"
date: 2008-09-29
forum: General Help
---

### Post by madtyper on 2008-09-29
Hi. I'm trying to install the adobe flash alternative gansh, but can't seem to get aptitude or apt-get to install it. I am entering

```
aptitude install gnash-0.8.3.tar.gz
```

but am getting the output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "gnash-0.8.3.tar.gz"
Couldn't find any package whose name or description matched "gnash-0.8.3.tar.gz"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

If it helps, I am on a 64-bit install on an AMD machine, the ubuntu install is fresh, and everything was updated via the Update Manager. Here is the output of *'ls -l'* (sorry, it's just so fun & convenient to hit the 'code' button):

```

drwxr-xr-x 2 user grp    4096 2008-09-29 21:17 Documents
-rw-r--r-- 1 user grp 4002062 2008-09-29 20:48 gnash-0.8.3.tar.gz

```

---

### Post by ju2wheels on 2008-09-29
You downloaded the gnash source, that needs to be unzipped and compiled. It cant be installed using apt.

Download the following packages and install them in this order instead:
[http://http.us.debian.org/debian/pool/main/g/gnash/gnash-common_0.8.3-6_amd64.deb](http://http.us.debian.org/debian/pool/main/g/gnash/gnash-common_0.8.3-6_amd64.deb)
[http://http.us.debian.org/debian/pool/main/g/gnash/gnash_0.8.3-6_amd64.deb](http://http.us.debian.org/debian/pool/main/g/gnash/gnash_0.8.3-6_amd64.deb)
[http://http.us.debian.org/debian/pool/main/g/gnash/mozilla-plugin-gnash_0.8.3-6_amd64.deb](http://http.us.debian.org/debian/pool/main/g/gnash/mozilla-plugin-gnash_0.8.3-6_amd64.deb)

Just so you know ahead of time, this will not fix all your problems with flash on a 64bit version of Ubuntu. Flash is currently highly unstable especially if you are running Intrepid, and from the looks of things this wont be fixed for a while.

---

### Post by jerome1232 on 2008-09-29
Also if you want an easy way to install gnash it is in the repos
```
apt-cache search gnash
gnash - free SWF movie player
gnash-common - free SWF movie player - common files/libraries
gnash-cygnal - free SWF movie player - Media server
gnash-tools - free SWF movie player - Command-line Tools
klash - free SWF movie player - standalone player for KDE
konqueror-plugin-gnash - free SWF movie player - Plugin for Konqueror
mozilla-plugin-gnash - free SWF movie player - Plugin for Mozilla and derivatives
```

the mozilla-plugin-gnash is probably the one you want

edit: By the way I run a 64bit system, I use adobe's flash (flashplugin-nonfree) and haven't had any problems what-so-ever.

---

### Post by madtyper on 2008-09-29
Thanks Jerome, what's up ju2wheels?

Could you tell me, what is intrepid?

---

### Post by ju2wheels on 2008-09-29
Intrepid is the next version of Ubuntu (8.10) which is currently in Alpha and will be released at the end of October. You are probably running Hardy Heron though (8.04.1).

---

### Post by ju2wheels on 2008-09-29
0.8.3 is not in the repos, at least not for Intrepid. Only 0.8.2, however 0.8.3 was updated to support a higher version of Flash than 0.8.2 but still doesnt have as much compatibility as the non free flash (which on Intrepid 64bit crashes very often, I dont know about Hardy though I never installed it on this machine).

---

### Post by jerome1232 on 2008-09-29
hardy uses 0.8.2, 0.8.3 isn't in backports either, so if you want that newest version you will have to compile or install those packages from the debian repositories that ju2wheels linked for you.

---

### Post by madtyper on 2008-09-29
Ok ... arg. Can someone tell me what am I doing wrong? This time I downloaded the ".deb" file, but without any improved results... Here is my screen:

```

usr@grp:~/Desktop$ sudo apt-get install gnash-common_0.8.3-6_amd64.deb 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnash-common_0.8.3-6_amd64.deb

```

I hope I'm not missing some silly detail, but it's a crazy learning process. 

Thanks for your help!

---

### Post by madtyper on 2008-09-29
> **jerome1232 said:**
> hardy uses 0.8.2, 0.8.3 isn't in backports either, so if you want that newest version you will have to compile or install those packages from the debian repositories that ju2wheels linked for you.

Ok. I guess I'll cross that bridge when I get there. For now if I can get anything working, I'll do it, then see what should do once it works, or works not so good.

I am glad my Windows crashed and I decided to give linux another try. It pushes you to learn a little more, makes you ask questions. Windows is too limitless, if one thing doesn't work, there are a thousand other 1-click fixes (maybe that's the case here too, but you'd have to know what you were doing slightly to know that too!).

---

### Post by jerome1232 on 2008-09-29
since you downloaded those packages the method to install differs a bit.
let's say you downloaded them to your desktop you would do this
```
cd Desktop
sudo dpkg -i nameofdebfilehere
```

edit: And btw you can actually just double click the files too :)

---

