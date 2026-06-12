---
title: "CD / DVD drive does not work"
date: 2009-12-27
forum: Hardware
---

### Post by J.23.espinosa.13 on 2009-12-27
CD / DVD drive does not work
 

 I currently have a HP pavillion dv6205us laptop with ubuntu 9.10. My situation is that I can't get my cd/dvd drive to work. I put in a disk and the light goes on 2 or 3 times and it does nothing. I went to this post:
 

 Obtained from:
 [http://ubuntuforums.org/showthread.php?t=807834](http://ubuntuforums.org/showthread.php?t=807834)
 

 [COLOR=#000080]1. Open a terminal window.

2. Execute the following terminal command to install the necessary packages (make sure to approve any prompts):
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread4

3. Execute the following terminal command:
sudo /usr/share/doc/libdvdread4/install-css.sh

After you have executed the above terminal commands, insert a DVD into your drive. Totem will open and the movie will begin playing.[/COLOR]
 

  Below is what output of the terminal when I did what was posted


 xavier@Javier-Tesla:~$ sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3  
 [sudo] password for xavier:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 E: Couldn't find package libdvdread3  
 

 xavier@Javier-Tesla:~$ sudo apt-get install totem-xine libxine1-ffmpeg libdvdread4  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 libdvdread4 is already the newest version.  
 libdvdread4 set to manually installed.  
 The following packages were automatically installed and are no longer required:  
   binutils-static  
 Use 'apt-get autoremove' to remove them.  
 The following extra packages will be installed:  
   libxine1-bin  
 The following NEW packages will be installed:  
   libxine1-bin libxine1-ffmpeg totem-xine  
 0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.  
 Need to get 1,880kB of archives.  
 After this operation, 4,354kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) karmic/main libxine1-bin 1.1.16.3-0ubuntu4 [1,393kB]  
 Get:2 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) karmic/main libxine1-ffmpeg 1.1.16.3-0ubuntu4 [434kB]  
 Get:3 [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) karmic-updates/universe totem-xine 2.28.2-0ubuntu3 [52.5kB]  
 Fetched 1,880kB in 28s (65.4kB/s)                                               
 Selecting previously deselected package libxine1-bin.  
 (Reading database ... 133449 files and directories currently installed.)  
 Unpacking libxine1-bin (from .../libxine1-bin_1.1.16.3-0ubuntu4_i386.deb) ...  
 Selecting previously deselected package libxine1-ffmpeg.  
 Unpacking libxine1-ffmpeg (from .../libxine1-ffmpeg_1.1.16.3-0ubuntu4_i386.deb) ...  
 Selecting previously deselected package totem-xine.  
 Unpacking totem-xine (from .../totem-xine_2.28.2-0ubuntu3_all.deb) ...  
 Processing triggers for man-db ...  
 Setting up libxine1-bin (1.1.16.3-0ubuntu4) ...  
 

 Setting up libxine1-ffmpeg (1.1.16.3-0ubuntu4) ...  
 

 Setting up totem-xine (2.28.2-0ubuntu3) ...  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place  
 

 

 

 xavier@Javier-Tesla:~$ sudo /usr/share/doc/libdvdread4/install-css.sh  
 --2009-12-27 12:31:51--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb) 
 Resolving packages.medibuntu.org... 88.191.82.11  
 Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.  
 HTTP request sent, awaiting response... 200 OK  
 Length: 36812 (36K) [application/octet-stream]  
 Saving to: `/tmp/dvdcss-kaS3di/libdvdcss.deb'  
 

 100%[======================================>] 36,812      43.9K/s   in 0.8s     
 

 2009-12-27 12:32:08 (43.9 KB/s) - `/tmp/dvdcss-kaS3di/libdvdcss.deb' saved [36812/36812]  
 

 Selecting previously deselected package libdvdcss2.  
 (Reading database ... 133525 files and directories currently installed.)  
 Unpacking libdvdcss2 (from .../dvdcss-kaS3di/libdvdcss.deb) ...  
 Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...  
 

 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place  
 xavier@Javier-Tesla:~$ 



and I did what was recommended but with   libdvdread4 and it seem to be accomplished in the terminal , but still the problem persist.


 
 Also when I go to Places/Computer   and right click on the cd/dvd drive and go to properties on basic everything is unknown and on permissions it says “The permissions of “CD/DVD Drive” could not be determined.
 

 I went to this post
[http://ubuntuforums.org/showthread.php?t=807667](http://ubuntuforums.org/showthread.php?t=807667)
 and went to the post that are recommended in there and still the problem persist.


Note I am a Begginer

---

### Post by brunoscunha on 2009-12-28
I have the same issue. On 9.04 the cd/dvd working and after upgrading and event after a fresh install the cd/dvd drive is not recognized on 9.10.
I wento to fstab and saw no entry for the cd/dvd drive.
How can I solve this. I don't know how to add a device on fstab.
My laptop is a HP/Compaq 6910p
Thank you

---

