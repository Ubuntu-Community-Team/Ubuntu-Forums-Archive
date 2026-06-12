---
title: "Apt-Get not working correctly?"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Whisp3r on 2009-07-20
I'm trying to figure out what's going on with my apt-get. 

I do an 'sudo apt-get install kismet,", apt-get grabs the correct .deb from the respository, and installs kismet. It looks like the files for usr/bin are getting installed, but nothing is going into the etc/kismet folder. Apt-get seems to create the correct folders, but then doesn't make any of the files. I think apt-get is having some kind of problem installing into /etc? But I can't figure out what. Thoughts?

---

### Post by bacil on 2009-07-20
This is full list of kismet files have you got all of them ?

```

kismet: /etc/kismet/ap_manuf                                                  
kismet: /etc/kismet/client_manuf                                              
kismet: /etc/kismet/kismet.conf                                               
kismet: /etc/kismet/kismet_drone.conf                                         
kismet: /etc/kismet/kismet_ui.conf                                            
kismet: /etc/others-menu/0000_kismet.desktop                                  
kismet: /usr/bin/kismet                                                       
kismet: /usr/bin/kismet_client                                                
kismet: /usr/bin/kismet_drone                                                 
kismet: /usr/bin/kismet_server                                                
kismet: /usr/share/doc/kismet/DEVEL.client                                    
kismet: /usr/share/doc/kismet/DEVEL.groupmap                                  
kismet: /usr/share/doc/kismet/DEVEL.ipmap                                     
kismet: /usr/share/doc/kismet/DEVEL.ssidmap                                   
kismet: /usr/share/doc/kismet/README.Debian                                   
kismet: /usr/share/doc/kismet/README.extras                                   
kismet: /usr/share/doc/kismet/README.gz                                       
kismet: /usr/share/doc/kismet/changelog.Debian.gz                             
kismet: /usr/share/doc/kismet/changelog.gz                                    
kismet: /usr/share/doc/kismet/copyright                                       
kismet: /usr/share/doc/kismet/extra/Makefile                                  
kismet: /usr/share/doc/kismet/extra/Makefile.in                               
kismet: /usr/share/doc/kismet/extra/buzzme/Makefile                           
kismet: /usr/share/doc/kismet/extra/buzzme/Makefile.in                        
kismet: /usr/share/doc/kismet/extra/buzzme/buzzme.c.gz                        
kismet: /usr/share/doc/kismet/extra/buzzme/sharp_char.h.gz                    
kismet: /usr/share/doc/kismet/extra/cwgd2gpsdrive.sh                          
kismet: /usr/share/doc/kismet/extra/gpsdrive-1.32-heading.patch               
kismet: /usr/share/doc/kismet/extra/gpsxml-sanitize.cc.gz                     
kismet: /usr/share/doc/kismet/extra/ieee-manuf-tr.sh                          
kismet: /usr/share/doc/kismet/extra/kismet-1.3.dtd.gz                         
kismet: /usr/share/doc/kismet/extra/kismet-1.4.dtd.gz                         
kismet: /usr/share/doc/kismet/extra/kismet-1.5.dtd.gz                         
kismet: /usr/share/doc/kismet/extra/kismet-1.6.1.dtd.gz                       
kismet: /usr/share/doc/kismet/extra/kismet-1.6.2.dtd.gz                       
kismet: /usr/share/doc/kismet/extra/kismet-1.6.dtd.gz                         
kismet: /usr/share/doc/kismet/extra/kismet-2.9.1.dtd.gz                       
kismet: /usr/share/doc/kismet/extra/kismet-2005-03.dtd.gz                     
kismet: /usr/share/doc/kismet/extra/kismet-3.1.0.dtd.gz                       
kismet: /usr/share/doc/kismet/extra/kismet-gps-1.0.dtd.gz                     
kismet: /usr/share/doc/kismet/extra/kismet-gps-2.9.1.dtd.gz                   
kismet: /usr/share/doc/kismet/extra/kismet2cwgd.cc.gz                         
kismet: /usr/share/doc/kismet/extra/kismet2xml.cc.gz                          
kismet: /usr/share/doc/kismet/extra/kismet_watchdog.sh                        
kismet: /usr/share/doc/kismet/extra/kismetcsv.sql                             
kismet: /usr/share/doc/kismet/extra/listchan-bsd.pl                           
kismet: /usr/share/doc/kismet/extra/listchan.pl                               
kismet: /usr/share/doc/kismet/extra/manuf_update.sh                           
kismet: /usr/share/doc/kismet/extra/multi-gpsmap.sh                           
kismet: /usr/share/doc/kismet/extra/pcap-to-tuntap.c.gz                       
kismet: /usr/share/doc/kismet/scripts/gpsmap-helper-earthamaps                
kismet: /usr/share/kismet/wav/alert.wav                                       
kismet: /usr/share/kismet/wav/junk_traffic.wav                                
kismet: /usr/share/kismet/wav/new_network.wav                                 
kismet: /usr/share/kismet/wav/traffic.wav                                     
kismet: /usr/share/man/man1/kismet.1.gz                                       
kismet: /usr/share/man/man1/kismet_drone.1.gz                                 
kismet: /usr/share/man/man5/kismet.conf.5.gz                                  
kismet: /usr/share/man/man5/kismet_drone.conf.5.gz
kismet: /usr/share/man/man5/kismet_ui.conf.5.gz
kismet: /usr/share/menu/kismet

```

---

### Post by Whisp3r on 2009-07-20
Not by a long shot. apt-get doesn't seem to be making most of them.

Edit: I stand corrected. I found my kismet.conf file in usr/local/etc... I'm confused why apt-get is doing this.

---

### Post by bacil on 2009-07-20
Works fine here.. just installed it (for test)

what exactly is output of your apt-get ?

---

### Post by Whisp3r on 2009-07-20
> andrew@silver-laptop:/var/cache/apt/archives$ sudo apt-get install kismet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sox festival gpsd
The following NEW packages will be installed:
  kismet
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 960kB of archives.
After this operation, 2417kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe kismet 2008-05-R1-4build1 [960kB]
Fetched 960kB in 8s (115kB/s)                                                  
Selecting previously deselected package kismet.
(Reading database ... 117213 files and directories currently installed.)
Unpacking kismet (from .../kismet_2008-05-R1-4build1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up kismet (2008-05-R1-4build1) ...

Processing triggers for menu ...
andrew@silver-laptop:/var/cache/apt/archives$ 

Here it is.

---

### Post by bacil on 2009-07-20
Wierd...

apt-get gets everything .. seems like package is messed up on your mirror.

my download from uk mirror worked perfectly. 

```

[+33% 00:01:08]-bacil@one:~$ sudo apt-get install kismet                               
Reading package lists... Done                             
Building dependency tree                                  
Reading state information... Done                         
The following extra packages will be installed:           
  libadns1 libportaudio2 wireshark wireshark-common       
Suggested packages:                                       
  sox festival gpsd adns-tools                            
The following NEW packages will be installed              
  kismet libadns1 libportaudio2 wireshark wireshark-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.                               
After this operation, 44.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y                                   
Get: 1 http://gb.archive.ubuntu.com jaunty/main libadns1 1.4-2 [57.9kB]
Get: 2 http://gb.archive.ubuntu.com jaunty/universe wireshark-common 1.0.7-1ubuntu1 [10.3MB]
Get: 3 http://gb.archive.ubuntu.com jaunty/universe kismet 2008-05-R1-4build1 [960kB]
Get: 4 http://gb.archive.ubuntu.com jaunty/main libportaudio2 19+svn20071207-0ubuntu7 [55.8kB]
Get: 5 http://gb.archive.ubuntu.com jaunty/universe wireshark 1.0.7-1ubuntu1 [623kB]
Fetched 12.0MB in 4min 44s (42.1kB/s)
Selecting previously deselected package libadns1.
(Reading database ... 119174 files and directories currently installed.)
Unpacking libadns1 (from .../libadns1_1.4-2_i386.deb) ...
Selecting previously deselected package wireshark-common.
Unpacking wireshark-common (from .../wireshark-common_1.0.7-1ubuntu1_i386.deb) ...
Selecting previously deselected package kismet.
Unpacking kismet (from .../kismet_2008-05-R1-4build1_i386.deb) ...
Selecting previously deselected package libportaudio2.
Unpacking libportaudio2 (from .../libportaudio2_19+svn20071207-0ubuntu7_i386.deb) ...
Selecting previously deselected package wireshark.
Unpacking wireshark (from .../wireshark_1.0.7-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up libadns1 (1.4-2) ...

Setting up wireshark-common (1.0.7-1ubuntu1) ...

Setting up kismet (2008-05-R1-4build1) ...

Setting up libportaudio2 (19+svn20071207-0ubuntu7) ...

Setting up wireshark (1.0.7-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu .

```

and all files are present

---

### Post by Whisp3r on 2009-07-20
Well, I wonder what the heck is going on. I complete removed every file I could find by hand of kismet after removing it, then I did a fresh install, complete with new download and all, and here's the resulting locate -e kismet:

andrew@silver-laptop:/var/cache/apt/archives$ locate -e kismet
/etc/kismet
/home/andrew/.config/awn/custom-icons/sudo-kismet
/home/andrew/.local/share/Trash/info/kismet.trashinfo
/home/andrew/Documents/test/mytarget-01.kismet.csv
/home/andrew/Documents/test/mytarget-01.kismet.netxml
/home/andrew/Documents/wep/mytarget-01.kismet.csv
/home/andrew/Documents/wep/mytarget-01.kismet.netxml
/usr/share/gnome-games/gtali/pixmaps/kismet-none.svg
/usr/share/gnome-games/gtali/pixmaps/kismet1.svg
/usr/share/gnome-games/gtali/pixmaps/kismet2.svg
/usr/share/gnome-games/gtali/pixmaps/kismet3.svg
/usr/share/gnome-games/gtali/pixmaps/kismet4.svg
/usr/share/gnome-games/gtali/pixmaps/kismet5.svg
/usr/share/gnome-games/gtali/pixmaps/kismet6.svg
/var/lib/dpkg/info/kismet.list
/var/lib/dpkg/info/kismet.postrm

---

