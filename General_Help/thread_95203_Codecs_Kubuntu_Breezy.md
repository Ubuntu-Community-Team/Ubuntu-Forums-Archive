---
title: "Codecs Kubuntu Breezy"
date: 2005-11-26
forum: General Help
---

### Post by cajunboy2k on 2005-11-26
OK, I've got the w32codecs tar file. Now, how do I install it? 
:confused:

---

### Post by aysiu on 2005-11-26
Throw the .tar.gz in the trash.
Download to your desktop the [w32codecs .deb file instead](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb). Then pop open a Konsole and type in ```
cd Desktop
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
``` If you don't know how to get to the Konsole, click on the KMenu and then click on Run and type the word *konsole* in there.

---

### Post by goldenboy on 2005-11-26
[QUOTE=aysiu]Download to your desktop the [w32codecs .deb file instead](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb).[/QUOTE]

Or for a more convienent way with respect to updates and other usefull stuff like lame, etc.

Add

```
deb ftp://ftp.nerim.net/debian-marillat/ sid main
```

To your /etc/apt/sources.list file (you have to be root to do so, or at least have root rights).
Then either run your favourized grahical package manager to install the w32codecs package, or open a shell and run

```
sudo apt-get update
```

followed by 

```
sudo apt-get install w32codecs
```

You will likely receive an error message after the apt-get update, which you can either ignore - it get somewhat annoying with time, or follow the instructions provided here: [https://wiki.ubuntu.com//AptAuthenticationInstructionsForHoary](https://wiki.ubuntu.com//AptAuthenticationInstructionsForHoary)

Otherwise if you want to stay with the sources, which I would not recommend follow this HOWTO:

[http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278)

enjoy

---

### Post by cajunboy2k on 2005-11-26
WOO HOO!!! Thanks guys. I just switched from Mepis to Kubuntu, I think I like it better.

---

### Post by Firetech on 2005-11-26
For w32codecs, I think the Ubuntu PLF repo is a better alternative, as marillat is made for debian and might break stuff.
Instructions on how to use Ubuntu PLF is available at [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by André on 2005-11-26
Hi, if you want to make your Kubuntu have all the nice extra stuff like codecs, proprietary drivers... you might like easy-kubuntu. You can find it here: [http://olwin.free.fr/](http://olwin.free.fr/) It worked pretty well for me and for the first time i have no problems with videos on websites :-)

Greetings Andr&#233;

P.S.: Easy Kubuntu uses the mentioned PLF mirrors but configures your sources.list automatically.

---

### Post by carlos1 on 2005-11-27
Try this: 
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)

---

### Post by André on 2005-11-27
Hi Carlos1,

just wanted to know: Does Automatix work well for Kubuntu? The author says it brings up some problems (whatever that may be).

Did you try it and experience problems??

Greetings
André

---

### Post by carlos1 on 2005-11-27
The only problem I had was it wouldn't install MPlayer properly. However, I tried compiling that from source and still no go, so I think it's a local problem, not something with Automatix.
Also, for some reason my Azureus install isn't right - ie. it won't download. Again, I tried to install it separately and had the same problem so I don't think it's Automatix.
Otherwise, the codecs, etc. work great - it's much more convenient that rooting around for the different apt sources, etc. 
I didn't experience any other problems than those.

---

### Post by Brando569 on 2005-11-29
it depends on how you have kubuntu working. if you installed the kubuntu-desktop onto ubuntu then it will work, but if you have just plain kubuntu it wont work cuz it doesnt have the needed files for the Gnome GUI, i think the author said it would take somewhere around 100+ packages that would need to be installed for it to work. easy-ubuntu works just as good as automatix would in a KDE environment

---

### Post by carlos1 on 2005-11-29
Not true, it works with Kubuntu just fine. I never had a Gnome GUI either, I installed Kubuntu straight from disc without going through the Gnome thing. 
There are 2 or 3 Gnome libraries you have to install to get  Automatix to work, which is easily done through Apt or Synaptic. After that it was no problem. 
The exact libraries are, I believe, in the Automatix how-to or on the site itself. It's easy to find - I certainly didn't figure it out for myself!

---

