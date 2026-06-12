---
title: "install programs and codecs without internet access"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Sipke on 2009-11-05
Hi 
I have an old laptop with a broken network card, which we use to show dvds and miro downloads to our children, it didn't run properly any more, so I decided to reinstall it with Xubuntu Karmic (from cd)

However I forgot that I needed an internet connection to get codecs to watch dvds and MP4 etc, how can I install them (and other programs like OO.o) to this laptop without access to the internet?
Thanks
Sipke

---

### Post by mac9416 on 2009-11-05
Hi, Sipke!

You can use [Keryx]("http://keryxproject.org") to download packages and all their dependencies from your online computer and take them to your offline computer to be installed.

You will want to read the tutorial: [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

Let me know if you have any trouble!
-mac

---

### Post by s_raiguel on 2009-11-05
Just a thought, but if it has a PCMCIA slot, maybe you could borrow (or buy, they're not that expensive) network module and plug into it to get access.

---

### Post by Sipke on 2009-11-05
> **mac9416 said:**
> Hi, Sipke!

You can use [Keryx]("http://keryxproject.org") to download packages and all their dependencies from your online computer and take them to your offline computer to be installed.

You will want to read the tutorial: [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

Let me know if you have any trouble!
-mac

Great I'll try it right away, thanks for the fast reply!

> **s_raiguel said:**
> Just a thought, but if it has a PCMCIA slot, maybe you could borrow (or buy, they're not that expensive) network module and plug into it to get access.
thanks, I'll see if I can get one!

have a nice day!
Sipke

---

### Post by Sipke on 2009-11-06
Yes it worked, I was able to install libdvdcss2 and now most dvds play again. The strange thing is that a dd that did play before, won't play now anymore....

I get this error:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc 
comes from:
#: modules/access/dvdnav.c:318
msgid ""
"VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc."
msgstr ""
"VLC kan de dvd-titel niet instellen. Het is mogelijk dat niet de hele schijf "
"ontcijferd kan worden."

---

### Post by mac9416 on 2009-11-06
Hey, Sipke,

I'm glad Keryx worked for you. In order to get everything humming along, you may want to grab a few more packages. Use Keryx to get 'ubuntu-restricted-extras', 'libdvdread4', and 'w32codecs'. That should get it.

You'll probably find these pages helpful:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Good luck!

---

### Post by Sipke on 2009-11-10
> **s_raiguel said:**
> Just a thought, but if it has a PCMCIA slot, maybe you could borrow (or buy, they're not that expensive) network module and plug into it to get access.


I found a[SIZE=2] Longshine Ethernet PCMCIA Adapter (10/100Mbps)[/SIZE] for 12 Euro, how do I know whether it is compatible with xubuntu?
thanks for all your help

---

### Post by izak on 2009-11-12
Hi,

Did this work with libdvdread4? I am having similar problems since I can connect our local mirrored repositories, but our proxy apparently blocks access to medibuntu.

*The problem (as I see it):*

According to [the official documentation]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") one must manually run 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

after installing libdvdread4 via synaptic. This install script then tries to connect [http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/) to do additional downloads. This attempt times out for me, leaving me unable to play DVDs.

Will Keryx be able to sidestep these difficulties? Or is there an easy way to download the required packages via the normal http ports (which won't be blocked by the proxy). 

@Spike: you might want to check the [hardware [in]compatibility lists]("http://ubuntuforums.org/forumdisplay.php?f=332") here.

---

### Post by izak on 2009-11-12
To answer my own question: the easiest way to solve my problem is simply to go to [http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html) and manually download the packages (libdvdccs2 and w64codecs) for later "offline" installation.

---

### Post by mac9416 on 2009-11-12
Hey, izak,

The install-css.sh script just installs libdvdcss2. In order to get all codecs working, I usually install ubuntu-restriceted-extras, libdvdread4, libdvdcss2, and w32codecs (or w64codecs) with Keryx. However, since your proxy blocks medibuntu, you do have to use packages.medibuntu.org. There may be workarounds, but I'm not sure what they are.

Good luck!

---

### Post by Sipke on 2009-11-19
It worked, I've got everything up and running and bought a PCMCIA cards in the meantime!
Thanks

---

