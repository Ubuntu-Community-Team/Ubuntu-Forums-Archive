---
title: "[How-To] Install Acrobat Air, then Tweet Deck"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by shaka zulu on 2009-04-29
This how to is taken from here: [http://jamsubuntu.blogspot.com/2008/12/installing-using-adobe-air.html](http://jamsubuntu.blogspot.com/2008/12/installing-using-adobe-air.html)

I did not come up with this, but I did it and it worked. I'm posting because I keep seeing people on this site attempting the same thing to no avail. Hope it goes well for you.

I'm using Intrepid Ibex.

*Adobe AIR is a cross-operating system runtime that enables web developers to use their existing web development skills, code and tools to build and deploy rich web applications and content to the desktop.***From: [http://onair.adobe.com/air](http://onair.adobe.com/air)**

To download Adobe Air, use the following command to download the .bin file from the official website:[INDENT]```
wget http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin
```[/INDENT]Before we can begin to install it, we need to apply the right permissions to it. Once that is done, we can then begin to install:[INDENT]```
chmod +x AdobeAIRInstaller.bin
./AdobeAIRInstaller.bin
```Once that is done you may go to [http://www.tweetdeck.com/beta/](http://www.tweetdeck.com/beta/) and click on the [Download now, it's free]("http://tweetdeck.com/mint/pepper/tillkruess/downloads/tracker.php?url=http://tweetdeck.com/beta/TweetDeck_0_25_manual.air") button (or you can just click my link here, then click "ok" to save, then "open" when it prompts you to) and it should all work as it's supposed to. The missing link for me was a properly installed and configured AdobeAIR installation.

Happy hunting!
[/INDENT]

---

### Post by snerd on 2009-05-02
Thanks! Worked a charm!

---

### Post by parsim on 2009-05-08
Well against my better judgment, because Adobe hasn't yet made a product that doesn't foul up my computer, I installed Adobe AIR. It didn't work and wouldn't even uninstall:

```
"/opt/Adobe AIR/Versions/1.0/Resources/Adobe AIR Updater" -arp:uninstall
Error loading the runtime (libadobecertstore.so: cannot open shared object file: No such file or directory)
```
I hunted around until I found the answer: to make it work on a 64-bit system you need to do this:
```
sudo ln -s /usr/lib/libadobecertstore.so /usr/lib32/libadobecertstore.so
```
This allowed me to install TweetDeck, which then came up with icons but an otherwise black screen that didn't respond to anything I clicked. So now I'm getting rid of it.

---

### Post by kneewax on 2009-05-08
> **parsim said:**
> 
This allowed me to install TweetDeck, which then came up with icons but an otherwise black screen that didn't respond to anything I clicked. So now I'm getting rid of it.

Parsim, see this howto, this solved the same problem for me, works a treat now [http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

---

### Post by JBK617 on 2009-05-18
I got Air installed finally, thanks to the help, when I downloaded Twwetdeck, it shows a lock in the upper right hand corner of the icon, I double click on it and nothing happens
Any thoughts?

Thanks

---

### Post by Sukotto on 2009-06-28
> **JBK617 said:**
> I got Air installed finally, thanks to the help, when I downloaded Twwetdeck, it shows a lock in the upper right hand corner of the icon, I double click on it and nothing happens
Any thoughts?

Thanks

When you clicked the TweedDeck Download a window should pop up and ask you to save the file or open with AdobeAIR Installer. Just choose open with AdobeAIR Installer.

I made a turoial of how I installed AdobeAIR and TweetDeck [http://ubuntugreatness.blogspot.com/2009/06/installing-adobe-air-and-tweetdeck-in.html](http://ubuntugreatness.blogspot.com/2009/06/installing-adobe-air-and-tweetdeck-in.html)

---

### Post by bthodla on 2009-07-06
I can only install Adobe AIR by running:

sudo ./AdobeAIRInstaller.bin

It hangs if I run it as logged in user. Also, any AIR app such as TweetDeck or Seesmic only installs if I run the app installer as root. And even then, none of the installed apps actually work.

What am I doing wrong?

---

