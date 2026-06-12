---
title: "Update Manager &quot;W: Failed to fetch...&quot;"
date: 2008-08-29
forum: General Help
---

### Post by MarcosDurrant on 2008-08-29
When I try to update my system through the update manager and I hit the "check now" button it sits there for a couple minutes and then it spits out the following error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas as to what is happening?  This has occured he past fews days for me and it happens on my laptop and on the desktop...

---

### Post by tamoneya on 2008-08-30
for some reason your computer is getting the wrong IP address.  You could try switching you server though.  Go system -> administration -> software sources and select a new mirror.

---

### Post by bapoumba on 2008-08-30
To the OP: do you have a proxy setup somewhere ?

---

### Post by MarcosDurrant on 2008-08-30
I have tried a number of the different servers from synaptic...it still gives me the same error.

---

### Post by tamoneya on 2008-08-30
does it always give the same IP address as well?  In case you dont know the IP address is 198.167.2.100 in the first error.  Are you having any difficulties connecting to the internet?  What is the output of:```
ifconfig
```

---

### Post by MarcosDurrant on 2008-08-31
I hadn't had any problems with the internet until just barely and my WIFI just seemed really sluggish (and I am sitting right in front of the router...)  But I just plugged it in with an Ethernet cord and it seems to be working just fine - I am able to surf, download, use messenger, etc.  The strangest thing is that yesterday and this morning it was doing the same thing on both my laptop and desktop but the problem with the desktop was a repository that I had to add for cinelerra - so that is working now and it is just the laptop that is having issues...doing a sudo apt-get update helped me pinpoint the error on my desktop but when I do it on my laptop all I get is the following:

Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy Release.gpg                                
  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy/main Translation-en_US                     
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy/restricted Translation-en_US               
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy/multiverse Translation-en_US               
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy/universe Translation-en_US                 
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-updates Release.gpg                        
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-updates/main Translation-en_US             
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-updates/restricted Translation-en_US       
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-updates/multiverse Translation-en_US       
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-updates/universe Translation-en_US         
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-security Release.gpg                       
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-security/main Translation-en_US            
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-security/restricted Translation-en_US      
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-security/multiverse Translation-en_US      
  Unable to connect to 198.167.2.100 8080:
Err [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu) hardy-security/universe Translation-en_US        
  Unable to connect to 198.167.2.100 8080:
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
  Unable to connect to 198.167.2.100 8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out
Reading package lists... Done                   
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/Release.gpg](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/Release.gpg)  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/Release.gpg](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/Release.gpg)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to 198.167.2.100:8080 (198.167.2.100), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/Release.gpg](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/Release.gpg)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Failed to fetch [http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://ubuntu.cs.utah.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to 198.167.2.100 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

And the output of Ifconfig is the following:

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:0b:79:31  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe0b:7931/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2107006 (2.0 MB)  TX bytes:481678 (470.3 KB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67300 (65.7 KB)  TX bytes:67300 (65.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:e5:4b:29:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148707 (145.2 KB)  TX bytes:108647 (106.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-E5-4B-29-7F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I appreciate your help!

---

### Post by MarcosDurrant on 2008-08-31
And I have never setup a proxy.

---

### Post by tamoneya on 2008-08-31
okay stay connected to ethernet and run this:```
sudo ifconfig wlan0 down
sudo apt-get update
```

---

### Post by MarcosDurrant on 2008-09-01
It still gives me the same error as before...

---

### Post by bapoumba on 2008-09-01
> **MarcosDurrant said:**
> It still gives me the same error as before...
Please post your sources.list:
```
cat /etc/apt/sources.list
```
I get a 404 for these repos too.

---

### Post by MarcosDurrant on 2008-09-01
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy main restricted multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy universe
deb [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy-security main restricted multiverse
deb-src [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.cs.utah.edu/ubuntu/](http://ubuntu.cs.utah.edu/ubuntu/) hardy-security universe

---

### Post by MarcosDurrant on 2008-09-08
It seems like this problem happened after I had to play with my wireless while on campus.  I had to connect to a secured network where it needed a certificate to authenticate my login.  Is there anyway that somehow playing with my WIFI setting (albeit just for the WIFI secured network which I am logged on to right not) could have caused this IP address issue?

---

### Post by mb_webguy on 2008-09-08
Are you connected to the campus network right now?

---

### Post by MarcosDurrant on 2008-09-08
Yes

---

### Post by MarcosDurrant on 2008-09-08
And when I try and update I get the same error that I was getting from home.

---

### Post by wanderson on 2009-09-12
Hello!
Sorry, but I'm bumping this message because I have the same error now. On work, my notebook is connected with a proxy server on Synaptic. When I came to my house, the apt wasn't responding, even when I changed the proxy.
I checked the file 'environment' inside the /etc directory and I erased the line with the http_proxy configuration.
All works fine now.
Thanks =)

---

### Post by bapoumba on 2009-09-12
> **wanderson said:**
> Hello!
Sorry, but I'm bumping this message because I have the same error now. On work, my notebook is connected with a proxy server on Synaptic. When I came to my house, the apt wasn't responding, even when I changed the proxy.
I checked the file 'environment' inside the /etc directory and I erased the line with the http_proxy configuration.
All works fine now.
Thanks =)
W00t :)
This is an older thread, but it can always be helpful.

---

