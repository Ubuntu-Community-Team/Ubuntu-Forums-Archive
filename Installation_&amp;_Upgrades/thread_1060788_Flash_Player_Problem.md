---
title: "Flash Player Problem"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by frozenfire0808 on 2009-02-05
I'm pretty new to Ubuntu but I went to Ubuntu but I went to 

[http://community.abcfamily.go.com/watch/kyle-xy/company-men-full-episode](http://community.abcfamily.go.com/watch/kyle-xy/company-men-full-episode) 

to watch an episode of Kyle XY I missed because of work and it said my flash player was not up to date to click on the link it provided 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

 and Iclicked on the link and for the version I clicked 
.deb for Ubuntu 8.04+   installed it but I still can't watch it.         

Any suggestions will be appreciated.

---

### Post by apjone on 2009-02-05
Have you restarted Firefox since?

---

### Post by frozenfire0808 on 2009-02-05
yes

---

### Post by ajgreeny on 2009-02-05
You may need to uninstall **flashplugin-nonfree** first, if that is also installed on your system.  You may also need to reinstall the adobe .deb file again.  Check exactly what is installed using synaptic.

---

### Post by frozenfire0808 on 2009-02-05
In synaptic it says the status of Adobe Flash Player 10 is installed when I checked the common tab and in the installed files tab the files mention the word flash  quite a bit.

Where is flashplugin-nonfree at?

---

### Post by frozenfire0808 on 2009-02-05
Never mind I found it. I'm going to close firefox and try the website again if it doesn't work I'll come back to this forum again .

---

### Post by frozenfire0808 on 2009-02-05
It didn't work I even tried reinstalling it. Are there any more suggestions?

---

### Post by ajgreeny on 2009-02-05
Do you have **gnash** installed?  The two certainly are not compatible and you should remove gnash if you have it.
Also have a look in FF using **about:plugins** in the address bar.  It will list all your plugins and their files and pathways to them. You can also see what is showing in Tools > Add-ons and the plugin tab will show you which are enabled.

---

### Post by frozenfire0808 on 2009-02-05
I went to the synaptic package manager found gnash and it says it isn't installed.

I went to about:plugins in the address bar (I don't know what the FF was)

the following were in bold  and had information about them

Default Plugin
Demo Print Plugin for unix/linux
iTunes Application Detector
Java(TM) Plug-in 1.6.0_07-b06
Totem Web Browser Plugin 2.22.1
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
VLC Multimedia Plugin (compatible Totem 2.22.1)
Windows Media Player Plug-in 10 (compatible; Totem)
DivX® Web Player
QuickTime Plug-in 7.2.0


I went to add-ons in the tools tab the following were in bold

Default Plugin, Demo Print Plugin for unix/linux, DixX Web Player, Helix DHA Plugin: RealPlayer G2 Plug-In Compatible (compatible;Totem), iTunes Application Detector, Java (TM) Plug-in 1.6.0_07-b06, QuickTime Plug-in 7.2.0, Shockwave Flash the details for this one is Shockwave Flash 9.0 r100 ,  Totem Web Browser Plugin 2.22.1, Windows Media Plug-in 10 (compatible;totem)

All of those are enabled I tried disabling the Shockwave Flash but it didn't work so I re enabled it.

---

### Post by frozenfire0808 on 2009-02-06
Help is still needed.  I decided to post this because the post from the last person is a day old.

---

### Post by ajgreeny on 2009-02-06
Sorry if you didn't understand , but the FF was Firefox, and you should type **about:plugins** in the address bar of that, where you type other web addresses (such as [www.ubuntu.com](www.ubuntu.com))  You will get a screen like this where mine shows Shockwave Flash 10.0 r15

---

### Post by frozenfire0808 on 2009-02-06
When I went to about:plugins  the shockwave flash part had this

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes


unfortunately it is too outdated for me to watch the episode of Kyle XY I missed.

how do I get rid of this version and install the newer version which is on this webpage    [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

and says  

Download Adobe Flash Player
Adobe Flash Player
Linux, x86

Different operating system or browser?

Browser: Firefox, Mozilla, SeaMonkey

Learn more | System requirements | Distribute Flash Player | Installation instructions 

and gives me the following versions to possibly download 
.tar.gz for Linux
.rpm for Linux
YUM for Linux
.deb for Ubuntu 8.04+

---

### Post by ajgreeny on 2009-02-07
Download the .deb file for ubuntu 8.04 to your normal download folder (**Desktop** or **download**, whatever you use) and double click it, but first, remove whichever flash you have at the moment using synaptic and searching for **flash**.  Different install methods can put the various files in lots of different locations, which can sometimes baffle the system.

---

