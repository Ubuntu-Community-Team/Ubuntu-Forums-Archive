---
title: "DPKG Error when installing ANYTHING"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Kobayashi-kun on 2009-01-28
Hi, I am using Ubuntu Studio and before I installed any updates, I installed some programs. NOW, I get a "DPKG" error which says this:

> torako@SoH-PROJEKT:~$ sudo apt-get install abiword
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Can anyone tell me how to fix this?

Whenever I say 

> torako@SoH-PROJEKT:~$ dpkg --configure -a 
sudo apt-get install -f


It says

> dpkg: requested operation requires superuser privilege


PLEASE HELP!!

~Kobayashi

---

### Post by Partyboi2 on 2009-01-28
You need to use sudo, which gives you superuser privileges. 
```
sudo dpkg --configure -a
sudo apt-get -f install
```You can read more [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Kobayashi-kun on 2009-01-28
Thanks a lot!

Just got another error now:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

OH GAWD

EDIT: I am in the middle of fixing it now. But I cant help noticing, Partiboi2, that you have just repeated what I said before, without even reading what I said. See:

[QUOTE=Myself] Whenever I say

> 
torako@SoH-PROJEKT:~$ dpkg --configure -a
sudo apt-get install -f
It says

> 
dpkg: requested operation requires superuser privilege[/QUOTE]

[QUOTE=Partiboi2]You need to use sudo, which gives you superuser privileges.

> 
sudo dpkg --configure -a
sudo apt-get -f install[/QUOTE]

*rolls eyes*

---

### Post by regala on 2009-01-28
> **Kobayashi-kun said:**
> Thanks a lot!

EDIT: I am in the middle of fixing it now. But I cant help noticing, Partiboi2, that you have just repeated what I said before, without even reading what I said. See
...
*rolls eyes*


Nope, he didn't repeat :)
look closer at the message, it says dpkg needs superuser privileges, which can be given by the use of sudo. You did NOT use sudo with DPKG.

---

### Post by Partyboi2 on 2009-01-28
I would say the reason you got 
>                               dpkg: requested operation requires superuser privilege                       could have been because you had used
>                               torako@SoH-PROJEKT:~$ dpkg --configure -a without sudo infront of it.
Can you post the results to
```
 sudo apt-get -f install
```

---

### Post by Kobayashi-kun on 2009-01-28
Ah. It worked. But...I...closed...the terminal...

Sorry.

---

### Post by Partyboi2 on 2009-01-28
Then open a terminal and 
```
sudo apt-get update
sudo apt-get upgrade
```
If you get any errors then post the output to those commands. If you get no error messages then your problem should have been solved.

---

### Post by Kobayashi-kun on 2009-01-28
Recently had to do this again. Results:

> root@SoH-PROJEKT:~# sudo dpkg --configure -a
Setting up libots0 (0.5.0-1) ...

Setting up libpq5 (8.3.5-0ubuntu8.10) ...

Setting up libenca0 (1.9-6) ...

Processing triggers for man-db ...
Setting up libdvdread3 (0.9.7-11ubuntu2) ...

Setting up libwildmidi0 (0.2.2-2) ...

Setting up libopenspc0 (0.3.99a-2) ...

Setting up libcdaudio1 (0.99.12p2-5) ...

Setting up libmjpegtools0c2a (1:1.8.0-0.2ubuntu5) ...

Setting up libloudmouth1-0 (1.4.1-1) ...

Setting up libstreams0 (0.5.11-1ubuntu2) ...

Setting up gstreamer0.10-fluendo-mpegdemux (0.10.15-1) ...
Setting up liblua50 (5.0.3-3) ...

Setting up libmms0 (0.4-2) ...

Setting up libneon27-gnutls (0.28.2-2build1) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up kdebase-runtime-data-common (4:4.1.3-0ubuntu1~intrepid1) ...
Setting up libavahi-qt3-1 (0.6.23-2ubuntu2.1) ...

Setting up libmpcdec3 (1.2.2-1build1) ...

Setting up libtwolame0 (0.3.12-1) ...

Setting up libruby1.8 (1.8.7.72-1ubuntu0.1) ...

Setting up gstreamer0.10-ffmpeg (0.10.5-1) ...
Setting up ttf-wqy-zenhei (0.6.26-2ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/wqy
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
Regenerating fonts cache... done.

Setting up vlc-data (0.9.4-1ubuntu3) ...
Setting up libsoundtouch1c2 (1.3.1-2) ...

Setting up liblualib50 (5.0.3-3) ...

Setting up libschroedinger-1.0-0 (1.0.5-1) ...

Setting up libofa0 (0.9.3-3) ...

Setting up kde-icons-oxygen (4:4.1.3-0ubuntu1~intrepid1) ...
Setting up libphonon4 (4:4.2.0-0ubuntu1) ...

Setting up kdebase-runtime-data (4:4.1.3-0ubuntu1~intrepid1) ...
Setting up libaiksaurus-1.2-data (1.2.1+dev-0.12-5) ...
Setting up libsdl-gfx1.2-4 (2.0.13-4) ...

Setting up libiptcdata0 (1.0.2+libtool01-2) ...

Setting up gstreamer0.10-schroedinger (1.0.5-1) ...
Setting up libsmpeg0 (0.4.5+cvs20030824-2) ...

Setting up libsidplay1 (1.36.59-5) ...

Setting up kdelibs5-data (4:4.1.3-0ubuntu1~intrepid4) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


Setting up gstreamer0.10-gnonlin (0.10.9-1) ...
Setting up libxvidcore4 (2:1.1.2-0.1ubuntu3) ...

Setting up openjdk-6-jre (6b12-0ubuntu6.1) ...

Setting up libstrigiqtdbusclient0 (0.5.11-1ubuntu2) ...

Setting up libx264-59 (1:0.svn20080408-0.0ubuntu1) ...

Setting up kdelibs-data (4:3.5.10-0ubuntu6) ...

Setting up libartsc0 (1.5.10-0ubuntu1) ...

Setting up libaiksaurus-1.2-0c2a (1.2.1+dev-0.12-5) ...

Setting up libdvdnav4 (4.1.2-3) ...

Setting up liblua5.1-0 (5.1.3-1) ...

Setting up libclucene0ldbl (0.9.20-3) ...

Setting up libvlccore0 (0.9.4-1ubuntu3) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up freepats (20060219-1) ...
Setting up libmpeg2-4 (0.4.1-3) ...

Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up libdvbpsi4 (0.1.5-3.1) ...

Setting up libmusicbrainz4c2a (2.1.5-2ubuntu1) ...

Setting up libmad0 (0.15.1b-3) ...

Setting up libgmyth0 (1:0.7.1-1) ...

Setting up libraptor1 (1.4.17-1) ...

Setting up libmodplug0c2 (1:0.7-7) ...

Setting up gstreamer0.10-plugins-bad-multiverse (0.10.6-1ubuntu1) ...
Setting up libmatroska0 (0.8.1-1.1) ...

Setting up libarts1c2a (1.5.10-0ubuntu1) ...

Setting up libvlc2 (0.9.4-1ubuntu3) ...

Setting up phonon-backend-gstreamer (4:4.2.0-0ubuntu1) ...
Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up gstreamer0.10-plugins-bad (0.10.8-1) ...
Setting up gstreamer0.10-plugins-ugly (0.10.9-1ubuntu0.1) ...
Setting up libaiksaurusgtk-1.2-0c2a (1.2.1+dev-0.12-5) ...

Setting up libstreamanalyzer0 (0.5.11-1ubuntu2) ...

Setting up librasqal0 (0.9.15-2) ...

Setting up phonon (4:4.2.0-0ubuntu1) ...
Setting up kdelibs4c2a (4:3.5.10-0ubuntu6) ...

Setting up librdf0 (1.0.7-1) ...

Setting up soprano-daemon (2.1.1+dfsg.1-0ubuntu1) ...
Setting up libsoprano4 (2.1.1+dfsg.1-0ubuntu1) ...

Setting up kdelibs-bin (4:4.1.3-0ubuntu1~intrepid4) ...
Setting up kdelibs5 (4:4.1.3-0ubuntu1~intrepid4) ...

Setting up kdebase-runtime-bin-kde4 (4:4.1.3-0ubuntu1~intrepid1) ...
Setting up kdebase-runtime (4:4.1.3-0ubuntu1~intrepid1) ...

Setting up khelpcenter4 (4:4.1.3-0ubuntu1~intrepid1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@SoH-PROJEKT:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 178 not upgraded.


---

### Post by shark1997 on 2009-01-28
For the superuser error:
Do you now the root password? You can use "sudo su" then "passwd"

---

### Post by Kobayashi-kun on 2009-01-29
Im going to have to switch back to Ubuntu 8.10; Ubuntu Studio needs me to do the same thing over and over again. Then I cant install anything. It says that it cant get a "exclusive lock". D:

Can someone either give me a solution to stop the flippin' thing happening all the time? I *would* like to install updates/programs. 

Or its back to normal Ubuntu 8.10. Or I go to Xubuntu or Kubuntu. :popcorn:

EDIT: Just ordered Kubuntu CD. In the meantime im going to use Ubuntu until after like 4-5 weeks. Seeing as how im from the UK and the cd will be coming from the Netherlands. I really was surprised when I found out that the CDs weren't from the Isle Of Man.

---

### Post by Kobayashi-kun on 2009-01-29
Please change the thread to solved. I have now switched back to Ubuntu Intrepid.

---

