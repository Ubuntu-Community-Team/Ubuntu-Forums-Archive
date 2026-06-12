---
title: "Getting 'Sources List' error"
date: 2008-10-29
forum: General Help
---

### Post by DougieFresh4U on 2008-10-29
I have ran 'sudo apt-get update' 3 times as suggested, but still get the following. Any one know what this is and maybe a solution to it?
Thanks
[B]Reading package lists... Done
W: Bizarre Error - File size is not what the server reported 0 8032
W: You may want to run apt-get update to correct these problems
dougie@DougiesLeanMachine:~$[/B]

**EDIT: When I said that I ran 'update' 3 times, I actually ran 'sudo apt-get update' which most replies have been telling me to do - mis-communication **

---

### Post by mikewhatever on 2008-10-29
Try running <sudo apt-get update> as suggested by the 'second error'.

---

### Post by Motomo on 2008-10-29
Tried that and still getting an error after the update this am.

---

### Post by DougieFresh4U on 2008-10-29
> **DougieFresh4U said:**
> **I have ran 'update' 3** times as suggested, but still get the following. Any one know what this is and maybe a solution to it?
Thanks
[B]Reading package lists... Done
W: Bizarre Error - File size is not what the server reported 0 8032
W: You may want to run apt-get update to correct these problems
dougie@DougiesLeanMachine:~$[/B]

> **mikewhatever said:**
> Try running <sudo apt-get update> as suggested by the 'second error'.
:confused:

---

### Post by Nepherte on 2008-10-29
Did you try another mirror?

---

### Post by Zyphrexi on 2008-10-29
I got the same error message using update-manager, i'll update using terminal and post where exactly it freaks out.

EDIT: using sudo apt-get update produced no errors

I suggest unchecking or commenting out any 'extra' (not supported) 3rd party sources.

Just for completeness sake, open up a terminal, type **sudo apt-get update**

---

### Post by DougieFresh4U on 2008-10-29
> **Zyphrexi said:**
> 

Just for completeness sake, open up a terminal, type **sudo apt-get update**

That is what is giving me the error.

---

### Post by Zyphrexi on 2008-10-29
I just realized you're on intrepid, you should have posted this in the development forum, you'd probably get better help that way. (i'm running intrepid too btw)

try posting your sources.list and I'll test it against mine, since I had that error using update-manager, but doing it in the terminal reported no error.

I assume you know how to do that, but to be sure I'll write it out.

in a terminal type: **gedit /etc/apt/sources.list**
then copy and paste the contents here.
sudo here isn't needed since no modification of the file is being done.

here's mine (I didn't copy the commented out stuff ubuntu puts in the file) 
______________________________________________________________________
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) intrepid main universe
_________________________________________________________________________

---

### Post by brandoncolorado on 2008-10-29
Fixed on my machine (8.10) by unchecking the Medibuntu repository in Synaptic.

---

### Post by Zyphrexi on 2008-10-29
yeah medibuntu seems to periodically go down for whatever reason.

---

### Post by Mr.Auer on 2008-10-29
Seems I have the same problem as of today. Installed Intrepid amd64 Release Candidate couple days ago, tried to update just now.
This is what happens:

```
sudo apt-get update
Get:1 http://fi.archive.ubuntu.com intrepid Release.gpg [189B]
Ign http://fi.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://fi.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://fi.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://fi.archive.ubuntu.com intrepid-backports Release.gpg
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-backports/main Translation-en_US
Ign http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://fi.archive.ubuntu.com intrepid-proposed Release.gpg
Ign http://fi.archive.ubuntu.com intrepid-proposed/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-proposed/main Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US
Ign http://fi.archive.ubuntu.com intrepid-proposed/universe Translation-en_US
Get:2 http://fi.archive.ubuntu.com intrepid Release [65.9kB]
Hit http://fi.archive.ubuntu.com intrepid-updates Release
Hit http://fi.archive.ubuntu.com intrepid-backports Release
Hit http://fi.archive.ubuntu.com intrepid-proposed Release
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]
Hit http://archive.canonical.com intrepid Release
Err http://fi.archive.ubuntu.com intrepid Release

Hit http://fi.archive.ubuntu.com intrepid-updates/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://fi.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://fi.archive.ubuntu.com intrepid-updates/main Sources
Hit http://fi.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://fi.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://fi.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://fi.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://archive.canonical.com intrepid/partner Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.canonical.com intrepid/partner Sources
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://fi.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://fi.archive.ubuntu.com intrepid-backports/main Packages
Hit http://fi.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://fi.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://fi.archive.ubuntu.com intrepid-backports/multiverse Packages
Get:4 http://fi.archive.ubuntu.com intrepid-backports/main Sources [14B]
Get:5 http://fi.archive.ubuntu.com intrepid-backports/restricted Sources [14B]
Get:6 http://fi.archive.ubuntu.com intrepid-backports/universe Sources [14B]
Get:7 http://fi.archive.ubuntu.com intrepid-backports/multiverse Sources [14B]
Hit http://fi.archive.ubuntu.com intrepid-proposed/restricted Packages
Hit http://fi.archive.ubuntu.com intrepid-proposed/main Packages
Hit http://fi.archive.ubuntu.com intrepid-proposed/multiverse Packages
Hit http://fi.archive.ubuntu.com intrepid-proposed/universe Packages
Fetched 247B in 0s (501B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://fi.archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://fi.archive.ubuntu.com/ubuntu/...trepid/Release

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

---

### Post by Mr.Auer on 2008-10-29
"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

This sounds like its the Ubuntu repo key that mismatches? Am I in the woods here?

---

### Post by Motomo on 2008-10-29
sudo apt-get update gives the error that has listed above

I am running Hardy Heron

I began to occur after the system update today that laoded the new kernal and headers

After the restart it showed another update of three packages and that is when the error began

---

### Post by Mr.Auer on 2008-10-29
Ill quickly boot back to my Hardy install on this same box, and try updating that one. Ill edit this post as to tell what happens as soon as Im done. Brb.

Okies:
My Hardy install updates, Medibuntu seems to be ignored (I did have Medibuntu and its keyring installed on Intrepid too, Ill try removing Medibuntu keyring next to see what happens - I disabled the repo already thou) and some other entries are marked as Ignored as well? 
Dunno what is wrong here....

Hardy update:

```
sudo apt-get update
[sudo] password for usagi: 
Hit http://fi.archive.ubuntu.com hardy Release.gpg
Ign http://fi.archive.ubuntu.com hardy/main Translation-en_US
Ign http://fi.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://fi.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://fi.archive.ubuntu.com hardy/multiverse Translation-en_US            
Get:1 http://fi.archive.ubuntu.com hardy-updates Release.gpg [189B]            
Get:2 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Get:3 http://packages.medibuntu.org hardy Release.gpg [189B]                   
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://fi.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://fi.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://fi.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://fi.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://fi.archive.ubuntu.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Get:4 http://fi.archive.ubuntu.com hardy-updates Release [58.5kB]              
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Get:5 http://security.ubuntu.com hardy-security Release [58.5kB]               
Get:6 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://fi.archive.ubuntu.com hardy/main Packages                           
Hit http://fi.archive.ubuntu.com hardy/restricted Packages                     
Hit http://fi.archive.ubuntu.com hardy/main Sources                            
Hit http://fi.archive.ubuntu.com hardy/restricted Sources                      
Hit http://fi.archive.ubuntu.com hardy/universe Packages                       
Hit http://fi.archive.ubuntu.com hardy/universe Sources                        
Hit http://fi.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://fi.archive.ubuntu.com hardy/multiverse Sources                      
Ign http://ppa.launchpad.net hardy/main Sources                                
Get:7 http://fi.archive.ubuntu.com hardy-updates/main Packages [367kB]         
Hit http://ppa.launchpad.net hardy/main Packages                               
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://ppa.launchpad.net hardy/main Sources                                
Get:8 http://packages.medibuntu.org hardy Release [9335B]                      
Get:9 http://security.ubuntu.com hardy-security/main Packages [63.1kB]         
Get:10 http://fi.archive.ubuntu.com hardy-updates/restricted Packages [6740B]  
Get:11 http://fi.archive.ubuntu.com hardy-updates/main Sources [97.3kB]        
Get:12 http://fi.archive.ubuntu.com hardy-updates/restricted Sources [1092B]   
Get:13 http://fi.archive.ubuntu.com hardy-updates/universe Packages [130kB]    
Get:14 http://fi.archive.ubuntu.com hardy-updates/universe Sources [31.7kB]    
Get:15 http://fi.archive.ubuntu.com hardy-updates/multiverse Packages [23.0kB] 
Get:16 http://fi.archive.ubuntu.com hardy-updates/multiverse Sources [4020B]   
Get:17 http://security.ubuntu.com hardy-security/restricted Packages [6819B]   
Get:18 http://security.ubuntu.com hardy-security/main Sources [15.1kB]     
Get:19 http://security.ubuntu.com hardy-security/restricted Sources [1092B] 
Get:20 http://security.ubuntu.com hardy-security/universe Packages [40.4kB]
Get:21 http://packages.medibuntu.org hardy/free Packages [6333B]          
Get:22 http://security.ubuntu.com hardy-security/universe Sources [6773B]
Get:23 http://security.ubuntu.com hardy-security/multiverse Packages [8320B]   
Get:24 http://security.ubuntu.com hardy-security/multiverse Sources [14B]      
Get:25 http://packages.medibuntu.org hardy/non-free Packages [7814B]           
Fetched 944kB in 2s (424kB/s)                            
Reading package lists... Done
usagi@Opossumi:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30
The following packages will be upgraded:
  apt apt-utils cpp-4.2 g++-4.2 gcc-4.2 gcc-4.2-base gstreamer0.10-plugins-bad
  gstreamer0.10-tools gtk2-engines-pixbuf icedtea-gcjwebplugin lib32gcc1
  lib32stdc++6 libexif12 libffi4 libgcc1 libglib2.0-0 libgomp1
  libgstreamer0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common liblwres30
  libstdc++6 libstdc++6-4.2-dev linux-headers-2.6.24-21
  linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-libc-dev
  pciutils rhino thunderbird-locale-en-gb tzdata xkb-data
  xserver-xorg-video-intel
34 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 45.6MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Edit: Fixed it back then by removing the Ubuntu and Medibuntu keyrings (the deb package in the repos containing the repo GPG key), and reinstalling them after that.

---

