---
title: "Troubles at Settiing Up PXE Server."
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by huangyingw on 2009-04-02
hello all,
   I have set up a DHCP and atftpd server, in order to support PXE installatioin within my local network.
   I have succeeded in net boot,and go to the step of choosing archive mirror step. Bellowing are my detail step, I don't know which step cause me problem. Would be greatly appreciated, if your advise could help.
   Before choosing mirror, it prompts me that there is no a DNS server, does this neccessary in PXE installation?
   Choose a mirror of the Ubuntu archive->enter information manually->Ubuntu archive mirror hostname:(I enter the IP of the PXE and Mirror server: 192.168.0.8)->Ubuntu archive mirror directory(I enter: /ubuntu)->http proxy information (I leave blank)->finally, it prompts "the selected is either not available or does not have a valid release file on it".
   The following URL, could give you a rough eye at my apache setting:   [http://192.168.0.64/ubuntu/mirror/tw.archive.ubuntu.com/ubuntu/pool/](http://192.168.0.64/ubuntu/mirror/tw.archive.ubuntu.com/ubuntu/pool/)
   I don't know what caused this? Is it because I have not completely downloaded the archive files. For, the mirror archive is really too big and cost much time to download. Bellowing are my important part of mirror.list file:
=================================================================
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
=================================================================
Just in order to support PXE installation, could it be smaller by removing some?
   If any description not in detail, please let me know.
   Would be greatly appreciated at your advise.

---

