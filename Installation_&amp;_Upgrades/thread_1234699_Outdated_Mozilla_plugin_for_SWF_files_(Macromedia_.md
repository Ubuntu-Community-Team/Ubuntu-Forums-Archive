---
title: "Outdated Mozilla plugin for SWF files (Macromedia Flash)"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by mRuNB on 2009-08-08
Dear community,

i am a new ubuntu user and i use in my HP mini 2140 the netbook remix of the lastest version of ubuntu. I have done all updates from the update manager and also i have installed the latest version of swf plugin,using the Synaptic Package manager, 0.8.2. But, once i visited pages like Myspace.com and youtube.com the Flash player was unable to play the files. Later i visited the plugin's page and discovered that there are 2 later versions(0.8.4) of the one i have installed. I'm talking about swfdec plugin and it's website is [http://swfdec.freedesktop.org/](http://swfdec.freedesktop.org/) .

Then, i downloaded the latest version of the plugin but i wasn't able to install it. I decompressed the .tar.gz in which the new version was and 'oups'!! How to install it?

So, my problem has 2 sides.

1. Is there any way to get and install the newer version of swfdec-mozilla plugin from the Synaptic Package Manager directly?

2. Anyone can help me install the new version manually. Here is a picture of the files i downloaded:

[IMG]http://img151.imageshack.us/img151/2852/swfdec084.png[/IMG]

Hope someone can help a noobie!

Thanks :)

---

### Post by Partyboi2 on 2009-08-08
If you don't mind using the unstable version (0.9.2) you could add [[COLOR=Blue]this[/COLOR]]("https://launchpad.net/%7Eswfdec-team/+archive/ppa") 3rd party repo.

---

### Post by mRuNB on 2009-08-08
I installed what you've told me! Youtube is improved but still sucks. Myspace.com still as it was. 

Anyone can tell me how to install the new version of swf plugin for firefox? The one in the screenshot!

Thanks:)

---

### Post by presence1960 on 2009-08-08
actually you don't need swfdec. basically it is terrible anyway. remove it and then install flash like this: open a terminal and run this command ```
sudo apt-get install flashplugin-nonfree
``` or go to  [adobe]("http://get.adobe.com/flashplayer/?promoid=BUIGP") and download the deb file if you are running 32 bit Ubuntu.

or if you are running 64 bit Ubuntu see [here]("http://ubuntuforums.org/showthread.php?t=772490")

First be sure to remove all instances of flash you currently have installed such as swfdec, gnash, etc.

---

