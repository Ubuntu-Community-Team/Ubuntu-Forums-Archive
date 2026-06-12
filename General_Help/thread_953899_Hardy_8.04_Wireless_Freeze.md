---
title: "Hardy 8.04 Wireless Freeze"
date: 2008-10-20
forum: General Help
---

### Post by legendofzash on 2008-10-20
I've been reading a couple of topics about the freezing issue with Hardy for the past couple of days and have yet to find a fix that works for me.  I've just installed Hardy on my frankenPC.  I've got a Linksys wireless card that uses the rt61pci driver.  I've heard that there are issues with this driver but I've yet to be able to resolve them.  Here's my problem...

Basically, whenever I try to do anything via network or internet (with the wireless connection) Hardy freezes and requires a hard reboot.  The caps lock key does flash (which indicates kernel panic I believe?).  I've used Ubuntu for a while (though I'm still a noob lol).  If I use Hardy with the wired connection, it works perfectly fine (but is REALLY inconvenient).  Any idea how I can resolve this issue would be greatly appreciated.  Once again, I apologize if there is a fix already posted somewhere that I have missed.  I've read through several topics and not found one that has worked just yet =\

---

### Post by ajmorris on 2008-10-20
> **legendofzash said:**
> I've been reading a couple of topics about the freezing issue with Hardy for the past couple of days and have yet to find a fix that works for me. I've just installed Hardy on my frankenPC. I've got a Linksys wireless card that uses the rt61pci driver. I've heard that there are issues with this driver but I've yet to be able to resolve them. Here's my problem...
 
Basically, whenever I try to do anything via network or internet (with the wireless connection) Hardy freezes and requires a hard reboot. The caps lock key does flash (which indicates kernel panic I believe?). I've used Ubuntu for a while (though I'm still a noob lol). If I use Hardy with the wired connection, it works perfectly fine (but is REALLY inconvenient). Any idea how I can resolve this issue would be greatly appreciated. Once again, I apologize if there is a fix already posted somewhere that I have missed. I've read through several topics and not found one that has worked just yet =\
 
 
Hi there,
hmm... a kernel panic from accessing the internet via a wireless card... sounds like the drivers are hooked up to the wrong device id to me... Not familiar with the Linksys cards myself, but the rt61pci driver, is that a native linux driver, or ndiswrapper? If it is native, you might find it easier, and that it works better, if you download the windows XP driver for your model card, and install the .inf driver file via ndiswrapper (sudo apt-get install ndiswrapper)
Then you can force a devid to the ndiswrapper driver, however, if this is done incorrectly, you can muck things up, and cause things like kernel panics upon use of the driver. So, once you have the ndiswrapper drivers, can you post the output of the following:
 
```
sudo lspci
```
```
sudo ndiswrapper -l
```
 
 
AJ

---

### Post by legendofzash on 2008-10-20
> **ajmorris said:**
> Hi there,
hmm... a kernel panic from accessing the internet via a wireless card... sounds like the drivers are hooked up to the wrong device id to me... Not familiar with the Linksys cards myself, but the rt61pci driver, is that a native linux driver, or ndiswrapper? If it is native, you might find it easier, and that it works better, if you download the windows XP driver for your model card, and install the .inf driver file via ndiswrapper (sudo apt-get install ndiswrapper)
Then you can force a devid to the ndiswrapper driver, however, if this is done incorrectly, you can muck things up, and cause things like kernel panics upon use of the driver. So, once you have the ndiswrapper drivers, can you post the output of the following:
 
```
sudo lspci
```
```
sudo ndiswrapper -l
```
 
 
AJ

I was really hoping that I wouldn't have to revert to the ndiswrapper.  I've never gotten that to successfully work on any of my machines x.x.

The wireless connection does work.  If I connect to the wireless and open firefox, it works until I load a page that's fairly intense (or download any decently sized files).  For instance, after a fresh install, sudo apt-get install ssh worked for a second... then when it started downloading, freeze.

I'll see what I can do with the ndiswrapper tonight.  I'm very uneducated about using it though lol.

EDIT: Also thanks for the quick response!

---

### Post by legendofzash on 2008-10-20
Sorry for the double post \\:D/

AJ: It seems that using the windows drivers with ndiswrapper has somewhat resolved the issue.  I finally got ndiswrapper to work by using ndisgtk lol.  I've been going for about 2 hours now and not a single freeze.  I haven't intensely used the internet so I don't know if the issue is completely resolved.  It's definitely better.  Doing stuff like apt-get install rtorrent caused crashes before.  Since then I've installed rtorrent, cmus, Klibido (yeah, KDE... but it runs fine on gnome for the most part lol), and a few other things.  I've also surfed quite a few websites.  Seems to be running fine (or at the least, much better lol).  Thanks a million :)

---

