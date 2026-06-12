---
title: "[SOLVED] KTorrent has no network connectivity"
date: 2008-08-29
forum: General Help
---

### Post by Zorael on 2008-08-29
Simply put, my recently-installed KTorrent can't access my network. Starting it in debug mode, it apparently sees my UPnP router and tries to register port forwarding, but when it tries to connect to it, it fails. It loads torrents properly but can't access peers/seeds to start downloading. It can't open URLs, and it can't download the peerguardian ip filter ban list thingie.

```
$ ktorrent --debug
Bound to port 6881
Cannot open /home/zorael/.kde/share/apps/ktorrent/groups : No such file or directory
Loading /home/zorael/.kde/share/apps/ktorrent/tor0/
Encoding : UTF-8
OutputPath = *<filename of active torrent>*
Starting download
Loading list of peers from /home/zorael/.kde/share/apps/ktorrent/tor0/peer_list (num_peers =  0)
Loading 0 active chunk downloads
Selected tracker *<tracker address>*/announce (tier = 1)
Switching to tracker *<tracker address>*/announce
Doing tracker request to url : *<tracker address>*
[B]Loading plugin UPnP
Trying to find UPnP devices on the local network[/B]
Loading plugin Info Widget
Loading plugin Import
File limit allready at maximum
Data limit allready at maximum
**Detected IGD Ambit OS/1.0 UPnP/1.0 AMBIT-UPNP/1.0**
Error : Could not connect to host *<tracker address>*
Selected tracker *<tracker address>*/announce (tier = 1)
**Failed to download http://192.168.0.2:80/Public_UPNP_gatedesc.xml : Could not connect to host http://192.168.0.2:80/Public_UPNP_gatedesc.xml.**
```
I've tried removing all its settings in ~/.kde/share/apps/ktorrent and ~/.kde/share/config/ktorrentrc, but upon having the program recreate them the problem remains.

This is curious; I've never had any problems with the program before. The only thing different from my earlier installations is that this time it's a vanilla 32-bit flavor. So far I've also gotten the "firefox starts in offline mode" bug, too (which was easily worked around.)

This is in Hardy, with the KTorrent package available from the main repository.
```
$ apt-cache policy ktorrent
ktorrent:
  Installed: 2.2.5-0ubuntu1
  Candidate: 2.2.5-0ubuntu1
  Version table:
 *** 2.2.5-0ubuntu1 0
        500 http://se.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
```
Any ideas? :<

---

### Post by Zorael on 2008-08-30
Nevermind, sucky plastic Netgear routers suck, marking as solved at a lack of remove thread functionality.

---

