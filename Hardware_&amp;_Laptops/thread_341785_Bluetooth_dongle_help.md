---
title: "Bluetooth dongle help"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by michie86 on 2007-01-19
hello.. could somebody please teach me how i can use my bluetooth dongle in linux? i just bought one for my mobile phone and gnokii. it's a billionton bluetooth dongle UBTCR500-B.. is it known to work with linux? i hope so.. but in the instructions included in the package only windows is the OS mentioned :confused:  .. i only got to read this when i had already bought it since it's inside the package.. could anyone please help me? i really need to get this working.. thanks 

btw im using ubuntu 6.06.. thanks again

---

### Post by swamytk on 2007-01-19
Blue tooth stack service is running at startup? If not, try installing bluetooth related packages through synaptic (search bluetooth in synaptic).

---

### Post by michie86 on 2007-01-19
> **swamytk said:**
> Blue tooth stack service is running at startup? If not, try installing bluetooth related packages through synaptic (search bluetooth in synaptic).

what do u mean at startup? sorry if this is a stupid question, i'm really puzzled.. thanks again

---

### Post by Zimmer on 2007-01-19
have you loaded gnome-bluetooth from Synaptic?   I used that on Breezy to communicate with a Bluetooth dongle. I think it provides a Manager to discover and connect and a file transfer interface, both quite basic.  I now have a USB data cable and attach my phone directly via USB.... but I will have a go at installing gnome-bluetooth again to see if I can help you...
Check in the Device manager that the PC has recognised the dongle on the USB  controller..

OK. gnome bluetooth allows me to connect and send files from phone to PC 
 via Applications>Accessories> Bluetooth File Sharing  and see this [http://ubuntuforums.org/showthread.php?t=337965&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=337965&highlight=bluetooth)

 , but the general opinion at present is that THIS works a lot better...

[http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth)

I have not  tried it (and do not intend to).. but have a read of the thread and see if it fits your needs...

---

### Post by michie86 on 2007-01-19
hello.. i read the sites u gave and i have a question again.. it mentioned kdebluetooth, will that work for me too? or it should be gnome? i'm sorry but i'm confused..

i looked at the synaptic manager but i can't find gnome-blueooth.. though i found blueZ all installed.. hope you culd help me again.. thanks ;)

---

### Post by Zimmer on 2007-01-19
[http://ubuntuforums.org/showthread.php?t=338333&page=2&highlight=kde+applications+on+gnome](http://ubuntuforums.org/showthread.php?t=338333&page=2&highlight=kde+applications+on+gnome)

read that regarding KDE apps on Gnome and vice versa...  

as for finding gnome-bluetooth, have you enabled the extra Repositories..

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

As for gnome-bluetooth.. I quote from the README
> This package contains a controller class, GnomebtController, to control
Bluetooth devices, and a simple GUI to explore which devices are
available (gnome-bluetooth-manager).  An OBEX server is available,
gnome-obex-server.  This will receive files sent via Bluetooth to your
PC, and save them in your home directory.  The program gnome-obex-send
enables you to send files.  It is used by the Nautilus component --
select the files you want to send and choose "Send via Bluetooth..."
from the context menu.
So, if the dongle is in the USB port you can type    gnome-bluetooth-manager   in a terminal and you will get a very basic popup application that will try and scan for and detect available BT devices.
Launching Bluetooth File Sharing (from Accessories) will allow you to pass files from one to the other...  very basic..  but at least you will get a clue as to whether the dongle works.

---

### Post by michie86 on 2007-01-20
hello again.. the adding of extra repositories require internet connection? coz i currently have no connection on linux, i do the internet on my win partition.. coz im still having problems with detecting my modem, somebody said i need to compile my kernel to a 2.6.16 for me to be able to detect my modem. i currently have a 2.6.15 kernel.. oh, and a questione popped into my mind, if i compile my kernel, will it affect the applications i installed? like xampp for linux and gnokii perhaps?

oh..a nd i think i mentioned this before, i need the bluetooth connection for me to access my phone through gnokii.. i did a little research on using bluetooth in linux and i came about this article on the net

<a href ="http://pratyeka.org/rfcomm/"> http://pratyeka.org/rfcomm/</a>

do you think that is ok and will work? coz if the repositories need internet connection then that will be another problem for me.. 

thanks for your time and patience ;)

---

### Post by michie86 on 2007-01-20
sorry about that link.. i don't know how to create one.. hehe

---

### Post by michie86 on 2007-01-20
i tried a few of the steps said in that site.. 

when i type hciconfig, i get these

hci0:   Type: USB
        BD Address: 00:02:72:B0:00:26 ACL MTU: 120:20 SCO MTU: 64:0
        UP RUNNING PSCAN ISCAN
        RX bytes:379 acl:0 sco:0 events:17 errors:0
        TX bytes:319 acl:0 sco:0 commands:17 errors:0

does this mean that the dongle is recognized and may work with ubuntu?
shall i proceed with the other steps?

loads of thanks ;)

---

### Post by Zimmer on 2007-01-20
> **michie86 said:**
> i tried a few of the steps said in that site.. 

when i type hciconfig, i get these

hci0:   Type: USB
        BD Address: 00:02:72:B0:00:26 ACL MTU: 120:20 SCO MTU: 64:0
        UP RUNNING PSCAN ISCAN
        RX bytes:379 acl:0 sco:0 events:17 errors:0
        TX bytes:319 acl:0 sco:0 commands:17 errors:0

does this mean that the dongle is recognized and may work with ubuntu?
shall i proceed with the other steps?

loads of thanks ;)

Yes, it is recognised and up. I would suggest you get your modem running first so that you can use the Synaptic Package Manager to obtain software ....

---

### Post by michie86 on 2007-01-21
wow.. am glad that my dongle is being recognized.. ;)
and thanks again for your reply.. ok i'll follow your tip, i'll make my modem work first by compiling my kernel.. then i'll do the gnome bluetooth.. ;)

---

### Post by michie86 on 2007-01-23
hello.. i'm back now.. :) 

i tried adding the repositories, i followed the instructions from the site you gave..
i did it the "terminal way"

so i changed the sources.list contents.. then after the 
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
and
sudo apt-get update

i think i got it running but with some 'err'and 'could not resolve' lines and when i'm almost done (97%) i then encountered 'failed to fetch' messages..

here's what's in my terminal during the process.. hope you guys could help me again.. 

Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security Release.gpg
  Could not resolve 'ph.security.ubuntu.com'
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security Release
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Sources
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Sources
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Sources
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Sources
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Sources
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Sources
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial Release.gpg
  Could not resolve 'ph.archive.canonical.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Sources
  Could not resolve 'ph.security.ubuntu.com'
Ign [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial Release
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Sources
  Could not resolve 'ph.security.ubuntu.com'
Ign [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial/main Packages
Err [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial/main Packages
  Could not resolve 'ph.archive.canonical.com'
Get:1 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper Release.gpg [189B]
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper Release.gpg
  Could not resolve 'ph.medibuntu.sos-sts.com'
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper Release
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Packages
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Packages
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Sources
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Sources
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Packages
  Could not resolve 'ph.medibuntu.sos-sts.com'
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Packages
  Could not resolve 'ph.medibuntu.sos-sts.com'
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Sources
  Could not resolve 'ph.medibuntu.sos-sts.com'
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Sources
  Could not resolve 'ph.medibuntu.sos-sts.com'
Get:2 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper Release [34.8kB]
Get:5 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release [50.9kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release
Get:6 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports Release [38.4kB]
Get:7 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/main Packages [619kB]
Get:8 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:9 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:10 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:11 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/main Sources [255kB]
Get:12 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:13 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Sources [975kB]
Get:14 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
Get:15 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/main Packages [131kB]
Get:16 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:17 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages [21.6kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
Get:18 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/multiverse Packages [964B]
Get:19 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/main Sources [48.3kB]
Get:20 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:21 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Sources [3530B]
Get:22 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get:23 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/main Packages [13.0kB]
Get:24 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:25 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/universe Packages [43.5kB]
Get:26 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/multiverse Packages [2486B]Get:27 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/main Sources [4308B]
Get:28 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:29 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/universe Sources [10.9kB]
Get:30 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/multiverse Sources [2126B]
Get:31 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
97% [31 Sources gzip 0] [Connecting to ph.archive.ubuntu.com (195.248.90.35)]
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:32 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages [24.8kB]
97% [32 Packages gzip 0]                                            2045B/s 58s
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 4821kB in 42m0s (1913B/s)
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not resolve 'ph.archive.canonical.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)  Could not resolve 'ph.archive.canonical.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://ph.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


but after this, i checked the synaptic package manager and there are new stuffs there even the gnome-bluetooth.. but i was just wondering wether this 'failed to fetch' and other messages would have effects afterwards? also worried bout the 'Some index files failed to download, they have been ignored, or old ones used instead.'

hoping for your help.. thanks :wink:

---

### Post by Zimmer on 2007-01-24
To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code)

You only add the country code before yopur LOCAL archive.  sources .
You appear to have added a country code to the security  repositories and other non-local repositories.

> Failed to fetch [http://ph.security.ubuntu.com/ubuntu...ty/Release.gpg](http://ph.security.ubuntu.com/ubuntu...ty/Release.gpg) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...er/Release.gpg](http://ph.medibuntu.sos-sts.com/repo...er/Release.gpg) Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.archive.canonical.com/ubun...al/Release.gpg](http://ph.archive.canonical.com/ubun...al/Release.gpg) Could not resolve 'ph.archive.canonical.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...86/Packages.gz](http://ph.security.ubuntu.com/ubuntu...86/Packages.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...86/Packages.gz](http://ph.security.ubuntu.com/ubuntu...86/Packages.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...86/Packages.gz](http://ph.security.ubuntu.com/ubuntu...86/Packages.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...86/Packages.gz](http://ph.security.ubuntu.com/ubuntu...86/Packages.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz](http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz](http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz](http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz](http://ph.security.ubuntu.com/ubuntu...rce/Sources.gz) Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.archive.canonical.com/ubun...86/Packages.gz](http://ph.archive.canonical.com/ubun...86/Packages.gz) Could not resolve 'ph.archive.canonical.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...86/Packages.gz](http://ph.medibuntu.sos-sts.com/repo...86/Packages.gz) Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...86/Packages.gz](http://ph.medibuntu.sos-sts.com/repo...86/Packages.gz) Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...rce/Sources.gz](http://ph.medibuntu.sos-sts.com/repo...rce/Sources.gz) Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...rce/Sources.gz](http://ph.medibuntu.sos-sts.com/repo...rce/Sources.gz) Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://ph.archive.ubuntu.com/ubuntu/...rce/Sources.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/...86/Packages.gz) Sub-process gzip returned an error code (1)

find the relevant entries in your sources.list  for these repositories and remove the country code....

> Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...86/Packages.gz](http://ph.medibuntu.sos-sts.com/repo...86/Packages.gz) Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo...rce/Sources.gz](http://ph.medibuntu.sos-sts.com/repo...rce/Sources.gz) Could not resolve 'ph.medibuntu.sos-sts.com'
And it might be worth commenting out the PLF repository completely for the time being...

---

### Post by michie86 on 2007-01-25
hello again.. i did what you said.. i removed some of the local mirrors.. i also commented out the PLF repositories.. everything was almost workin fine till i got two 'failed to fetch' messages again.. here's what happened.. 

Get:1 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Get:4 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper Release
Get:6 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release [50.9kB]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [4886B]
Get:9 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [2389B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports Release
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [94.7kB]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Sources
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:11 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
99% [11 Sources gzip 0] [Waiting for headers] [Waiting for headers]  2880B/s 0s
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:12 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages [24.8kB]
99% [Waiting for headers]                                           15.0kB/s 0s
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6460B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [50.6kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2782B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [18.3kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [968B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6354B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [520B]
Fetched 288kB in 4m37s (1038B/s)
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://ph.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

i think it's beacuse of that 'gzip: stdin: not in gzip format'..
ive read some threads about it and they say change http to ftp..
is that alright? i hope so.. maybe i'll give it a try.. and i wish this won't get me into bigger troubles.. i'll update you on what happens next.. thanks ;)

---

### Post by michie86 on 2007-01-25
finally! :o i think i got my repositories now.. first i changed all http to ftp in my sources.list file.. bu then i got this

Err [ftp://archive.canonical.com](ftp://archive.canonical.com) dapper-commercial/main Packages
  Unable to fetch file, server said '"/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz": Is not a file  '

so i changed archive.canonical's back to http.. so now i got all ftp except for that one.. tried again and i think i got it this time! :D 

here it is

Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security Release.gpg
Get:2 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper Release.gpg
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates Release.gpg
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports Release.gpg
Get:3 [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper Release [34.8kB]
Get:4 [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates Release [50.9kB]
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/main Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/restricted Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/universe Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/multiverse Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/main Sources
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/restricted Sources
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/universe Sources
Get:5 [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports Release [38.4kB]
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/multiverse Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/main Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/restricted Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/universe Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/multiverse Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/main Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/restricted Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/universe Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper/multiverse Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/main Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/universe Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/main Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/universe Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/main Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/universe Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/main Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/universe Sources
Hit [ftp://ph.archive.ubuntu.com](ftp://ph.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 175kB in 3m0s (969B/s)
Reading package lists... Done

whoa! am i doing right? now i'll try to instal gome-bluetooth.. i'll update you again soon! thanks so much! ;)

---

### Post by michie86 on 2007-01-25
hello again.. i'm happy to inform you that i got bluetooth-gnome installed now and i have also tried sending a file to my phone and it worked! thank you so much! :D 

now i'll try to connect to my phone using bluetooth and gnokii as what i wanted in the first place.. thanks again! you've been a great help! ;)

---

### Post by Zimmer on 2007-01-25
Glad you have managed to sort out your Sources list..  let's hope you can find an acceptable solution for your Bluetooth needs..

---

### Post by michie86 on 2007-01-31
hello.. I'm here again.. 

i tried to install the binaries of gnokii and I encountered problems again.. 
this is what happened after I hit dpkg -i [package name.deb]

dpkg: dependency problems prevent configuration of gnokii: 
 gnokii depends on libbluetooth2 (>= 3.0); however: 
  Package libbluetooth2 is not installed. 
 gnokii depends on libc6 (>= 2.3.6-6); however: 
  Version of libc6 on system is 2.3.6-0ubuntu20. 
 gnokii depends on libgnokii3; however: 
  Package libgnokii3 is not installed. 
 gnokii depends on libusb-0.1-4 (>= 2:0.1.12); however: 
  Version of libusb-0.1-4 on system is 2:0.1.10a-22ubuntu1. 
dpkg: error processing gnokii (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 gnokii 

so i tried to look for the packages of libbluetooth2 ,  libc6 (>= 2.3.6-6), libusb-0.1-4 (>= 2:0.1.12).. I got them from packages.debian.org/unstable/

but I was just wondering wether installig these packages would have bad effects o my system? like, will my gnome-bluettoth still work as it did before (the problem we just fixed, thanks again)?

thanks,

---

### Post by Zimmer on 2007-02-01
Version 0.6.12 of gnokii ias available to me via Synaptic, looks like it is in the Universe repositories, so no need to mess with .deb files unless you are trying to install a more recent version.....

My advice would be that Synaptic is the best way forward to avoid Dependency hell.

> but I was just wondering wether installig these packages would have bad effects o my system? like, will my gnome-bluettoth still work as it did before (the problem we just fixed, thanks again)?
No idea ! But (think positively)if there are bad consequences you will learn a lot trying to clean it up and start again :)

---

### Post by michie86 on 2007-02-02
I tried installing the packages and now I have two broken packages :( in my system
oh no..
I tried fixing the broken packages but still no success

sudo apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-10 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

so I downloaded tzdata and tried to install it but this is what happens

dpkg -i tzdata_2007a-1_all.deb
(Reading database ... 69881 files and directories currently installed.)
Unpacking tzdata (from tzdata_2007a-1_all.deb) ...
dpkg: error processing tzdata_2007a-1_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/NZ', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 tzdata_2007a-1_all.deb

so I ended up still having two broken packages..
any way to restore my system?
then after that I'm thinking of installing gnokii 0.6.12 via synaptic instead of 0.6.14 as what you've said..

thanks

---

### Post by michie86 on 2007-02-08
hello.. just want to inform you that I now have my system back to normal.. Only, I re-installed both os.. 

Thanks for all your help :)

---

