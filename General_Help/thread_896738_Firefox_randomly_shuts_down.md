---
title: "Firefox randomly shuts down"
date: 2008-08-21
forum: General Help
---

### Post by talking Llama on 2008-08-21
Sometimes when I'm surfing Firefox not doing anything in particular it randomly shuts itself down. So for instance, I'll have a few tabs open, checking emails, Digg, etc and all of a sudden it will shut itself down without warning, Thanks to the Firefox restore session option I can get all the tabs back up again but its a bother. Anyone know why this is happening or how to fix it?
Thank you.

---

### Post by csa on 2008-09-04
Same problem here.... anyone knows how to fix this?

---

### Post by Scunge on 2008-09-04
No idea, but I remember reading somewhere else here that you can open a terminal window (**Applications > Accessories > Terminal**), and enter the command ```
nohup firefox
```

Then when Firefox crashes, copy the contents of the file *nohup.out* in your home directory and paste it all here. That at least could tell people what the error messages are which are causing the crash.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by mb_webguy on 2008-09-04
It's probably Flash.  If you don't either have the Flash 10 plugin from the backports repository or the libflashsupport package installed, Flash can cause several problems with Firefox, including preventing any other application from producing sound when Firefox is open, and causing Firefox to crash whenever there's a problem with Flash on a page.

My suggestion is to install the Flash 10 plugin from the backports repository (see the link in my signature if you don't know what I'm talking about).

---

### Post by talking Llama on 2008-09-11
I tried that method from your signature but it says there were errors in the process:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mb_webguy on 2008-09-11
> **talking Llama said:**
> I tried that method from your signature but it says there were errors in the process:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

It doesn't look to me like you added the backports repository, since it's saying that flashplugin-nonfree 9.0.124.0ubuntu2 is the newest version.

---

### Post by Crafty Kisses on 2008-09-11
While Firefox is running, run this command and post the results:
```
top
```
It could be a resource issue.

---

### Post by talking Llama on 2008-09-11
How do I add the back ports repository? Also it isn't a resource issue but thanks for the help. ^-^

---

### Post by unutbu on 2008-09-11
Edit /etc/apt/sources.list:
```

gksu gedit /etc/apt/sources.list
```

Add these lines:
```

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```
Save, exit. Then run
```

sudo apt-get update
```

See [https://help.ubuntu.com/community/UbuntuBackports#Enabling%20the%20entire%20repository](https://help.ubuntu.com/community/UbuntuBackports#Enabling%20the%20entire%20repository)

---

### Post by benjick on 2008-09-11
If it's flash, i followed this guide which helped me out.

[http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/](http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/)

Try it :)

---

### Post by mb_webguy on 2008-09-11
> **unutbu said:**
> Edit /etc/apt/sources.list:
```

gksu gedit /etc/apt/sources.list
```

Add these lines:
```

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```
Save, exit. Then run
```

sudo apt-get update
```

See [https://help.ubuntu.com/community/UbuntuBackports#Enabling%20the%20entire%20repository](https://help.ubuntu.com/community/UbuntuBackports#Enabling%20the%20entire%20repository)

Or you can just open System->Administration->Software Sources, go to the Updates tab, and check the box next to "Unsupported updates (hardy-backports)" -- which, by the way, was described in the instructions I originally suggested you try.  :wink:

---

### Post by talking Llama on 2008-09-11
Thanks guys I'm pretty sure this has worked now, hopefully won't have any random shutdowns from Firefox anymore. Thanks  ^-^

---

