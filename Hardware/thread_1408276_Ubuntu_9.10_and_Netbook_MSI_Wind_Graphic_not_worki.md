---
title: "Ubuntu 9.10 and Netbook MSI Wind: Graphic not working"
date: 2010-02-16
forum: Hardware
---

### Post by pabst2k on 2010-02-16
Dear Ubuntu Community,
I installed Ubuntu 9.10 (Kernel 2.6.31-19; earlier tried with -14 --> same result) on my MSI Wind U115 Hybrid with the Intel Gma500 graphic chip. I only get a resolution of 800x600. I tried the same with the Netbook Remix. Same result.
So I read a lot in different communities. But their solutions only causes errors on my Netbook. Can you help me please?!

Heres one way I tried

I followed the instructions in [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

Now heres what the terminal says. Maybe you can tell me whats wrong!?.  

pabst2k@netbook:~$ sudo wget [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh) && sh ./poulsbo.sh
--2010-02-16 16:36:24--  [http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh](http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4390 (4.3K) [text/x-sh]
Saving to: `poulsbo.sh.3'

100%[======================================>] 4,390       --.-K/s   in 0.1s    

2010-02-16 16:36:26 (35.7 KB/s) - `poulsbo.sh.3' saved [4390/4390]

GMA500 Poulsbo drivers ('poulsbo.sh acer' for AO751h support)
--2010-02-16 16:36:26--  [http://dl.dropbox.com/u/1338581/Gma500/deb/libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19686 (19K) [application/x-debian-package]
Saving to: `/tmp/libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb'

100%[======================================>] 19,686      84.6K/s   in 0.2s    

2010-02-16 16:36:27 (84.6 KB/s) - `/tmp/libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb' saved [19686/19686]

--2010-02-16 16:36:27--  [http://dl.dropbox.com/u/1338581/Gma500/deb/libva1_0.31.0-1+sds9_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/libva1_0.31.0-1+sds9_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41518 (41K) [application/x-debian-package]
Saving to: `/tmp/libva1_0.31.0-1+sds9_i386.deb'

100%[======================================>] 41,518       125K/s   in 0.3s    

2010-02-16 16:36:28 (125 KB/s) - `/tmp/libva1_0.31.0-1+sds9_i386.deb' saved [41518/41518]

--2010-02-16 16:36:28--  [http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-config_0.1_all.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-config_0.1_all.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4278 (4.2K) [application/x-debian-package]
Saving to: `/tmp/poulsbo-config_0.1_all.deb'

100%[======================================>] 4,278       --.-K/s   in 0.1s    

2010-02-16 16:36:28 (40.3 KB/s) - `/tmp/poulsbo-config_0.1_all.deb' saved [4278/4278]

--2010-02-16 16:36:28--  [http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1994 (1.9K) [application/x-debian-package]
Saving to: `/tmp/poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb'

100%[======================================>] 1,994       --.-K/s   in 0.002s  

2010-02-16 16:36:31 (1.21 MB/s) - `/tmp/poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb' saved [1994/1994]

--2010-02-16 16:36:31--  [http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2016 (2.0K) [application/x-debian-package]
Saving to: `/tmp/poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb'

100%[======================================>] 2,016       --.-K/s   in 0s      

2010-02-16 16:36:31 (42.0 MB/s) - `/tmp/poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb' saved [2016/2016]

--2010-02-16 16:36:31--  [http://dl.dropbox.com/u/1338581/Gma500/deb/psb-firmware_0.30-0ubuntu1netbook1_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/psb-firmware_0.30-0ubuntu1netbook1_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9824 (9.6K) [application/x-debian-package]
Saving to: `/tmp/psb-firmware_0.30-0ubuntu1netbook1_i386.deb'

100%[======================================>] 9,824       --.-K/s   in 0.1s    

2010-02-16 16:36:32 (90.0 KB/s) - `/tmp/psb-firmware_0.30-0ubuntu1netbook1_i386.deb' saved [9824/9824]

--2010-02-16 16:36:32--  [http://dl.dropbox.com/u/1338581/Gma500/deb/misc/psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/misc/psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 403908 (394K) [application/x-debian-package]
Saving to: `/tmp/psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb'

100%[======================================>] 403,908      481K/s   in 0.8s    

2010-02-16 16:36:34 (481 KB/s) - `/tmp/psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb' saved [403908/403908]

--2010-02-16 16:36:34--  [http://dl.dropbox.com/u/1338581/Gma500/deb/psb-modules_4.41.2-0ubuntu1~910um1_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/psb-modules_4.41.2-0ubuntu1~910um1_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 176926 (173K) [application/x-debian-package]
Saving to: `/tmp/psb-modules_4.41.2-0ubuntu1~910um1_i386.deb'

100%[======================================>] 176,926      279K/s   in 0.6s    

2010-02-16 16:36:36 (279 KB/s) - `/tmp/psb-modules_4.41.2-0ubuntu1~910um1_i386.deb' saved [176926/176926]

--2010-02-16 16:36:36--  [http://dl.dropbox.com/u/1338581/Gma500/deb/xpsb-glx_0.18-0ubuntu1netbook1_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/xpsb-glx_0.18-0ubuntu1netbook1_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1316866 (1.3M) [application/x-debian-package]
Saving to: `/tmp/xpsb-glx_0.18-0ubuntu1netbook1_i386.deb'

100%[======================================>] 1,316,866    582K/s   in 2.2s    

2010-02-16 16:36:39 (582 KB/s) - `/tmp/xpsb-glx_0.18-0ubuntu1netbook1_i386.deb' saved [1316866/1316866]

--2010-02-16 16:36:39--  [http://dl.dropbox.com/u/1338581/Gma500/deb/xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 84556 (83K) [application/x-debian-package]
Saving to: `/tmp/xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb'

100%[======================================>] 84,556       172K/s   in 0.5s    

2010-02-16 16:36:41 (172 KB/s) - `/tmp/xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb' saved [84556/84556]

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Translation-en_US       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates Release                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/universe Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [66.6kB]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic-updates/multiverse Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [20.7kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [30.7kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [5,663B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]
Fetched 170kB in 1s (113kB/s)                       
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up psb-kernel-source (4.41.6-0ubuntu1~1004jbs1) ...
Loading new psb-kernel-source-4.41.6 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.6 does not exist.
dpkg: error processing psb-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 psb-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace libdrm-poulsbo1 2.3.0-0ubuntu3netbook7 (using .../libdrm-poulsbo1_2.3.0-0ubuntu3netbook7_i386.deb) ...
Unpacking replacement libdrm-poulsbo1 ...
Setting up libdrm-poulsbo1 (2.3.0-0ubuntu3netbook7) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace libva1 0.31.0-1+sds9 (using .../libva1_0.31.0-1+sds9_i386.deb) ...
Unpacking replacement libva1 ...
Setting up libva1 (0.31.0-1+sds9) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace poulsbo-config 0.1 (using .../tmp/poulsbo-config_0.1_all.deb) ...
Unpacking replacement poulsbo-config ...
Setting up poulsbo-config (0.1) ...
Modifying xorg.conf through X-Kit...
Done

(Reading database ... 118773 files and directories currently installed.)
Preparing to replace psb-firmware 0.30-0ubuntu1netbook1 (using .../psb-firmware_0.30-0ubuntu1netbook1_i386.deb) ...
Unpacking replacement psb-firmware ...
Setting up psb-firmware (0.30-0ubuntu1netbook1) ...
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace psb-kernel-source 4.41.6-0ubuntu1~1004jbs1 (using .../psb-kernel-source_4.41.6-0ubuntu1~1004jbs1_all.deb) ...
Unpacking replacement psb-kernel-source ...
Removing old module source...
Setting up psb-kernel-source (4.41.6-0ubuntu1~1004jbs1) ...
Loading new psb-kernel-source-4.41.6 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.6 does not exist.
dpkg: error processing psb-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 psb-kernel-source
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace psb-modules 4.41.2-0ubuntu1~910um1 (using .../psb-modules_4.41.2-0ubuntu1~910um1_i386.deb) ...
Unpacking replacement psb-modules ...
Setting up psb-modules (4.41.2-0ubuntu1~910um1) ...

(Reading database ... 118773 files and directories currently installed.)
Preparing to replace xpsb-glx 0.18-0ubuntu1netbook1 (using .../xpsb-glx_0.18-0ubuntu1netbook1_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/psb/libGL.so.1.xlibmesa', not allowed
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/psb/libGL.so.1.2.xlibmesa', not allowed
Unpacking replacement xpsb-glx ...
Setting up xpsb-glx (0.18-0ubuntu1netbook1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace xserver-xorg-video-psb 0.31.0-0ubuntu1~904um1 (using .../xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb) ...
Unpacking replacement xserver-xorg-video-psb ...
Setting up xserver-xorg-video-psb (0.31.0-0ubuntu1~904um1) ...

Processing triggers for man-db ...
(Reading database ... 118773 files and directories currently installed.)
Preparing to replace poulsbo-driver-2d 1.1-0ubuntu1~904um1 (using .../poulsbo-driver-2d_1.1-0ubuntu1~904um1_all.deb) ...
Unpacking replacement poulsbo-driver-2d ...
Setting up poulsbo-driver-2d (1.1-0ubuntu1~904um1) ...

(Reading database ... 118773 files and directories currently installed.)
Preparing to replace poulsbo-driver-3d 1.1-0ubuntu1~904um1 (using .../poulsbo-driver-3d_1.1-0ubuntu1~904um1_all.deb) ...
Unpacking replacement poulsbo-driver-3d ...
Setting up poulsbo-driver-3d (1.1-0ubuntu1~904um1) ...

blacklist i915
Section "Device"
        Identifier      "GMA500"
        Driver         "psb"
        Option         "DownScale" "false"
        Option         "ExaNoComposite" "false"
        #Option     "ExaMem" "131072"
    #Option        "ExaScratch" "4"
    #Option        "ExaCached" "false"
        Option         "IgnoreACPI" "true"
        Option         "LidTimer" "false"
        Option         "NoAccel" "false"
        Option        "NoFitting" "false"
        Option         "NoPanel" "false"
        Option         "MigrationHeuristic" "greedy"
        Option         "ShadowFB" "false"
        Option         "SWcursor" "false"
        Option         "Vsync" "false"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
    Option        "RENDER" "Enable"
EndSection
--2010-02-16 16:37:15--  [http://dl.dropbox.com/u/1338581/Gma500/deb/mplayer-vaapi_20100114-1_i386.deb](http://dl.dropbox.com/u/1338581/Gma500/deb/mplayer-vaapi_20100114-1_i386.deb)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9107272 (8.7M) [application/x-debian-package]
Saving to: `/tmp/mplayer-vaapi_20100114-1_i386.deb'

100%[======================================>] 9,107,272   1019K/s   in 11s     

2010-02-16 16:37:28 (838 KB/s) - `/tmp/mplayer-vaapi_20100114-1_i386.deb' saved [9107272/9107272]

(Reading database ... 118773 files and directories currently installed.)
Preparing to replace mplayer-vaapi 20100114-1 (using .../mplayer-vaapi_20100114-1_i386.deb) ...
Unpacking replacement mplayer-vaapi ...
Setting up mplayer-vaapi (20100114-1) ...
Processing triggers for man-db ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer-skins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up psb-kernel-source (4.41.6-0ubuntu1~1004jbs1) ...
Loading new psb-kernel-source-4.41.6 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.6 does not exist.
dpkg: error processing psb-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 psb-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
ln: creating symbolic link `/usr/lib/va/drivers/psb_drv_video.so': File exists
--2010-02-16 16:37:35--  [http://dl.dropbox.com/u/1338581/Gma500/deb/misc/libflashplayer.so](http://dl.dropbox.com/u/1338581/Gma500/deb/misc/libflashplayer.so)
Resolving dl.dropbox.com... 174.129.33.139, 174.129.33.163, 174.129.33.164, ...
Connecting to dl.dropbox.com|174.129.33.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11198636 (11M) [application/octet-stream]
Saving to: `/tmp/libflashplayer.so'

100%[======================================>] 11,198,636  1.10M/s   in 10s     

2010-02-16 16:37:48 (1.04 MB/s) - `/tmp/libflashplayer.so' saved [11198636/11198636]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package flashplugin-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up psb-kernel-source (4.41.6-0ubuntu1~1004jbs1) ...
Loading new psb-kernel-source-4.41.6 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.6 does not exist.
dpkg: error processing psb-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 psb-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
[: 98: unexpected operator
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
pabst2k@netbook:~$ 

Thanks pabst2k

---

### Post by pabst2k on 2010-02-16
Another Method I tried is from this page: [http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/](http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/)

I successfully added 
[I]deb [http://ppa.launchpad.net/lucazade/gma500/ubuntu/](http://ppa.launchpad.net/lucazade/gma500/ubuntu/) karmic main and 
deb-src [http://ppa.launchpad.net/lucazade/gma500/ubuntu/](http://ppa.launchpad.net/lucazade/gma500/ubuntu/) karmic main
to the software sources but the entering 
[/I]sudo apt-get install psb-kernel-source to the terminal gets me the following error

pabst2k@netbook:~$ sudo apt-get install psb-kernel-source
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
psb-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up psb-kernel-source (4.41.6-0ubuntu1~1004jbs1) ...
Loading new psb-kernel-source-4.41.6 DKMS files...

Error! Could not find module source directory.
Directory: /usr/src/psb-kernel-source-4.41.6 does not exist.
dpkg: error processing psb-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 psb-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
pabst2k@netbook:~$ 

Then i tried to fix it with sudo aptiturde purge psb-kernel-source just with the result of getting a different error now...

pabst2k@netbook:~$ sudo aptitude purge psb-kernel-source
[sudo] password for pabst2k: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  psb-kernel-source{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2,015kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 118772 files and directories currently installed.)
Removing psb-kernel-source ...
Purging configuration files for psb-kernel-source ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

pabst2k@netbook:~$ sudo apt-get install psb-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  psb-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 407kB of archives.
After this operation, 2,019kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main psb-kernel-source 4.41.1-0ubuntu1~904um1 [407kB]
Fetched 407kB in 0s (595kB/s)         
Selecting previously deselected package psb-kernel-source.
(Reading database ... 118654 files and directories currently installed.)
Unpacking psb-kernel-source (from .../psb-kernel-source_4.41.1-0ubuntu1~904um1_all.deb) ...
Setting up psb-kernel-source (4.41.1-0ubuntu1~904um1) ...
Loading new psb-kernel-source-4.41.1 DKMS files...

Creating symlink /var/lib/dkms/psb-kernel-source/4.41.1/source ->
                 /usr/src/psb-kernel-source-4.41.1

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-19-generic LINUXDIR=/lib/modules/2.6.31-19-generic/build DRM_MODULES=psb"......(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-19-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/psb-kernel-source/4.41.1/build/ for more information.
0
0
dpkg: error processing psb-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 psb-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pabst2k on 2010-02-16
A third method kills my system. 

I entered 
*wget [http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz](http://poulsbo-karmic.angelfire.com/files/poulsbo1.tar.gz)*

*tar -zxvf poulsbo1.tar.gz*

*cd poulsbo1*

*sudo ./install.pl*
 
like descriped on [http://poulsbo-karmic.angelfire.com/](http://poulsbo-karmic.angelfire.com/)

I got no errors and rebooted. Now after booting I only get a black screen.

---

### Post by pabst2k on 2010-02-16
#4:
The tried the method from [http://www.ubuntugeek.com/howto-get-the-best-performance-from-the-gma-500-video-chipset.html](http://www.ubuntugeek.com/howto-get-the-best-performance-from-the-gma-500-video-chipset.html) in the recovery mode and it worked worked without errors but the file they supposed to change was empty/didnt exist (/boot/grub/menu.lst). Nevertheless I added the supposed line. 

I rebooted. The system works normal again but im still not able to change the Display resolution and the display is still shown as unknown. Does no one know whats going wrong?!

pabst2k

---

### Post by pabst2k on 2010-02-22
Does no one know whats going wrong?
I'm still not able to get the graphic chip working...

greets pabst2k

---

### Post by horstmacin on 2010-02-23
Hey,

I can only confirm your bug and haven't found a proper solution so far. I also tried several post but only ending with a black screen. At least I found a little workaround for the bug with the overlapping icons. I reduced the font from 10 to 8. Anyway I will let you know when I could solve it...

Cheers

---

### Post by pabst2k on 2010-02-24
Hey ubuntu users, i found the solution for the problem on [http://inpec-web.de/index.php/2010/02/msi-u115-ubuntu-9-10-karmic/comment-page-1/#comment-6](http://inpec-web.de/index.php/2010/02/msi-u115-ubuntu-9-10-karmic/comment-page-1/#comment-6)

Heres the englisch Version of what I did for Ubuntu Karmic Koala Desktop Edition 2.6.31-19-generic #56-Ubuntu (might also work with NBR :

First do an Ubuntu Update, then type to terminal

gksu gedit /etc/apt/sources.list.d/mobile.list

and add the following sources


 deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) karmic main
 
  deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu)  karmic main
 
  deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty  main
 
  deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu)  jaunty main
 
  deb [http://ppa.launchpad.net/lucazade/gma500/ubuntu/](http://ppa.launchpad.net/lucazade/gma500/ubuntu/)  karmic main
 
  deb-src [http://ppa.launchpad.net/lucazade/gma500/ubuntu/](http://ppa.launchpad.net/lucazade/gma500/ubuntu/)  karmic main
 
        deb [http://ppa.launchpad.net/lucazade/gma500/ubuntu](http://ppa.launchpad.net/lucazade/gma500/ubuntu)  karmic main 
   deb-src [http://ppa.launchpad.net/lucazade/gma500/ubuntu](http://ppa.launchpad.net/lucazade/gma500/ubuntu)  karmic main
 
  

then do ‘apt-get update’ 
then
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99D6B21CC6598A30  
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F5F2A6FE6699F3D9
  
then install the driver with

sudo apt-get install psb-kernel-source psb-firmware poulsbo-driver-3d poulsbo-driver-2d

Then enter sudo gedit /etc/modprobe.d/blacklist.conf
and just add the line“blacklist i915&#8243;

Now you have to edit the
gksu gedit /etc/X11/xorg.conf (might be empty)


  Section “Device”
 
  Identifier “GMA500&#8243;
 
  Option “AccelMethod” “EXA”
 
  Option “DRI” “on”
 
  Option “MigrationHeuristic” “greedy”
 
  Option “IgnoreACPI” “yes”
 
  Driver “psb”
 
  EndSection


 
  Section “DRI”
 
  Mode 0666
 
 
  EndSection
 
[FONT=Verdana]
The next step is 

[/FONT]sudo gedit /usr/srv/psb-kernel-source4.41.*/intel_lvds.c
in my case the star is 6.

 Now search with CTRL & F “static int intel_lvds_get_modes(struct drm_output *output)”  and comment 

  [LEFT]if (edid)
drm_add_edid_modes(output, edid);[/LEFT]
  [LEFT]these lines out so it looks like this:
[/LEFT]
  /*        if (edid) */
/*                  drm_add_edid_modes(output, edid); */
  Now do
 sudo dpkg-reconfigure psb-kernel-source


and reboot.


The last step:


sudo gedit /usr/bin/compiz 

search for

  WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx"
  and add psb so it looks like this.

  WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx psb"


Restart and everything should be fine. 

pabst2k

---

### Post by pabst2k on 2010-02-24
If you Change 

Option “AccelMethod” “UXA” 

in the xorg.conf and delete 

Option “MigrationHeuristic” “greedy”

you have a better videoperformance.

On inpec web the author announces to tell us how to play 1080p movies.
But the article hasnt been released yet. I'll give you the translation when its done

pabst2k

---

### Post by horstmacin on 2010-02-25
Wow, thanks a lot!! Just worked out for me as well.

---

