---
title: "Latest flash-nonfree update seg faults firefox 3"
date: 2008-07-11
forum: General Help
---

### Post by freymann on 2008-07-11
We've been getting lots of updates lately, and this morning there was just one, the flashplugin-nonfree.

So I let it install.

Now firefox 3 seg faults all the time. So much so that Firefox is practically useless. I'm assuming it's due to flash enabled sites or sites with flash banners.

Anybody else see this?

In the meantime I am forced to load a different web browser as I can't go very far without Firefox crashing. Nice.

---

### Post by chemist109 on 2008-07-11
I have exactly the same problem.  You can disable flash by going to Tools->Add-ons and clicking the plugins tab then clicking "disable" on the shockwave flash item.

I'm going to re-install the old plugin and try the new one when it gets updated again.

---

### Post by chemist109 on 2008-07-11
Okay, here's how I did a temporary fix.  First, download the version 9 flash plugin:

```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Extract the archive and (using sudo)copy the libflashplayer.so file to /usr/lib/flashplugin-nonfree/

```
sudo cp libflashplayer.so /usr/lib/flashplugin-nonfree/
```

You might have to delete pluginreg.dat from ~/.mozilla/firefox/randomstring.default (your firefox settings directory).

Restart Firefox.  You will have the older version (9.0 r124) and the package manager won't bother you about having software that's not updated.  If an updated version comes through, it will overwrite your current setup.  If the newer version still causes crashes, you can reinstall the version 9 plugin with the above instructions.

To change back to version 10, just do

```
sudo apt-get install --reinstall flashplugin-nonfree
```

---

### Post by Jaymac on 2008-07-11
Yup, same problem here for me.

---

### Post by gunashekar on 2008-07-11
I have installed the same Flash update on Hardy. I don't have the problem. wonder why.

---

### Post by phoenixrising888 on 2008-07-11
having the same exact problem,firefox crashes

---

### Post by Melindrea on 2008-07-11
Interesting. I updated it aswell. Firefox 3 doesn't seg fault, however... My flash doesn't work anymore! *goes to check that guide a bit higher in the topic*

---

### Post by guildofghostwriters on 2008-07-12
I had a similar problem - applied all the automatic updates and then flash stopped working on the bbc cricket pages (it said I was using the wrong version) although it continued to work on youtube with some break up/corruption of the video. I followed the guide above, when I did the sudo cp... bit, firefox crashed (the failed bbc flash page was open so maybe that had something to do with it) and when I relaunched it, flash is working fine. Many thanks!

---

### Post by kaibob on 2008-07-12
> **freymann said:**
> We've been getting lots of updates lately, and this morning there was just one, the flashplugin-nonfree.

So I let it install.

Now firefox 3 seg faults all the time. So much so that Firefox is practically useless. I'm assuming it's due to flash enabled sites or sites with flash banners.

Anybody else see this?

In the meantime I am forced to load a different web browser as I can't go very far without Firefox crashing. Nice.

I'm having the same problem. For example, the following page, which is a CNet review of the new iPhone, causes Firefox to crash (shut down) every time:

[http://reviews.cnet.com/smartphones/apple-iphone-3g-16gb/4505-6452_7-33054209.html](http://reviews.cnet.com/smartphones/apple-iphone-3g-16gb/4505-6452_7-33054209.html)

I disabled flash and everything is OK.

---

### Post by NilsE on 2008-07-12
The flashplugin version 10 Beta 2 was being installed by Flashplugin-nonfree starting yesterday. It is now in the backports to install version 9 which will solve a number of peoples problems so just remove flashplugin-nonfree and then reinstall it.

---

### Post by kbozen on 2008-07-13
the last ubuntu update (with backports) solved the problem; it updated:

- firefox-3.0
(3.0.1+build1+nobinonly-0ubuntu0.8.04.1) hardy-proposed

- flashplugin-nonfree
(10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124 .0ubuntu2) hardy-backports

---

### Post by NilsE on 2008-07-13
Correct.  What fixes the problem is going back to version 9 of the flash plugin.  RC3 of FF3 is a bonus.

---

### Post by tghe-retford on 2008-07-13
Since the change to flashplugin-nonfree 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 today, my computer is now consistently crashing every so often when I use Flash based sites.

If I am lucky, Firefox will just crash and I can restore where I was. However, in the few hours this afternoon since this update X has restarted once and another time my computer just went blank to the point where the only way to recover was to power down the computer.

Version 10 of Flash didn't cause segmentation faults on my computer, even if the BBC doesn't support it yet.

---

### Post by fragos on 2008-07-13
> **kaibob said:**
> I'm having the same problem. For example, the following page, which is a CNet review of the new iPhone, causes Firefox to crash (shut down) every time:

[http://reviews.cnet.com/smartphones/apple-iphone-3g-16gb/4505-6452_7-33054209.html](http://reviews.cnet.com/smartphones/apple-iphone-3g-16gb/4505-6452_7-33054209.html)

I disabled flash and everything is OK.

I hadn't had problems but tried your cnet url. It crashed but when Firefox was restarted with the same tabs, flash worked.

---

### Post by arnotsmith on 2008-12-06
I have just started having the same problem with flash crashing firefox 3 - but I am still using flashplugin-nonfree 9.0.124 with Ubuntu 8.04.
I have been installing all updates, but I have never installed flash 10.

The problem appeared only last week, and it seems to affect some sites, but not all.

Has the bug been backported?

---

