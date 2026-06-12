---
title: "Problem installing nvidia drivers on asus w7j (geforce go 7400/ubuntu edgy)"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by angelofhope on 2007-02-01
Hi, I tried installing the nvidia driver several different ways, using envy, following the description on [http://home.comcast.net/~andrex/Debian-nVidia/installation.html](http://home.comcast.net/~andrex/Debian-nVidia/installation.html), but I seem to get the same error:

```
 sudo modprobe nvidia
FATAL: Error running install command for nvidia
```

someone who can help me here?

---

### Post by Lfrb on 2007-02-05
You just have to add this line to your "/etc/apt/sources.list" file :

```
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```
and then :
```

sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
Restart your X server with Ctrl+Alt+Backspace. I have the same laptop so I guess you don't have the right resolution. You can add it in your "/etc/X11/xorg.conf" file. Search for this section :

```

	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```
And add "1280x800" before "1024x768".
If you need more help to configure your hardware just tell me.

--
Louis-Francis

---

### Post by angelofhope on 2007-02-08
What I did:
```
$ sudo gedit /etc/apt/sources.list
Password:

```
Then I added the line you said:
```
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```

after doing
```
sudo apt-get update[code]
I get:
[CODE]Get:1 http://be.archive.ubuntu.com edgy Release.gpg [191B]
Err http://be.archive.ubuntu.com edgy Release.gpg                              
  Error reading from server - read (104 Connection reset by peer)
Hit ftp://ftp.belnet.be edgy Release.gpg                                       
Ign http://be.archive.ubuntu.com edgy/main Translation-en_US                   
Get:2 ftp://ftp.belnet.be edgy/main Translation-en_US                          
Ign ftp://ftp.belnet.be edgy/main Translation-en_US                            
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://be.archive.ubuntu.com edgy/restricted Translation-en_US             
Ign http://ntfs-3g.sitesweetsite.info edgy Release.gpg                         
Get:4 ftp://ftp.belnet.be edgy/universe Translation-en_US                      
Ign ftp://ftp.belnet.be edgy/universe Translation-en_US                        
Get:5 ftp://ftp.belnet.be edgy/multiverse Translation-en_US                    
Ign ftp://ftp.belnet.be edgy/multiverse Translation-en_US                      
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Get:6 ftp://ftp.belnet.be edgy/restricted Translation-en_US                    
Get:7 http://be.archive.ubuntu.com edgy-updates Release.gpg [191B]             
Ign http://ntfs-3g.sitesweetsite.info edgy/main Translation-en_US              
Ign http://be.archive.ubuntu.com edgy-updates/main Translation-en_US           
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://download.skype.com stable Release.gpg                               
Ign ftp://ftp.belnet.be edgy/restricted Translation-en_US                      
Ign http://be.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
Get:8 ftp://ftp.belnet.be edgy-security Release.gpg [191B]                     
Ign http://ntfs-3g.sitesweetsite.info edgy/main-all Translation-en_US          
Get:9 http://security.ubuntu.com edgy-security Release [50.9kB]                
Get:10 http://be.archive.ubuntu.com edgy Release [34.7kB]                      
Get:11 ftp://ftp.belnet.be edgy-security/main Translation-en_US                
Ign http://ntfs-3g.sitesweetsite.info edgy Release                             
Ign ftp://ftp.belnet.be edgy-security/main Translation-en_US                   
Ign http://wine.sourceforge.net binary/ Release.gpg                            
Ign http://download.skype.com stable/non-free Translation-en_US                
Get:12 http://be.archive.ubuntu.com edgy-updates Release [38.4kB]              
Get:13 ftp://ftp.belnet.be edgy-security/universe Translation-en_US            
Ign http://ntfs-3g.sitesweetsite.info edgy/main Packages                       
Ign ftp://ftp.belnet.be edgy-security/universe Translation-en_US               
Get:14 ftp://ftp.belnet.be edgy-security/multiverse Translation-en_US          
Ign http://security.ubuntu.com edgy-security Release                           
Ign http://be.archive.ubuntu.com edgy-updates Release                          
Ign ftp://ftp.belnet.be edgy-security/multiverse Translation-en_US             
Hit http://be.archive.ubuntu.com edgy/main Packages                            
Get:15 ftp://ftp.belnet.be edgy-security/restricted Translation-en_US          
Ign http://ntfs-3g.sitesweetsite.info edgy/main-all Packages                   
Ign ftp://ftp.belnet.be edgy-security/restricted Translation-en_US             
Get:16 ftp://ftp.belnet.be edgy-updates Release.gpg [191B]                     
Get:17 http://security.ubuntu.com edgy-security/main Packages [58.6kB]         
Ign http://be.archive.ubuntu.com edgy/restricted Packages                      
Ign http://download.skype.com stable Release                                   
Hit http://ntfs-3g.sitesweetsite.info edgy/main Packages                       
Hit http://be.archive.ubuntu.com edgy/main Sources                             
Get:18 ftp://ftp.belnet.be edgy-updates/multiverse Translation-en_US           
Ign http://www.albertomilone.com binary/ Release.gpg                           
Ign ftp://ftp.belnet.be edgy-updates/multiverse Translation-en_US              
Get:19 ftp://ftp.belnet.be edgy-updates/main Translation-en_US                 
Ign ftp://ftp.belnet.be edgy-updates/main Translation-en_US                    
Get:20 http://security.ubuntu.com edgy-security/restricted Packages [3529B]    
Get:21 ftp://ftp.belnet.be edgy-updates/restricted Translation-en_US           
Get:22 http://be.archive.ubuntu.com edgy/restricted Sources [1436B]            
Ign http://be.archive.ubuntu.com edgy/restricted Sources                       
Hit http://ntfs-3g.sitesweetsite.info edgy/main-all Packages                   
Ign ftp://ftp.belnet.be edgy-updates/restricted Translation-en_US              
Get:23 ftp://ftp.belnet.be edgy-updates/universe Translation-en_US             
Ign ftp://ftp.belnet.be edgy-updates/universe Translation-en_US                
Get:24 http://be.archive.ubuntu.com edgy-updates/main Packages [62.6kB]        
Get:25 ftp://ftp.belnet.be edgy Release [34.7kB]                               
Get:26 http://security.ubuntu.com edgy-security/main Sources [11.7kB]          
Ign http://download.skype.com stable/non-free Packages                         
Get:27 http://be.archive.ubuntu.com edgy-updates/restricted Packages [14B]     
Ign http://www.albertomilone.com binary/ Translation-en_US                     
Ign http://be.archive.ubuntu.com edgy-updates/restricted Packages              
Get:28 http://security.ubuntu.com edgy-security/restricted Sources [940B]      
Get:29 ftp://ftp.belnet.be edgy-security Release [50.9kB]                      
Get:30 http://be.archive.ubuntu.com edgy-updates/main Sources [18.9kB]         
Get:31 ftp://ftp.belnet.be edgy-updates Release [38.4kB]                       
Get:32 http://be.archive.ubuntu.com edgy-updates/restricted Sources [14B]      
Hit http://download.skype.com stable/non-free Packages                         
Get:33 http://be.archive.ubuntu.com edgy/restricted Packages [6132B]           
Hit ftp://ftp.belnet.be edgy/main Packages                                     
99% [33 Packages gzip 0] [Waiting for headers] [Waiting for headers] [Query] [W
gzip: stdin: not in gzip format
Err http://be.archive.ubuntu.com edgy/restricted Packages                      
  Sub-process gzip returned an error code (1)
Err http://be.archive.ubuntu.com edgy/restricted Sources                       
  416 Requested Range Not Satisfiable
Hit ftp://ftp.belnet.be edgy/universe Packages                                 
Ign http://www.albertomilone.com binary/ Release                               
Hit ftp://ftp.belnet.be edgy/multiverse Packages                     
Get:34 http://be.archive.ubuntu.com edgy-updates/restricted Packages [20B]
Hit ftp://ftp.belnet.be edgy/restricted Packages                              
Get:35 ftp://ftp.belnet.be edgy-security/main Packages [58.6kB]
Get:36 ftp://ftp.belnet.be edgy-security/universe Packages [32.0kB]          
Ign http://www.albertomilone.com binary/ Packages                              
Get:37 ftp://ftp.belnet.be edgy-security/multiverse Packages [3572B]     
Get:38 ftp://ftp.belnet.be edgy-security/restricted Packages [3529B]         
Get:39 ftp://ftp.belnet.be edgy-updates/multiverse Packages [14B]       
Get:40 http://www.albertomilone.com binary/ Packages [3294B]          
Get:41 ftp://ftp.belnet.be edgy-updates/main Packages [62.6kB]               
Get:42 ftp://ftp.belnet.be edgy-updates/restricted Packages [14B]
Get:43 ftp://ftp.belnet.be edgy-updates/universe Packages [10.7kB]
Ign http://wine.sourceforge.net binary/ Translation-en_US
Hit http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Hit http://wine.sourceforge.net binary/ Packages                               
Fetched 579kB in 8s (71.7kB/s)                                                 
Failed to fetch http://be.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://be.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://be.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  416 Requested Range Not Satisfiable
Reading package lists... Done
W: GPG error: http://security.ubuntu.com edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://be.archive.ubuntu.com edgy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
I don't really know what this all means, but I don't see an error with the given site (I might be missing it)

So after that I did sudo apt-get install nvidia-glx and got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-common-dev libglu1-mesa-dev libgl1-mesa-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.17-10-386 linux-restricted-modules-2.6.17-10-386
Suggested packages:
  linux-doc-2.6.17 linux-source-2.6.17 avm-fritz-firmware-2.6.17-10
The following NEW packages will be installed:
  linux-image-2.6.17-10-386 linux-restricted-modules-2.6.17-10-386
The following packages will be upgraded:
  nvidia-glx
1 upgraded, 2 newly installed, 0 to remove and 21 not upgraded.
Need to get 13.5MB/36.3MB of archives.
After unpacking 91.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  linux-restricted-modules-2.6.17-10-386 nvidia-glx
Install these packages without verification [y/N]? Y
Get:1 http://www.albertomilone.com binary/ linux-restricted-modules-2.6.17-10-386 2.6.17.9-1 [8655kB]
Get:2 http://www.albertomilone.com binary/ nvidia-glx 1.0.9746+2.6.17.9-1 [4822kB]
Fetched 8655kB in 38s (223kB/s)                                                
Failed to fetch http://www.albertomilone.com/drivers/edgy/latest/32bit/binary/nvidia-glx_1.0.9746+2.6.17.9-1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I guess there might be a problem here?

If I ignore this and try the sudo nvidia-xconfig and restart X it doesn't start and gives me the option to see the log (don't know how to save this, but it seemt to be the same thing as before)

Any ideas?
TIA

---

### Post by Lfrb on 2007-02-12
Maybe there is a problem with the repository. You can try again in a few days. Alberto Milone doesn't seem to have enough time to update his repository : [http://albertomilone.com/wordpress/?p=61](http://albertomilone.com/wordpress/?p=61) :-(

You can also try this other repository ([http://nvidia.limitless.lupine.me.uk/](http://nvidia.limitless.lupine.me.uk/))
You add this line to your /etc/apt/source.list file (after you removed the other line) :

```
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
```

And add the key (in a terminal) :

```
wget -O- --quiet http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg | sudo apt-key add -
```

Then :

```

sudo apt-get update
sudo apt-get install nvidia-glx
```

--
Louis-Francis

---

