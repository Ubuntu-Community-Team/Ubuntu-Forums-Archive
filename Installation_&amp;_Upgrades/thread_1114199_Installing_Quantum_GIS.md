---
title: "Installing Quantum GIS"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2009-04-02
I've updated QGIS installation here @ [http://ubuntuforums.org/showthread.php?t=1180347]("http://ubuntuforums.org/showthread.php?t=1180347")

---

### Post by ajgreeny on 2009-04-02
Use ```
gksudo gedit /etc/apt/sources.list
```in terminal and add the two repository lines manually, then in terminal use the two final commands to update the package database and then install qgis.

---

### Post by Technophobia on 2009-04-02
1. At the top desktop bar go to: System > Administration > **Software Sources**

2. Click the "Third-Party Software" Tab

3. Add your items to that list and then hit close to auto update your list of available packages.

4. Open Synaptic package Manager or a console window and install your package.

Good luck

---

### Post by ajgreeny on 2009-04-02
Yes you can do it the way Technophobia says as well as my way.  I was telling you the manual way as it may help you in future to understand the system more fully.

---

### Post by badaveil on 2009-04-03
Technophobia & ajgreeny,

Firstly, thank you for such a fast reply, one in GUI mode, the other in script mode. Excellent! As I'm not a programmer, I first tried Technophobia's advice and successfully followed step 1,2 and 3. During update, a NO PUBKEY error (as in the result of the command line entry) came up so I decided to follow ajgreeny's advice and entered the gksudo line then the 2 deb lines but nothing happened so I decided to go ahead with the 2 sudo lines and got results to a point the output stopped. I followed the advice and realized the system needed updates so I entered the "sudo apt-get install qgis" and down they came. The last line was "ldconfig deferred processing now taking place" and I didn't know what to do seeing so many error outputs but I did earlier scan through the pdf manual and saw that I needed to type "qgis" to start the GIS application. I tried it and HEY PRESTO! the GIS application works. I later found out the QGIS start application was automatically installed under education. Cool!

[IMG]http://lh5.ggpht.com/_yJ5Rhn3UxL4/SdbhyMxG4XI/AAAAAAAACCQ/mq8r2Cptmx8/s800/Screenshot-2.png[/IMG]
main screen with data of Peninsular Malaysia

[IMG]http://lh6.ggpht.com/_yJ5Rhn3UxL4/SdaZ9beSiyI/AAAAAAAACBw/1z4hCehtZgE/s800/Screenshot-1.png[/IMG]
qgis search result from Synaptic Package Manager

As you can see in the upper pix, it works! The original Ver 1.0.0 was updated to Ver 1.0.1.

For your information, my Town Planning Department in Malaysia in the next few years has intentions to migrate to OSS desktops in line with the Ministry's OSS policy. Since our department is a heavy user of GIS, I wanted to promote Ubuntu as the OSS desktop and Quantum GIS as the OSS GIS. I believe I am a lone user in OSS in the department but I plan to spearhead OSS with my limited knowledge in Ubuntu 8.0.4. You two really made my day!

Again, thank you so much

RESULT OF COMMAND LINE ENTRY

badaveil@ubuntu:~$ deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main
bash: deb: command not found
badaveil@ubuntu:~$ deb-src [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main
bash: deb-src: command not found
badaveil@ubuntu:~$ gksudo gedit /etc/apt/sources.list
badaveil@ubuntu:~$ sudo apt-get update
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/restricted Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main Packages                           
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main Sources                            
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy-updates/multiverse Sources
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Fetched 308B in 7s (39B/s)                                                     
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5227BEBD68436DDF
W: You may want to run apt-get update to correct these problems
badaveil@ubuntu:~$ sudo apt-get install qgis
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgdal1-1.4.0 libgeos-c1 libgeos2c2a libhdf4g libhdf5-serial-1.6.5-0 libnetcdf4 libogdi3.2 libqgis1 proj qgis-common
Suggested packages:
  libhdf4g-doc libhdf4g-dev hdf4-tools ogdi-bin proj-ps-doc gpsbabel
Recommended packages:
  python-qgis qgis-plugin-grass
The following NEW packages will be installed:
  libgdal1-1.4.0 libgeos-c1 libgeos2c2a libhdf4g libhdf5-serial-1.6.5-0 libnetcdf4 libogdi3.2 libqgis1 proj qgis qgis-common
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.9MB of archives.
After this operation, 37.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libqgis1 qgis-common qgis
Install these packages without verification [y/N]? y
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libgeos2c2a 2.2.3-4 [381kB]                            
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main libqgis1 1.0.1-2~hardy1 [894kB]                                
Get:3 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libgeos-c1 2.2.3-4 [21.6kB]
Get:4 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libhdf4g 4.1r4-21 [284kB]
Get:5 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libhdf5-serial-1.6.5-0 1.6.5-5.2build1 [654kB]                                  
Get:6 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libnetcdf4 1:3.6.2-2 [212kB]                                                    
Get:7 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe proj 4.6.0-1 [406kB]                                                            
Get:8 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libogdi3.2 3.2.0~beta1-3ubuntu1 [236kB]                                         
Get:9 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe libgdal1-1.4.0 1.4.4-1ubuntu3 [2059kB]                                          
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main qgis-common 1.0.1-2~hardy1 [4678kB]                                                    
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main qgis 1.0.1-2~hardy1 [2078kB]                                                           
Fetched 11.9MB in 9min4s (21.9kB/s)                                                                                               
Selecting previously deselected package libgeos2c2a.
(Reading database ... 274832 files and directories currently installed.)
Unpacking libgeos2c2a (from .../libgeos2c2a_2.2.3-4_i386.deb) ...
Selecting previously deselected package libgeos-c1.
Unpacking libgeos-c1 (from .../libgeos-c1_2.2.3-4_i386.deb) ...
Selecting previously deselected package libhdf4g.
Unpacking libhdf4g (from .../libhdf4g_4.1r4-21_i386.deb) ...
Selecting previously deselected package libhdf5-serial-1.6.5-0.
Unpacking libhdf5-serial-1.6.5-0 (from .../libhdf5-serial-1.6.5-0_1.6.5-5.2build1_i386.deb) ...
Selecting previously deselected package libnetcdf4.
Unpacking libnetcdf4 (from .../libnetcdf4_1%3a3.6.2-2_i386.deb) ...
Selecting previously deselected package proj.
Unpacking proj (from .../archives/proj_4.6.0-1_i386.deb) ...
Selecting previously deselected package libogdi3.2.
Unpacking libogdi3.2 (from .../libogdi3.2_3.2.0~beta1-3ubuntu1_i386.deb) ...
Selecting previously deselected package libgdal1-1.4.0.
Unpacking libgdal1-1.4.0 (from .../libgdal1-1.4.0_1.4.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package libqgis1.
Unpacking libqgis1 (from .../libqgis1_1.0.1-2~hardy1_i386.deb) ...
Selecting previously deselected package qgis-common.
Unpacking qgis-common (from .../qgis-common_1.0.1-2~hardy1_all.deb) ...
Selecting previously deselected package qgis.
Unpacking qgis (from .../qgis_1.0.1-2~hardy1_i386.deb) ...
Setting up libgeos2c2a (2.2.3-4) ...

Setting up libgeos-c1 (2.2.3-4) ...

Setting up libhdf4g (4.1r4-21) ...

Setting up libhdf5-serial-1.6.5-0 (1.6.5-5.2build1) ...
Setting up libnetcdf4 (1:3.6.2-2) ...

Setting up proj (4.6.0-1) ...

Setting up libogdi3.2 (3.2.0~beta1-3ubuntu1) ...

Setting up libgdal1-1.4.0 (1.4.4-1ubuntu3) ...

Setting up libqgis1 (1.0.1-2~hardy1) ...

Setting up qgis-common (1.0.1-2~hardy1) ...
Setting up qgis (1.0.1-2~hardy1) ...
* Error in type 'application/x-qgis-project'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-qgis-layer-settings'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-esri-shape'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-esri-crs'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'image/tiff'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'image/jpeg'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'image/jp2'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-raster-aig'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-raster-ecw'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-raster-mrsid'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.

* Error in type 'application/x-mapinfo-mif'
*   (in /usr/share/mime/packages/qgis.xml):
*   Unknown freedesktop.org field 'icon'.


Processing triggers for libc6 ...
ldconfig deferred processing now taking place
badaveil@ubuntu:~$ qgis

---

