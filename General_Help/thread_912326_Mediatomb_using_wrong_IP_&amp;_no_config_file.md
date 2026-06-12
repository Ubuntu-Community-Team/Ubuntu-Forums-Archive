---
title: "Mediatomb using wrong IP &amp; no config file"
date: 2008-09-06
forum: General Help
---

### Post by ukblacknight on 2008-09-06
I'm trying to get mediatomb working (a UPNP server, so I can share data between my N95 over wi-fi).

I'm having two problems:
1) When I start it, it's returning "Page Load Error", instead of the UI.  I've noticed it's trying to set it up on my hamachi network, which I don't want, I'd rather it be on my local IP.

2) Theres no ~/.mediatomb/ directory!  I keep seeing people mentioning about an .xml config file in there, however the directory doesn't exist.

I've uninstall and re-installed it several times, making no difference on any attempt.

Anyone have any ideas?

---

### Post by Tech Wrangler on 2008-09-14
Bump!

I'm having trouble with Mediatomb as well.  After I installed it and set it up, it would work until the server was shut down.  After that, it would ask for a password to start it again, but ignore anything I typed in (no error message).  I also could not find a config file, and occasionally it would give a 'failed to connect' browser message.  

I'm just trying to share a few music files with my N800.  Are there any other UPNP server packages that are being supported and are simple to use? Geexbox and GmediaServer seem to have been abandoned. And I really don't want to delve into MythTV...

Thanks in advance.

---

### Post by ukblacknight on 2008-09-14
I'm using fuppes now.  It's in the repos, seems simple enough!  You have to edit the config file so that it allows all IP's to connect.

Nobody every seems to reply to my posts when I need help :(

---

### Post by Tech Wrangler on 2008-09-14
Fuppes eh?  Okay, I'll give it a try.  Thanks for the response!

---

### Post by ilferra on 2009-01-04
I'm facing the same problem of Tech Wrangler,
just to share with you the "manual solution" I found:

in my Mediatomb installation the config.xml files seems located in /etc/mediatomb/config.xml

After a server shut down, at the restart, the system everytime asks for a username and a password, but it ignores anything I type in.
It seems that the server doesn't load the config.xml file with all settings.
So, the solution I found is to load manually the config.xml file using the following command 

sudo mediatomb -c /etc/mediatomb/config.xml

once executed this command, the shown link can be used to launch Mediatomb.


I hope that could help you

---

### Post by Axess_Denied on 2009-04-04
Thank ilferra, that was a very simple solution and it seemed to work out very well! I have only used MediaTomb for a few days and am curious, does it require you to recompile the database on every reload?

---

### Post by mb_webguy on 2009-04-04
I've seen this problem reported a lot, and it usually seems to be due to the same thing -- following a Mediatomb tutorial that says to run Mediatomb using sudo.

There's no reason to run Mediatomb as sudo.  If you run it the first time with sudo, it will create config files under /etc (as should any program run as root) but obviously not under the user's home.  Mediatomb also uses a different port when run as root, so the web browser link to the configuration page created in the applications menu will not point to the configuration page for Mediatomb run as a normal user.  (Btw, even if the link is pointing to the correct port, you'll only be able to pull up the configuration page if Mediatomb is running.)

I posted a [guide to installing Mediatomb]("http://ubuntuforums.org/showthread.php?p=6684782&highlight=mediatomb#post6684782") a while back based on several I had seen online but with several bad suggestions corrected.  I'm not trying to brag here, but I haven't had anyone contact me about having problems with Mediatomb after following this guide, and have had several mention it worked where they had trouble with other guides.

---

### Post by Blackworm on 2010-01-11
> **ukblacknight said:**
> 
1) When I start it, it's returning "Page Load Error", instead of the UI.  I've noticed it's trying to set it up on my hamachi network, which I don't want, I'd rather it be on my local IP.


Hi there, i dunno if this is still usefull to you... Running Hamachi, you have to edit the file /etc/defaults/mediatomb
```
sudo nano /etc/defaults/mediatomb
```

then under INTERFACE write the name of your network interface, for example eth0

[HTML]INTERFACE=eth0[/HTML]

now in the same file change the parameters of connection like

```
ROUTE_ADD="/sbin/route add -net YOUR_IP netmask 255.255.255.0"
ROUTE_DEL="/sbin/route del -net YOUR_IP netmask 255.255.255.0"
```

If you have any doubt about your machine's IP or interface, give a ifconfig
Hope it works! ;)

---

