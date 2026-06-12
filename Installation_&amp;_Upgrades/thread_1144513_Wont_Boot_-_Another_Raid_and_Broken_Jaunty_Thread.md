---
title: "Wont Boot - Another Raid and Broken Jaunty Thread"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by AzT3K on 2009-04-30
Hi Guys,

To cut a long story short I have a partially updated computer that wont load ubuntu and a series of package conflicts that now makes updating impossible unless i can figure out how to resolve them....

Just some background:

I have a amd athlon x2 on a nf4 chipset.  I have two 2x250gb hdds running in raid0 arrays on a sataII bus. one of the arrays has an ext3 partition with my intrepid installation and also swap partition.

Installation in the first place was a headache but after i learned bout dmraid and the alternate install disc it made things easy.  i just downloaded the alternate install amd64 version and i was away.

However here's my problem,

I just attempted to upgrade to jaunty, although what i think happened was that the dist upgrade changed my package sources file and when the download terminated early these sources remained unchanged so when my computer did an upgrade, rather than a dist-upgrade, it installed a whole lot of new packages and not the updated kernel.  When my computer boots i get ejected out into a busybox shell giving an error something along the lines of 

Alert! Gave up waitng for /dev/mapper/nvidia_caghibdf1 to respond

[I will reboot and see what it looks like and update this post later.]

I thought the logical thing to do was to check dmraid and the /dev/mapper directory to see if anything was there - there was nothing just a file called "control"

I ran dmraid -ay and it issued a message about the being no block devices.

at this point i realised i wasn't going to get very far with the current busy box shell so i booted from a 8.10 x86 live CD i had sitting around and did a sudo apt-get install dmraid and it installed fine (1.0.0.rc14) and my raid arrays were instantly visible in /dev/mapper i mounted the one that had intrepid installed and mounted it to /mnt.

I then tried to chroot to it, but it couldn't find /bin/bash and eventually read somewhere in a redhat guide that trying to chroot wont work if the architecture is different between the current system and the the one you are trying to chroot to (x86 vs x64).

I then downloaded the new jaunty AMD64 live cd and booted, then issued the apt-get install dmraid command...

```

ubuntu@ubuntu:~$ sudo apt-get install dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdmraid1.0.0.rc15
The following NEW packages will be installed:
  dmraid libdmraid1.0.0.rc15
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 140kB of archives.from here 
After this operation, 459kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com jaunty/main libdmraid1.0.0.rc15 1.0.0.rc15-6ubuntu2 [105kB]
Get:2 http://archive.ubuntu.com jaunty/main dmraid 1.0.0.rc15-6ubuntu2 [35.1kB]
Fetched 140kB in 15s (9045B/s)                                                 
Selecting previously deselected package libdmraid1.0.0.rc15.
(Reading database ... 103503 files and directories currently installed.)
Unpacking libdmraid1.0.0.rc15 (from .../libdmraid1.0.0.rc15_1.0.0.rc15-6ubuntu2_amd64.deb) ...
Selecting previously deselected package dmraid.
Unpacking dmraid (from .../dmraid_1.0.0.rc15-6ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up libdmraid1.0.0.rc15 (1.0.0.rc15-6ubuntu2) ...

Setting up dmraid (1.0.0.rc15-6ubuntu2) ...
update-initramfs is disabled since running on read-only media
update-initramfs is disabled since running on read-only media

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I saw it installed 1.0.0.rc15 compared to 1.0.0.rc14 which was the default behaviour in 8.10.

I cd to /dev/mapper to see what got loaded - Only one of the two arrays was activated and it wasn't the one with the old 8.10 file system which is contrast to version 1.0.0.rc14 so i called "sudo dmraid -ay" which found the other array, activated it, which made it visible in /dev/mapper/ - i believe this is related to a bug I have seen in other threads but isn't my problem - but could be in the future if i can get my current install to recognise my install drive.

```

ubuntu@ubuntu:/dev/mapper$ ls
control  nvidia_iebhaeae  nvidia_iebhaeae1
ubuntu@ubuntu:/dev/mapper$ sudo dmraid -ay
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdb: "sil" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_iebhaeae" already active
RAID set "nvidia_caghibdf" was activated
RAID set "nvidia_iebhaeae1" already active
RAID set "nvidia_caghibdf1" was activated
RAID set "nvidia_caghibdf5" was activated
ubuntu@ubuntu:/dev/mapper$ ls
control          nvidia_caghibdf1  nvidia_iebhaeae
nvidia_caghibdf  nvidia_caghibdf5  nvidia_iebhaeae1


```

Mounted the array to /mnt, bound directories from current root file system to the newly mounted file system and chrooted to the old file system and SUCCESS!!:

```

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/mapper/nvidia_caghibdf1 /mnt
ubuntu@ubuntu:/mnt$ sudo cp {/,}etc/resolv.conf
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}proc
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}sys
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}dev
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
root@ubuntu:/#

```

So here is where i get stuck.

I found in another thread that perhaps the linux kernel was not updated so i ran " uname -a " from the busybox console i got right back at the start when my system wouldn't boot. and it said: Linux ubuntu 2.6.26-11-generic - which isn't jaunty's kernel (Linux ubuntu 2.6.28-11-generic) (what i get now as i work off the 9.04 live cd)

So here's what i think is causing the problem:

apt-get update:
```

root@ubuntu:/# apt-get update
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://nz.archive.ubuntu.com jaunty Release.gpg                            
Ign http://nz.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://nz.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty/multiverse Translation-en_US
Get:1 http://nz.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://nz.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://nz.archive.ubuntu.com jaunty-backports Release.gpg
Ign http://nz.archive.ubuntu.com jaunty-backports/main Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-backports/restricted Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-backports/universe Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US
Hit http://nz.archive.ubuntu.com jaunty Release                
Get:2 http://nz.archive.ubuntu.com jaunty-updates Release [49.6kB]
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://archive.canonical.com jaunty Release                                                                                              
Ign http://archive.canonical.com jaunty/partner Packages                                                                                     
Ign http://archive.canonical.com jaunty/partner Sources                                                                                      
Hit http://nz.archive.ubuntu.com jaunty-backports Release                                                                                    
Hit http://nz.archive.ubuntu.com jaunty/main Packages                                                                                        
Hit http://nz.archive.ubuntu.com jaunty/restricted Packages                                                                                  
Hit http://archive.canonical.com jaunty/partner Packages                                                                                     
Hit http://nz.archive.ubuntu.com jaunty/main Sources                                                                                         
Hit http://nz.archive.ubuntu.com jaunty/restricted Sources                                                                                   
Hit http://nz.archive.ubuntu.com jaunty/universe Packages                                                                                    
Hit http://nz.archive.ubuntu.com jaunty/universe Sources                                                                                     
Hit http://nz.archive.ubuntu.com jaunty/multiverse Packages                                                                                  
Hit http://nz.archive.ubuntu.com jaunty/multiverse Sources                                                                                   
Get:3 http://nz.archive.ubuntu.com jaunty-updates/main Packages [22.6kB]                                                                     
Hit http://archive.canonical.com jaunty/partner Sources                                                                                      
Get:4 http://nz.archive.ubuntu.com jaunty-updates/restricted Packages [14B]                                                                  
Get:5 http://nz.archive.ubuntu.com jaunty-updates/main Sources [7664B]                                                                       
Get:6 http://nz.archive.ubuntu.com jaunty-updates/restricted Sources [14B]                                                                   
Get:7 http://nz.archive.ubuntu.com jaunty-updates/universe Packages [6798B]                                                                  
Get:8 http://nz.archive.ubuntu.com jaunty-updates/universe Sources [14B]                                                                     
Get:9 http://nz.archive.ubuntu.com jaunty-updates/multiverse Packages [14B]                                                                  
Get:10 http://nz.archive.ubuntu.com jaunty-updates/multiverse Sources [14B]                                                                  
Hit http://nz.archive.ubuntu.com jaunty-backports/main Packages                                                                              
Hit http://nz.archive.ubuntu.com jaunty-backports/restricted Packages                                                                        
Hit http://nz.archive.ubuntu.com jaunty-backports/universe Packages                                                                          
Hit http://nz.archive.ubuntu.com jaunty-backports/multiverse Packages                                                                        
Fetched 87.0kB in 13s (6342B/s)                                                                                                              
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.freedesktop.PackageKit --type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StateHasChanged string:'cache-update''
E: Sub-process returned an error code

```

We have an error - i'm not sure how relevant it is so i tried 

apt-get upgrade:
```

root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libsox-fmt-ao: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-ffmpeg: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-mp3: Depends: libsox1 (>= 14.2.0) but it is not installed
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.16.3-0ubuntu1) but 1.1.15-0ubuntu3.3 is installed
  moc-ffmpeg-plugin: Depends: moc (= 1:2.5.0~alpha3-3ubuntu2) but 1:2.5.0~alpha3-3ubuntu1.1 is installed
  mpeg4ip-server: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
  openmovieeditor: Depends: libgavl1 (>= 1.1.0) but it is not installed
                   Depends: libjack0 (>= 0.116.1) but 0.109.2-3ubuntu1 is installed
  vlc: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
E: Unmet dependencies. Try using -f.

```

which worked until they hit these, the above output is all i get now, again at first i was not sure how relevant they were so i tried 

apt-get dist-upgrade:
```

root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libsox-fmt-ao: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-ffmpeg: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-mp3: Depends: libsox1 (>= 14.2.0) but it is not installed
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.16.3-0ubuntu1) but 1.1.15-0ubuntu3.3 is installed
  moc-ffmpeg-plugin: Depends: moc (= 1:2.5.0~alpha3-3ubuntu2) but 1:2.5.0~alpha3-3ubuntu1.1 is installed
  mpeg4ip-server: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
  openmovieeditor: Depends: libgavl1 (>= 1.1.0) but it is not installed
                   Depends: libjack0 (>= 0.116.1) but 0.109.2-3ubuntu1 is installed
  vlc: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
E: Unmet dependencies. Try using -f.

```

which lead me to

apt-get -f install:
```

root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcucul-dev libjaxp1.3-java libarts1c2a libgstreamer0.10-0-dbg libgnomedb3-bin libgoffice-0-6-common liblzo1 libpigment0.3-5
  libxerces2-java libraw1394-dev libgda3-3-dbg libgsf-1-114-dbg gstreamer0.10-plugins-ugly-dbg libgoffice-0-6 epiphany-browser-dbg
  libnss3-1d-dbg libartsc0-dev libxalan2-java amarok-engine-xine libboost-python1.34.1 libyaml-syck-perl qstat
  libboost-program-options1.34.1 bsh-gcj libsctp1 libgnomedb3-4-dbg liboobs-1-4-dbg libdc1394-22-dev libnspr4-0d-dbg python2.5-dbg
  lksctp-tools nautilus-dbg libfontconfig1-dbg libmaildir4 knetworkconf libloudmouth1-0-dbg libxft2-dbg libatk1.0-dbg libtheora-dev
  evolution-data-server-dbg libxerces2-java-gcj akonadi-server bsh libgtk2.0-0-dbg libgtkhtml3.14-dbg libgnomedb3-4 libdcop3-jni akonadi-kde
  libcaptury0 videotrans libgsf-gnome-1-114 kvm libdcop3-java libxml2-dbg libifp4 gstreamer0.10-plugins-base-dbg libgnomedb3-common
  libgnomevfs2-0-dbg python-numeric-dbg libgfortran2 exim4 libgnomeui-0-dbg bridge-utils totem-dbg libxalan2-java-gcj libgail-gnome-dbg
  libatspi-dbg libgsm1-dev libjline-java libgoffice-dbg libnjb5 libgsf-gnome-1-114-dbg libggzdmod6 libjaxp1.3-java-gcj libgda3-sqlite
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  jackd libcelt0 libffado0 libgavl1 libjack-dev libjack0 libsox-fmt-alsa libsox-fmt-base libsox-fmt-oss libsox1 libx264-65 libxine1
  libxine1-bin libxine1-console libxine1-gnome libxine1-misc-plugins libxine1-x moc sox
Suggested packages:
  libxine1-doc libxine-doc
The following packages will be REMOVED:
  libsox-fmt-gsm libsox-fmt-sndfile libsox0
The following NEW packages will be installed:
  libcelt0 libffado0 libgavl1 libsox1 libx264-65
The following packages will be upgraded:
  jackd libjack-dev libjack0 libsox-fmt-alsa libsox-fmt-base libsox-fmt-oss libxine1 libxine1-bin libxine1-console libxine1-gnome
  libxine1-misc-plugins libxine1-x moc sox
14 upgraded, 5 newly installed, 3 to remove and 245 not upgraded.
8 not fully installed or removed.
Need to get 0B/8074kB of archives.
After this operation, 9552kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 378453 files and directories currently installed.)
Preparing to replace libsox-fmt-base 14.0.1-2build2 (using .../libsox-fmt-base_14.2.0-1_amd64.deb) ...
Unpacking replacement libsox-fmt-base ...
Replacing files in old package libsox-fmt-gsm ...
dpkg: error processing /var/cache/apt/archives/libsox-fmt-base_14.2.0-1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/sox/libsox_fmt_sndfile.so', which is also in package libsox-fmt-sndfile
Errors were encountered while processing:
 /var/cache/apt/archives/libsox-fmt-base_14.2.0-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

dpkg --configure -a:
```

root@ubuntu:/# dpkg --configure -a
dpkg: dependency problems prevent configuration of openmovieeditor:
 openmovieeditor depends on libgavl1 (>= 1.1.0); however:
  Package libgavl1 is not installed.
 openmovieeditor depends on libjack0 (>= 0.116.1); however:
  Version of libjack0 on system is 0.109.2-3ubuntu1.
dpkg: error processing openmovieeditor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxine1-ffmpeg:
 libxine1-ffmpeg depends on libxine1-bin (= 1.1.16.3-0ubuntu1); however:
  Version of libxine1-bin on system is 1.1.15-0ubuntu3.3.
dpkg: error processing libxine1-ffmpeg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mpeg4ip-server:
 mpeg4ip-server depends on libx264-65 (>= 1:0.svn20081230); however:
  Package libx264-65 is not installed.
dpkg: error processing mpeg4ip-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of moc-ffmpeg-plugin:
 moc-ffmpeg-plugin depends on moc (= 1:2.5.0~alpha3-3ubuntu2); however:
  Version of moc on system is 1:2.5.0~alpha3-3ubuntu1.1.
dpkg: error processing moc-ffmpeg-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsox-fmt-ao:
 libsox-fmt-ao depends on libsox1 (>= 14.2.0); however:
  Package libsox1 is not installed.
dpkg: error processing libsox-fmt-ao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libx264-65 (>= 1:0.svn20081230); however:
  Package libx264-65 is not installed.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsox-fmt-ffmpeg:
 libsox-fmt-ffmpeg depends on libsox1 (>= 14.2.0); however:
  Package libsox1 is not installed.
dpkg: error processing libsox-fmt-ffmpeg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsox-fmt-mp3:
 libsox-fmt-mp3 depends on libsox1 (>= 14.2.0); however:
  Package libsox1 is not installed.
dpkg: error processing libsox-fmt-mp3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openmovieeditor
 libxine1-ffmpeg
 mpeg4ip-server
 moc-ffmpeg-plugin
 libsox-fmt-ao
 vlc
 libsox-fmt-ffmpeg
 libsox-fmt-mp3

```

So it looks like I have some package conflicts / depenency problems that are blocking my upgrade.

Am I right in making that assumption?
how do i get around these?

if i try to use apt-get remove libsox-fmt-base i get a lot of dependency errors.

Cheers

---

### Post by AzT3K on 2009-04-30
having a look through this seems to be the problem, of course apt-get -f install doesn't work, so i have to come up with a work around:

```

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libsox-fmt-ao: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-ffmpeg: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-mp3: Depends: libsox1 (>= 14.2.0) but it is not installed
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.16.3-0ubuntu1) but 1.1.15-0ubuntu3.3 is installed
  moc-ffmpeg-plugin: Depends: moc (= 1:2.5.0~alpha3-3ubuntu2) but 1:2.5.0~alpha3-3ubuntu1.1 is installed
  mpeg4ip-server: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
  openmovieeditor: Depends: libgavl1 (>= 1.1.0) but it is not installed
                   Depends: libjack0 (>= 0.116.1) but 0.109.2-3ubuntu1 is installed
  vlc: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
E: Unmet dependencies. Try using -f.

```

and if i try this:
```

apt-get install libsox1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsox1: Conflicts: libsox0 but 14.0.1-2build2 is to be installed
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.16.3-0ubuntu1) but 1.1.15-0ubuntu3.3 is to be installed
  moc-ffmpeg-plugin: Depends: moc (= 1:2.5.0~alpha3-3ubuntu2) but 1:2.5.0~alpha3-3ubuntu1.1 is to be installed
  mpeg4ip-server: Depends: libx264-65 (>= 1:0.svn20081230) but it is not going to be installed
  openmovieeditor: Depends: libgavl1 (>= 1.1.0) but it is not going to be installed
                   Depends: libjack0 (>= 0.116.1) but 0.109.2-3ubuntu1 is to be installed
  vlc: Depends: libx264-65 (>= 1:0.svn20081230) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


```

root@ubuntu:/# apt-get dselect-upgrade libsox0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libsox-fmt-ao: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-ffmpeg: Depends: libsox1 (>= 14.2.0) but it is not installed
  libsox-fmt-mp3: Depends: libsox1 (>= 14.2.0) but it is not installed
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.16.3-0ubuntu1) but 1.1.15-0ubuntu3.3 is installed
  moc-ffmpeg-plugin: Depends: moc (= 1:2.5.0~alpha3-3ubuntu2) but 1:2.5.0~alpha3-3ubuntu1.1 is installed
  mpeg4ip-server: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
  openmovieeditor: Depends: libgavl1 (>= 1.1.0) but it is not installed
                   Depends: libjack0 (>= 0.116.1) but 0.109.2-3ubuntu1 is installed
  vlc: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installed
E: Unmet dependencies. Try using -f.

```
hmmmm

---

### Post by AzT3K on 2009-05-06
So I gave up attempting to get this working again and reinstalled - however it wasn't simple...

Firstly i backed up the install drive to an external hdd, then I downloaded the amd64 alternate install cd and started it up - it all went smoothly until i had to choose an install disk.  It couldn't detect my raid array (because dmraid rc15 was installed) so i went to the install menu and started a shell in the installer environment and typed dmraid -ay and it found everything. so then i exited out of the shell and went back to the installer and my install array was visible again so I installed as per usual.

After that I booted it up and found myself in the same situation as before the install -> kicked out into the busy box.  I tried dmraid -ay and exit and the system jammed just like before.  -I'm unsure if it found the drives or not - as i write this after the fact - previously it just said no block devices found, but either way the system wouldn't boot with dmraid rc15 installed.

I read some more and found out that dmraid rc15 is broken.

so...

I booted into the x64 live cd i had also downloaded and ran
```
sudo apt-get install dmraid
```

the result was that dmraid rc15 was installed which oddly enough works okay in the live session environment - not automatically but when you type
```
sudo dmraid -ay
```

it detects the raid arrays

so i mounted the disk like this:
```
sudo mount -t ext4 /dev/mapper/nvidia_caghibdf1 /mnt
```

as i had changed the file system on the drive from ext3 to ext4 and it was fine i could access it from /mnt

I went to the intrepid package repository and downloaded the x64 versions of these files:

[http://packages.ubuntu.com/intrepid/libdmraid1.0.0.rc14](http://packages.ubuntu.com/intrepid/libdmraid1.0.0.rc14)
[http://packages.ubuntu.com/intrepid/dmraid](http://packages.ubuntu.com/intrepid/dmraid)

I copied these to the /mnt folder where my install drive was mounted

then i chrooted to the install drive like this:
```

ubuntu@ubuntu:/mnt$ sudo cp {/,}etc/resolv.conf
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}proc
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}sys
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}dev
ubuntu@ubuntu:/mnt$ sudo chroot /mnt

```

then i manually installed the rc14 version of dmraid from the packages i had downloaded like this:
```

dpkg -i libdmraid1.0.0.rc14_1.0.0.rc14-2ubuntu12_amd64.deb
dpkg -i dmraid_1.0.0.rc14-2ubuntu12_amd64.deb

```

then i ran:
```
dmraid -r
``` 

to see what was going on - it had found my drives then i ran:
```
dmraid --version
```

it was rc14 not rc15 which was the desired result.

so i updated the system / boot config like so:
```

update-initramfs
update-grub

```

then i rebooted off the raid array and it kicked me out into the busy box with the same message about the install drive not responding or existing so i typed:
```

dmraid -ay
exit

```

and the system booted so its still not working 100%, but at least i can get into the system now...

---

