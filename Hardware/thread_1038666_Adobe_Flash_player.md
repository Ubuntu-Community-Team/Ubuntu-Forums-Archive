---
title: "Adobe Flash player"
date: 2009-01-13
forum: Hardware
---

### Post by angelsniper45 on 2009-01-13
Ive been looking around the net, and ive tried a few methods of installation, all of coming out as a failure, so ive had to unistall and install numerous times. youtube never works, neither does hulu, dailymotion, or thatvideosite. 

Ive used gnash, sun java runtime, and adobe. Does anybody know a remedy for this problem? It will be greatly appreciated.

---

### Post by cmay on 2009-01-13
i cant say i am sure i completly understand the problem but as i see it there is only a debian package for ubuntu hardy on adobe flash homepage and it should work. i just installed flash for the first time on debian etch using the .tar archive they offer. i can see you tube just fine.  what browser do you use. maybe it has something to do with that.

---

### Post by angelsniper45 on 2009-01-13
im using firefox 3 beta 5. it didnt work in firefox 2 either.

---

### Post by Seth Kriticos on 2009-01-13
Do you use the ubuntu flash package? Did you enable the non-free packages in the package manager? (System->Administration->Software Sources)

Have this installed?:

% sudo apt-get install flashplugin-nonfree

I would also try to remove the other plug-ins, maybe there is a conflict.

If you want more concrete information you should specify what kind of hardware you are on, what browser you use and what packages are on your system.

---

### Post by cb34 on 2009-01-13
kill firefox: (hitting the X, or file/Quit is not enough.
```

killall -9 -r firefox

```
locate any and all adobe flash player files:
```

locate -e libflashplayer.so

```

delete all of them. there could be a bunch of them all over the system.. make sure you have no flash on your system anywhere.

in synaptic.. purge all other flash things you tried, everything flash.. remove.. like gnash, swfdec, non-free-plugin stuff.. everything flash..

download not the .deb, but the .tar.gz flash 10.. 15.3 off adobe's site..
the one at the top of the drop down list
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

extract the tar.gz file and do not run the script inside, there are 2 files, a .so file(flashplayer) and the script they want you to use to install it.

you just have to copy the libflashplayer.so file into the home mozilla plugins dir:
/home/yourusername/.mozilla/plugins

and if plugins directory doesn't exist, create it.

then go into:
/home/yourusername/.mozilla/firefox/yourprofile.default
and delete xpti.dat and pluginreg.dat
(these files will be recreated when you start up firefox as they should be)

now you can start firefox and type in the address bar:
[noparse]about:plugins[/noparse]

and you should see flash is installed, have fun.

all flash is, is 1 file.
libflashplayer.so

and if you have multiples all over, could cause problems, and if you have multiple other flash plugins installed, it could cause problems, that's why make sure, you find and remove all old flash stuff you may have because of all the trying you were doing.

---

### Post by angelsniper45 on 2009-01-13
hmmm. i cant get root permissions and show the hidden .mozilla folder. how can i get root privileges?

---

### Post by cb34 on 2009-01-13
you dont need root permissions to see the hidden files.. in the graphic file browser(nautilus) hit CTRL H or at the top, VIEW, show hidden files.

or in the terminal
ls -al

the -a flag with show all files, including hidden files.

---

### Post by angelsniper45 on 2009-01-13
thanks, but it still says the folders are owned by root, and that wont allow installation.


nvm i got it, and btw the .deb installer does work if you have everything else completely removed. +rep.

---

### Post by cb34 on 2009-01-14
the only reason i alwayz advise to use the tar file and not the deb, is because i've had situations where i ran the deb, and i got an error message and nothing installed, but i never knew i got an error message. because usually people dont run dpkg -i package.deb.. they just click on it in the gui. doing it from the terminal you see everything that's goin on.. the tar install is more reliable in my experience. same stuff though.

glad you got it going angelsniper45. :)

---

### Post by hotweiss on 2009-01-14
Try this:

> sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

---

