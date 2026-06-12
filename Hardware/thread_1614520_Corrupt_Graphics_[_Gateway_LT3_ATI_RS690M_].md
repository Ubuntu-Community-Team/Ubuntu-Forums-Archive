---
title: "Corrupt Graphics [ Gateway LT3 ATI RS690M ]"
date: 2010-11-05
forum: Hardware
---

### Post by justinebbby on 2010-11-05
Help me, Obibuntu, you're my only hope.

I just installed Lucid Lynx on my netbook (Gateway LT3(119u)), and it works ok, but I experience frequent graphics corruption. Sometimes, it manifests as a "bad font" in the browser and in the terminal, but most of the time it's fairly catastrophic mayhem of the entire display, including the mouse cursor.

Several screenshots are up on
[http://plainsalad.com/betty/]("http://plainsalad.com/betty/")

There are a few things I can do consistently to make it happen.
These include (to name a few):
* looking at images.google.com with firefox
* trying to post to ubuntuforums.org with epiphany
* scrolling quickly through `man`
* viewing any of the larger screenshots I've captured

Compiz effects work ok, but can trigger a corruption event, too. Turning off effects doesn't solve the issue, though.

I've found a bug report that looks to show a similar problem:
[https://bugs.launchpad.net/ubuntu/lucid/+source/xorg-server/+bug/565903]("https://bugs.launchpad.net/ubuntu/lucid/+source/xorg-server/+bug/565903")
At this point, I wouldn't mind trying to downgrade GLX as the ticket suggests, but I can't seem to find out how; or what version I even have.

output of  ** lspci -nn | grep VGA**
```
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
```

Any help would be appreciated!

---

### Post by justinebbby on 2010-11-07
Just an update on this - not sure if I'd call it "success". 

mkay, so I found and followed steps to install the fglrx driver as an alternate for the open ATI drivers. The good news is that the screen doesn't bug out anymore, but the down side is the loss of other function, like any 3D.

glxgears and fgl_glxgears both seg fault.
Youtube and Hulu videos play, but activating fullscreen crashes the browser. I'm not 100% certain that's related, but it's a change.

Desktop effects also refuse to turn on.

The immediate issue of corrupt graphics is resolved, I guess..  but now I think that something else is broken.

Should I try installing Maverick and hope for something different?

---

### Post by Yellow Pasque on 2010-11-07
ATI dropped fglrx support for your chip last year. You should remove fglrx: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

After that, try updated open-source drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by justinebbby on 2010-11-09
drag, ok.
I uninstalled fglrx and am now following the xorg-edgers ppa.

I'm back to having the original problem, but I might be able to work around it. I'll keep with the updates, and see if it goes away one day.

Thanks, Temüjin!

---

### Post by shomi on 2010-12-09
Any updates ?
I've got the exact symptoms.

```

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

```

Running brand new 10.10 on a Gateway LT31 netbook

---

### Post by Yellow Pasque on 2010-12-09
If you're running the r300g driver from xorg-edgers PPA, report the bug to them.

---

