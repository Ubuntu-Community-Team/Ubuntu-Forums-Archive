---
title: "Thai website not working"
date: 2008-09-13
forum: General Help
---

### Post by pretender? on 2008-09-13
I am wanting to re format my windows pc that my wife uses to ubuntu  but she listens to  radio.sanook.com the internet radio but it only seems to play in internet explorer think it uses shockwave 

Firefox wont even play the songs on windows with this site.  How can i get the internet radio songs to work from that website in ubuntu

Have tried 

Iceape
Konqueror 
Rythembox 
Firefox 2.0.0.16
Opera

With no Luck.  I am running Gutsy 

Regards 
Pretender

---

### Post by kokkus on 2008-09-13
I don't know that internet radio but if it uses shockwave it should work if you have installed flashplugin-nonfree. you can find it with synatic or in terminal: sudo apt-get install flashplugin-nonfree

---

### Post by mb_webguy on 2008-09-13
> **kokkus said:**
> I don't know that internet radio but if it uses shockwave it should work if you have installed flashplugin-nonfree. you can find it with synatic or in terminal: sudo apt-get install flashplugin-nonfree

No, the Flash plugin plays Flash.  Shockwave's something else.  So far, Adobe hasn't seen fit to create a Shockwave plugin for Linux.

You're going to have to install Wine.  Follow the instructions on [this page]("http://www.winehq.org/site/download-deb") to get the latest version.  Next, you have a choice.  You can follow the rest of the instructions on [this page]("https://help.ubuntu.com/community/Shockwave") to install Shockwave using the Firefox version.  Alternatively, you can install IE using IEs4Linux as described on [this page]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu"), and then install the Shockwave plugin.

---

### Post by cariboo on 2008-09-13
According to a new feature in Firefox 3.0.2 (manage content plugins) you need a ms-wmp plugin that is not available for the Linux version of Firefox. If you can get the classic windows media player to work in wine you may be ok. 

Jim

---

### Post by kokkus on 2008-09-13
Sorry, my bad.
But yes, it will work with IEs4Linux.
[COLOR="Red"]Use it on your own risk as it is not very stabile and has it's bugs.[/COLOR]
For example, 
1. activx pages will bug and freeze the browser.
2. It doesn't really close when you click the close button. 
So minimize it insted.

Good luck:)

---

### Post by kokkus on 2008-09-13
**[COLOR="Blue"]WMP on Ubuntu:[/COLOR]**
Here's a version that works perfect with Wine:
[http://rapidshare.com/files/26503856/WMP11-WindowsXP-x86-DEU-noWGA.zip.html](http://rapidshare.com/files/26503856/WMP11-WindowsXP-x86-DEU-noWGA.zip.html)

Enjoy!

---

