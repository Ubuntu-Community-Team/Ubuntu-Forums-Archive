---
title: "ATI Catalyst 11.7"
date: 2011-07-30
forum: Hardware
---

### Post by kiddykoff on 2011-07-30
Hello forum,

I had been using the opensource drivers for my ATI Mobility Radeon HD 4250. Since the recent Indie Humble Bundle I tried running Cogs. It said that a feature was not available with my hardware. I can't remember the error now.

So i've installed the drivers as well as i could figure. After uninstalling gnome-shell. Now when i run flrxinfo i get.

```
$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  140 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
```
instead of 
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4600 Series
OpenGL version string: 3.3.10524 Compatibility Profile Context
```
I've used this website [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick")

Now the desktop is working just fine, but some of my games are not running. They come up with errors similar to the one above.

---

### Post by kiddykoff on 2011-08-03
I've uninstalled using these [instructions]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch"). I purged fglrx and rebooted into my failsafe graphics mode. Then i followed these [instructions]("http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html") Essentially it just told me to run the command without making extraneous .deb files.

However i'm getting the same results when i run fglrxinfo. and when i open my games. Do i have to reinstall the games? Ubuntu?

---

### Post by Claus7 on 2011-08-07
Hello,

a quick one: I guess that you should not tamper with the installation of games. Just purge 11.7 and install the one that was working for you (e.g. 11.6). If you get the same results, then something different is fishy.

Regards!

---

### Post by kiddykoff on 2011-08-07
I've actually had trouble with installing those drivers. (I attached /var/log/jockey.log for reference)

I had been trying to use these instructions, [http://ubuntuforums.org/showthread.php?t=1773851]("http://ubuntuforums.org/showthread.php?t=1773851") I was told in that thread that the way natty handles update-alternatives might be different though.

---

### Post by Claus7 on 2011-08-17
Hello,

since it is the latest release it might break your system and if you are trying this on maverick this might cause more trouble, as I guess that the latest driver if focused on the latest ubuntu releases.

If I were in your shoes I would stick with 11.6. I do use this driver and is working as it should. 

Have you reinstalled 11.6 and see if is working as before? 

Just to mention that I do not use a patch for 11.6 to work in my system, and I guess that the best link (guide) you should follow is this:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide) 

as is maverick based.

Regards!

---

### Post by kiddykoff on 2011-08-19
I was having a problem installing the default propietary drivers from jockey.

at this point, i'm going to do a fresh install when oneric comes out. Then i'll be able to run gnome shell with proprietary drivers (assumingly). Before Gnome3 would distort windows with proprietary drivers, but now that i'm using the regular drivers. I'll just stick it out for a couple months.

School is starting for me soon, so I'll be busy anyways.

---

