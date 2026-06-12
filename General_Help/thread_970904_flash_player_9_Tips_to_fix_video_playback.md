---
title: "flash player 9 Tips to fix video playback"
date: 2008-11-04
forum: General Help
---

### Post by I'm a bus driver really on 2008-11-04
I don't know weather anyone cares about this but:

If you have bad video playback, do this:

I fixed my problem by installing non-free version of flash player 9. This is how you do it. Ahh.. few tips before you proceed.To install/uninstall packages (programs). You go System/Administration/Synaptics Package Manager. You can go under installed and look for flash or something like mozilla-flash etc. Uninstall it. Then go to not installed and look for flashplugin-nonfree click it for installation and press apply. (I would make sure u have mozilla closed when u do those steps).If you can't find flashplugin-nonfree on the list. It is possible that multiverse is not enabled in your apt.source. Note: Make sure you make copy of source.list in case you make mistake. <code>sudo cp /etc/apt/source.list /etc/apt/source.list.bak</code>If so then start Terminal and type in <code>sudo pico /etc/apt/source.list</code> You will be asked for your password, type it in, and it will start text editor. Look for lines which finish with multiverse and make sure they are not commented. Note: Commented means that it has # (hash) on front of it. When u done. Click CTRL + X and the text editor will ask you if you are willing to leave, click yes and then save it. Then you have to update your list. So you have to type in <code>sudo apt-get update</code>. If you have any errors then you have obviously done something wrong with source.list. I hope it helps, what happend in my case is that i had some old mozilla-flashplugin installed and it was playing up with my non-free one.

---

### Post by scouser73 on 2008-11-04
Wouldn't it be a lot easier to save yourself all the hassle and get flashplayer v.10; [http://get.adobe.com/flashplayer/?promoid=BUIGP]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

---

