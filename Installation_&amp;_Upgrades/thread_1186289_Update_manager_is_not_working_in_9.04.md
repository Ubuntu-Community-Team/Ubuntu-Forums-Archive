---
title: "Update manager is not working in 9.04"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by adam_ski on 2009-06-13
When I try to install upgrades or security updates to 9.04 the update manager hangs and I then get the error message:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-17ubuntu3.1_i386.deb
```

Does anyone know what's gone wrong? In case it's a problem with the settings in the Software Sources settings (System > Administration > Software Sources) I've taken screenshots of the tabs:

[Ubunutu Software]("http://farm3.static.flickr.com/2471/3622073778_9af4935ea1_o.png")
[Third party software]("http://farm4.static.flickr.com/3402/3622073780_d361670c6f_o.png")
[Updates]("http://farm4.static.flickr.com/3405/3622073782_bc48e96062_o.png")
[Authentication]("http://farm3.static.flickr.com/2426/3622073788_920c996374_o.png")

Thanks for your help.

---

### Post by gradinaruvasile on 2009-06-13
Try to disable the unsupported updates...

---

### Post by adam_ski on 2009-06-13
I tied that, but it still get the same error message. Also, after I click the "Install Updates" button in the Update Manager I get [this screen]("http://farm4.static.flickr.com/3397/3622105898_ed2ece3793_o.png"), saying that I am about to install software that can't be authenticated. That doesn't sound like a good thing, but I dunno what it means...

---

### Post by gradinaruvasile on 2009-06-13
click on the triangle left of NOT AUTHENTICATED
and see whats there

---

### Post by adam_ski on 2009-06-13
A load of stuff

```
NOT AUTHENTICATED
[INDENT]libcups
libcupsimage2
cups-common
cups
cups-bsd
cups-client
evolution-data-server-dbg
libedataserver1.2-11
libcamel1.2-14
libebackend1.2-0
libebook1.2-9
libecal1.2-7
libedata-book1.2-2
liedata-cal1.2-6
libegroupwise1.2-13
libgdata1.2-1
libgdata-google1.2-1
evolution-data-server
evolution-data-server-common
libtrackerclient0
tracker-utils
libtracker-gtk0
tracker-search-tool
tracker
libdeskbar-tracker
libedataserverui1.2-8
libexchange-storage1.2-3
pidgin-data
libpurple0
pidgin
cupsys
cupsys-bsd
cupsys-client
cupsys-common
libcupsys2[/INDENT]
```

---

### Post by adam_ski on 2009-06-13
Further to this, using ```
sudo apt-get update
``` via the terminal gives me ```
0% [Connecting to 128.40.33.200 (128.40.33.200)] [Connecting to 128.40.33.200 (128.40.33.200)]
``` and then the terminal hangs. I've no idea what the 128.40.33.200 IP is,  but it makes me think it's trying to go via a proxy. If that's the case, how can I stop it?

---

### Post by drs305 on 2009-06-13
> **adam_ski said:**
> I've no idea what the 128.40.33.200 IP is,  but it makes me think it's trying to go via a proxy. If that's the case, how can I stop it?

Check System, Preferences, Network Proxy to see if "Direct Internet Connection" is selected.

---

### Post by adam_ski on 2009-06-13
The direct internet connection seems to be OK - [as shown by the screenshot]("http://farm4.static.flickr.com/3660/3622658139_27960f8cda_o.png"). 

I have noticed, however, that the hosts file (/etc/hosts) contains that IP address:

```
127.0.1.1 laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
128.40.33.200 localhost laptop
```

so could that be the issue?

---

### Post by drs305 on 2009-06-13
Add the line:
> 127.0.1.1 laptop 

Put a comment symbol in front of:
128.40.33.200 localhost laptop  > # 128.40.33.200 localhost laptop

And try again. I don't know of course where the 128... came from, but if it continues to work without it just leave it commented. If it doesn't solve the issue, reverse the process.

To edit /etc/hosts:
```

gksudo gedit /etc/hosts

```

---

### Post by adam_ski on 2009-06-13
I tried that and I still get the ```
0% [Connecting to 128.40.33.200 (128.40.33.200)] [Connecting to 128.40.33.200 (128.40.33.200)]
``` which is then followed by ```
Err http://archive.ubuntu.com jaunty Release.gpg                                              
  Could not connect to 128.40.33.200:8080 (128.40.33.200), connection timed out
Err http://archive.ubuntu.com jaunty/main Translation-en_GB                                   
  Unable to connect to 128.40.33.200 8080:
```


However, I've now seen [this]("http://farm4.static.flickr.com/3652/3623519412_f2081fb61f_o.png") when looking at the settings for the wireless that Ubuntu currently has. The IP address that I've blacked out is the one I am current logged onto, but I don't think the Netmask/Prefix 255.255.255.0 should be there.

---

### Post by drs305 on 2009-06-13
I modified the new line a bit, but did you try to restart networking or reboot so the new setting can take effect?

---

### Post by adam_ski on 2009-06-13
> **drs305 said:**
> did you try to restart networking or reboot so the new setting can take effect?

Erm, no I didn't [IMG]http://yacf.co.uk/forum/Smileys/classic/embarrassed.gif[/IMG] 

.
.
.
.
.

Now I have done so, everything seems to be working again. Thanks for your help, it's really appreciated. It'd be nowhere no solving this issue if I hadn't had help from the forum.

---

