---
title: "[SOLVED] P2P File Sharing"
date: 2008-07-20
forum: General Help
---

### Post by Dyffo on 2008-07-20
One of my hobbies is collecting Vintage Film Clips. When I had Windows I used various P2P progs for downloading these Videos. I used emule, Morpheus, Shareaza and Limewire.Now that I am 100 % Ubuntu I can only use amule - the search results and downloads are useless.So my question is - anyone know of a P2P system that is GOOD and works with UBUNTU. or - heaven forbid can anyone tell me how to reinstall as a second boot to Ubuntu - Windows:confused:

---

### Post by macaholic on 2008-07-20
I wouldn't highly suggest using limewire, but you can install it on ubuntu by downloading it [here]("http://www9.limewire.com/download/LimeWireLinux.deb"). And what exactly do you mean when you say the search results and downloads in amule are useless? Do you ahve the servers configured correctly?

---

### Post by BUSHYBOB on 2008-07-20
Have you tried azureus?

---

### Post by Vivaldi Gloria on 2008-07-20
I am happy with amule's download speeds. Just use websites for searching. For example:

[http://sharethefiles.com/forum/index.php](http://sharethefiles.com/forum/index.php)

---

### Post by macaholic on 2008-07-20
> **BUSHYBOB said:**
> Have you tried azureus?
I assume he's not really looking for a bit torrent client, since for those you need to go out and separately find the torrent files, which can, especially for irregular items, be very tedious and annoying. However, if he were looking for a bit torrent client I would suggest deluge over Azureus, since IMO Azureus is way too bloated and overly complicated.

**P.S. I am not supporting the use of P2P for illegal means, and be wary that such discussions, to the best of my knowledge, are prohibited from these forums. Also I am assuming, and hoping, that when he speaks of "vintage film clips" he is talking of older movies that are most likely in the public domain and free to share.**

---

### Post by Dyffo on 2008-07-20
Yep I am searching for Vintage the 1940 era - certainly not doing anything illegal - ALL are available in the public domain

---

### Post by Dyffo on 2008-07-20
Maybe I am not configured correctly - can you advise the correct server config

---

### Post by Vivaldi Gloria on 2008-07-20
> **Dyffo said:**
> Maybe I am not configured correctly - can you advise the correct server config

I do nothing special. Every time amule starts it downloads the server list of

[http://www.gruk.org/server.met](http://www.gruk.org/server.met) 

and uses only those. I also use KAD. Look for amule forums for a latest nodes.dat.

The trick with amule/emule is to download a lot of files at the same time to use your all bandwidth. I have a 440kB/s connection and I download more than 200 files at the same time to reach ~400kB/s+. I don't download popular things, I generally download files with a few number of seeds, sometimes one. That's why I need about 200 downloads to reach decent speeds. Also my computer downloads 24h/7d.

I have found that this is the only method that gives me such speeds, especially with nonpopular files.

This is also tiring. It doesn't matter how big your hard disk is, it fills quiet fast. I write 2-3 DVDs everyday to keep up.

---

### Post by Dyffo on 2008-07-20
Have been to Sharefiles.... and checked that config is O.K.  Server list is Gruk... and server is Razorback. Still no results.
When I had a-mule we flew like a bird !!!!!!!. KADEMLIA status is Running, then underneath says status - disconnected.
ED2K Status is Connected IP Port - server. ID 10429246.
ED2K Link box at the bottom is BLANK.
I am getting very frustrated and confused

---

### Post by wfp on 2008-07-20
I use frostwire the interface is almost identical to limewire. There is a .deb file on there download page just download it to the desktop and open it up. Great features lot's of sources, and fast downloads.

---

### Post by Vivaldi Gloria on 2008-07-20
> **Dyffo said:**
> Have been to Sharefiles.... and checked that config is O.K.  Server list is Gruk... and server is Razorback. Still no results.
When I had a-mule we flew like a bird !!!!!!!. KADEMLIA status is Running, then underneath says status - disconnected.
ED2K Status is Connected IP Port - server. ID 10429246.
ED2K Link box at the bottom is BLANK.
I am getting very frustrated and confused

Isn't Razorback dead? My Gruk list has no Razorback.

Go to server settings and uncheck the options

```
Update serverlists when connecting a server
Update serverlists when a client connect
```

Then clear all servers and reload Gruk's met. Gruk only gives 7 servers to me.

---

### Post by Dyffo on 2008-07-21
Will do as you suggest and let you know how it goes - at the moment i receive 189 Servers on my list !!!! - What server are you connected to - that works !!!!!!!

---

### Post by Vivaldi Gloria on 2008-07-21
> **Dyffo said:**
> Will do as you suggest and let you know how it goes - at the moment i receive 189 Servers on my list !!!! - What server are you connected to - that works !!!!!!!

Here's a snapshot of my server list. Now I'm connected to the bold one.

---

### Post by Dyffo on 2008-07-21
Found the problem !!!!!!!!!!!!! I have LOW I.D - don't know why -never had this before. Problem is my machine is networked to another machine which is running Windows X.P. so presumably that Firewall is blocking me. Any ideas ??

---

### Post by Vivaldi Gloria on 2008-07-21
> **Dyffo said:**
> Found the problem !!!!!!!!!!!!! I have LOW I.D - don't know why -never had this before. Problem is my machine is networked to another machine which is running Windows X.P. so presumably that Firewall is blocking me. Any ideas ??

Do you have a direct connection from your router to the ubuntu system? If this is the case then It doesn't matter if you have another machine in the network.  You need to forward the ports amule uses from the router to ubuntu. A default amule install requires these ports:

TCP port 4662
UDP port 4665, 4672

See the amule wiki to find out more about the port numbers. To find out how to port-forward the router look at your router's page here:

[http://portforward.com/](http://portforward.com/)

---

### Post by Dyffo on 2008-07-21
My set up is :-  Modem is Alcatel/Speedtouch 330, this I am told doesn't need special port forwarding. This then goes into my wifes Dell Computer which is running X.P. Port forwarding is set up as you have said TCP 4662 and UDP 4672 - thats it then my machine is networked on to this configuration. I only have Ubuntu installed - is there some special way that I have to configure the ports or is this automatic. amule has these settings in preferences / connection.

---

### Post by Vivaldi Gloria on 2008-07-21
> **Dyffo said:**
> My set up is :-  Modem is Alcatel/Speedtouch 330, this I am told doesn't need special port forwarding. This then goes into my wifes Dell Computer which is running X.P. Port forwarding is set up as you have said TCP 4662 and UDP 4672 - thats it then my machine is networked on to this configuration. I only have Ubuntu installed - is there some special way that I have to configure the ports or is this automatic. amule has these settings in preferences / connection.

Sorry but I know neither about your modem nor about how to port forward in XP.

A remark though, for amule you need to port forward one more port than you do with emule:

TCP port 4662
UDP port 4665, 4672

---

### Post by Dyffo on 2008-07-21
> **Vivaldi Gloria said:**
> Sorry but I know neither about your modem nor about how to port forward in XP.

A remark though, for amule you need to port forward one more port than you do with emule:

TCP port 4662
UDP port 4665, 4672

Sorry for delay in responding - decided to delete and completely re install UBUNTU - !!!!!! NOW we have a clean sheet - ALL works fine. There must have been a glitch somewhere after an upgrade. This has happened to me before. So all is well and thanks for your help

---

### Post by Vivaldi Gloria on 2008-07-21
> **Dyffo said:**
> Sorry for delay in responding - decided to delete and completely re install UBUNTU - !!!!!! NOW we have a clean sheet - ALL works fine. There must have been a glitch somewhere after an upgrade. This has happened to me before. So all is well and thanks for your help

Glad to hear that. Have fun.

---

### Post by t0p on 2008-07-21
When I hit the torrents, I'm using **Transmission**, which is installed by default in Hardy.  It isn't very configurable, but it's very simple to use.  Click on a torrent download link at, say, [thepiratebay.org]("http://thepiratebay.org").  A dialogue box opens up, asking what you want to do with the torrent file - make sure **Open With Transmission** is selected, and click on OK. Transmission automagically connects up to peers and starts downloading.

Occasionally you'll want to click on **Ask Tracker For More Peers**, maybe you'll want to limit the upload rate if you have limited bandwidth... and that's about it really.

---

