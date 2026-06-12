---
title: "Iphone remote app with Windows XP, iTunes in VirtualBox xVM"
date: 2008-10-12
forum: General Help
---

### Post by mrming on 2008-10-12
I have an iPhone 3G and would like to use Apple's Remote application to control the music on my Ubuntu 8.04 (Hardy) machine.

I have iTunes running in a VirtualBox (Sun version) VM using Host Interface Networking. I can see the shared library from all the machines on my local network, both wired and wireless.

I can't however see the iPhone and therefore can't configure it as a remote. It just doesn't appear in the devices list in iTunes despite the fact that iTunes is configured to look for remotes.

Can anybody suggest any reasons why this might be?

---

### Post by maogianan on 2008-10-13
Hi,

This is exactly what I'm trying to do too.

I hope you share the solution if you find one.

---

### Post by maogianan on 2008-10-14
Maybe this can help:
Remote uses TCP port 3689 and UDP port 5353 to communicate with your iTunes or Apple TV. 

You need to make sure that these ports are open.

From [http://support.apple.com/kb/TS1741](http://support.apple.com/kb/TS1741)

---

### Post by ethanep on 2008-10-19
I also would love to do the same. I can't figure out how though. I did port forward  those two ports to the VM but it didn't work.

I think what would be the best option is to have the host emulate two Ethernet cards, one for the host and one for the VM. Is that possible? How would you set that up?

---

### Post by laxwrestler on 2009-02-24
wow i would love to have this functionality.  anyone have any updates on this?

---

### Post by pelao00 on 2009-05-10
Hi, a have iphone 2g firmware 2.2.1 with apple remote 1.2.1 and virtualbox 2.2.2 on ubuntu 9.04.  My vm is Windows XP Professional and the remote app is working using bridge network.  check if you have the bridge with eth0 or eth1 if you are using wireless.  that should work.

---

### Post by Gliitch on 2009-06-26
Ah thanks dood!! Been trying to do this for ages : D Works a treat ^_^ (FW 3.0)

---

### Post by greysocks on 2009-12-14
Amazing!  This has been bugging me for a while now, and I've just sorted it.

Just to re-iterate:

Shut your vm down and go to the vm settings window.  Select **Network** settings, and go to the tab for the adapter you're using (mine was **Adapter 1**).  Originally my "*Attached to:*" was set to **NAT**.  I changed it to "_**Bridged Adapter**_" and chose my active ethernet adapter "*eth1*".

Boot up the vm and voila.  I can now use my iPod touch as a remote.

I am happy now :)

What has made me _**really**_ happy is that this has also solved the problem I've been having with Genius.  It used to fail every time I tried to activate it. Now it's working beautifully.
[COLOR=Gray]
Ubuntu 9.04, VBox 2.2.2, Win XP, iTunes 9.0.1.8[/COLOR]

---

