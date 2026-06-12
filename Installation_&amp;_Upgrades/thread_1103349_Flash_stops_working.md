---
title: "Flash stops working"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by msp3 on 2009-03-22
I'm new to Ubuntu, but I've spent the last few days searching around and learning all I can. I managed to install Flash before but for some reason my system auto updates itself (I disabled this) and every time I get a new version of nspluginwrapper my flash starts working. I'm tried uninstalling and installing flashplugin-nonfree and nspluginwrapper before and it worked, but now it won't work anymore.

I'm using the 64 bit version if that's any help.

The strange thing is that it worked a few hours ago, but now it stopped working and I haven't messed with it. Can someone please help?

---

### Post by msp3 on 2009-03-22
Ok I managed to get it working...

Before I ran the commands:

```

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

It wouldn't work when I did this. This time I ran:

```

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Can someone please explain to me why it worked the second time? I'm trying to understand as much as I can.

---

### Post by msp3 on 2009-03-22
Now this is getting annoying...

I was on YouTube watching a video, then when I opened a new link Flash stopped working. All I see is a tan box. Any ideas why it's doing this?

---

