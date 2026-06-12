---
title: "Ibex and Cairo Plugins"
date: 2008-11-02
forum: General Help
---

### Post by MrWES on 2008-11-02
I just installed Ibex and was configuring Cario; I was looking for the trash applet, but I don't see any applets or desklets for Cairo. Am I missing something. I am not running compiz; this is just under GNOME.

Thanks,
Bill

---

### Post by Macdelaney on 2008-11-02
I was having the same problem, the solution is to use the official repositories
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu)

---

### Post by Landara on 2008-11-02
Sorry but that is not the solution. For a few people that worked, for most of us, it did nothing. Hasn't worked for me. Please do not mark this as solved.

---

### Post by fabounet on 2008-11-03
If you're under 32 bits it should work.
If you're under 64, you're unlucky ^_^

---

### Post by ValPaliy on 2009-01-27
Here [http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.6.2.3_i686.deb]("http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.6.2.3_i686.deb") are the x64 plig-ins. Cheers!

---

### Post by VeeDubb on 2009-01-27
Also, if you poke around at the developer's site, you can actually download debs of version 2.0.0-beta1.

I've been using it for a couple days, and aside from the fact that they systray plugin still sucks, it's really a superb release.  I can't wait until 2.0 final comes out.

FYI- After installing the debs for 2.0.0-beta1, I found that the dock would not launch at all.  The simple fix was to use getlibs.  If you don't have getlibs installed, install it.  It's a god send, especially on 64 bit.

```
sudo apt-get intall getlibs
```

Then use it to make sure you have all the dependencies you need for cairo dock.

```
getlibs /usr/bin/cairo-dock
```

---

