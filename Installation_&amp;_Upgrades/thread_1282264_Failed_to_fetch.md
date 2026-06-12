---
title: "Failed to fetch"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Colaborator on 2009-10-04
I am beginner in Ubuntu. I have the problen when i try install software witch comand apt-get install or with update manager. I try the commnand apt-get update, but the screen display this output:
```
Err http://repository.akirad.net akirad-jaunty Release.gpg                     
  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out
Err http://repository.akirad.net akirad-jaunty/main Translation-en_US          
  Unable to connect to 81.180.75.129 6565:
Err http://akirad.cinelerra.org akirad-jaunty Release.gpg                      
  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out
Err http://akirad.cinelerra.org akirad-jaunty/main Translation-en_US           
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty Release.gpg                               
  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out
Err http://archive.ubuntu.com jaunty/main Translation-en_US                    
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty/restricted Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty/universe Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty/multiverse Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-updates Release.gpg
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-updates/main Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-security Release.gpg
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-security/main Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-security/universe Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Err http://akirad.hfbk.net akirad-jaunty Release.gpg
  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out
Err http://akirad.hfbk.net akirad-jaunty/main Translation-en_US
  Unable to connect to 81.180.75.129 6565:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://repository.akirad.net/dists/akirad-jaunty/Release.gpg  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out

W: Failed to fetch http://repository.akirad.net/dists/akirad-jaunty/main/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://akirad.cinelerra.org/dists/akirad-jaunty/Release.gpg  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out

W: Failed to fetch http://akirad.cinelerra.org/dists/akirad-jaunty/main/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Failed to fetch http://akirad.hfbk.net/dists/akirad-jaunty/Release.gpg  Could not connect to 81.180.75.129:6565 (81.180.75.129), connection timed out

W: Failed to fetch http://akirad.hfbk.net/dists/akirad-jaunty/main/i18n/Translation-en_US.bz2  Unable to connect to 81.180.75.129 6565:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```.
 I try change the file /etc/apt/sources.list from other computer. I don't know what do for resolve this problem. Please help me?

---

### Post by Partyboi2 on 2009-10-04
Hi, open Software Sources (System>Admin>Software Sources) and under the 1st tab try changing your download server to another one.

---

### Post by Colaborator on 2009-10-04
> **Partyboi2 said:**
> Hi, open Software Sources (System>Admin>Software Sources) and under the 1st tab try changing your download server to another one.
I click on the Select Best Server and i see the message **no suitable server was found. Check your internet connection**. I have the Internet connection. When i try to change the download server. The download server is other. In the error message after the name of the new server is write**:Unable to connect to 81.180.75.129 6565:**. I try replase the file /etc/apt/sources.files with the context from other computer and version 8.10(I have the 9.04 version). Maybe this is server for authentification. But i don't know how corect replace this server.

---

### Post by Partyboi2 on 2009-10-04
> I try replase the file /etc/apt/sources.files with the context from other computer and version 8.10(I have the 9.04 version).Can you open a terminal (Applications>Accessories>Terminal) and post your sources.list with
```
cat /etc/apt/sources.list
```Just want to maker sure your sources.list is ok.
Also can you try pinging google to see what happens.
```
ping -c 4 google.com
```

Edit: Forgot to ask, are you using a proxy to connect?

---

### Post by Colaborator on 2009-10-04
```
cat /etc/apt/sources.list
```
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# newer versions of the distribution.



deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted

deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted



## Major bug fix updates produced after the final release of the

## distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team. Also, please note that software in universe WILL NOT receive any

## review or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu/ jaunty universe

deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe

deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse

deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse

deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb http://md.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

# deb-src http://md.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse



## Uncomment the following two lines to add software from Canonical's

## 'partner' repository. This software is not part of Ubuntu, but is

## offered by Canonical and the respective vendors as a service to Ubuntu

## users.

# deb http://archive.canonical.com/ubuntu intrepid partner

# deb-src http://archive.canonical.com/ubuntu intrepid partner



deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted

deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe

deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe

deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse



# deb http://apt.last.fm/ debian stable # disabled on upgrade to jaunty



#Mono 2.0 Packages for Ubuntu Intrepid

# deb http://ppa.launchpad.net/firerabbit/ubuntu jaunty main # disabled on upgrade to jaunty

# deb-src http://ppa.launchpad.net/firerabbit/ubuntu jaunty main # disabled on upgrade to jaunty
```Also can you try pinging google to see what happens.
```
ping -c 4 google.com
```Edit: Forgot to ask, are you using a proxy to connect?[/quote]
PING google.com (74.125.127.100) 56(84) bytes of data.
64 bytes from pz-in-f100.google.com (74.125.127.100): icmp_seq=1 ttl=42 time=242 ms
64 bytes from pz-in-f100.google.com (74.125.127.100): icmp_seq=2 ttl=42 time=232 ms
64 bytes from pz-in-f100.google.com (74.125.127.100): icmp_seq=3 ttl=42 time=219 ms
64 bytes from pz-in-f100.google.com (74.125.127.100): icmp_seq=4 ttl=42 time=236 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms

No, I don't use the proxy.

---

