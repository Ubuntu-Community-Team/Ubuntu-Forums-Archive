---
title: "apt-get and synaptic doesn't work"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by geraldvillorente on 2009-05-07
Good day Guru's and Master's,

I recently installed Ubuntu Jaunty and I love it's new performance. However, I have a problem in apt-get and synaptic, they are both not working.

Here is the error

> 
]root@wizardsides:/#apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 15 not upgraded.
Need to get 4162kB/6270kB of archives.
After this operation, 21.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/main g++-4.3 4.3.3-5ubuntu4
  Connection failed [IP: 91.189.88.46 80]
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.3-5ubuntu4_i386.deb](http://ph.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.3-5ubuntu4_i386.deb)  Connection failed [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Here's my source.list

> 
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##  deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
##  deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
##  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
##  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse


Tnx,

Gerald

---

### Post by geraldvillorente on 2009-05-07
Im using DHCP ip address and no proxy

---

### Post by dubhear on 2009-05-07
seems to me like proxy problem. just wondering...> 
Im using DHCP ip address and no proxy

[http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com)

do you have that adress in deps? i'm not sure, but i'd try to put that adress in deps...

---

### Post by geraldvillorente on 2009-05-07
I believe that the problem is not on IP because Im the only one who uses internet connection. I'm using 3COM router...
I can browse the internet but can't use apt-get and synaptic

Please advice me...

---

### Post by HyRax on 2009-05-07
The mirror server you are connecting to to download new software from is not responding. Try another source. Change it in System->Administration->Software Sources.

---

### Post by geraldvillorente on 2009-05-07
still the same sir...still have a problem

---

### Post by HyRax on 2009-05-07
> **geraldvillorente said:**
> still the same sir...still have a problem

Who did you try to connect to?

---

### Post by geraldvillorente on 2009-05-07
I tried the Main Server and other mirrors but it says:

"Package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

---

### Post by HyRax on 2009-05-07
> **geraldvillorente said:**
> I tried the Main Server and other mirrors but it says:

"Package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

You've changed your sources, so can you post up your current /etc/apt/sources.list file for us to have a look?

Unless you've got a seriously bad Internet connection that is timing out on you, the official mirrors have everything you need to install "build-essential".

---

### Post by geraldvillorente on 2009-05-07
Here's my new source.list Sir...I'm using Main Server now...
> 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##  deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
##  deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
##  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
##  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse


Here's the error if I'm trying to install vim editor...
> 
root@wizardsides:~# apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vim-runtime
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim vim-runtime
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 6662kB of archives.
After this operation, 26.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  vim-runtime vim
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main vim-runtime 2:7.2.079-1ubuntu5
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main vim 2:7.2.079-1ubuntu5
  Connection failed [IP: 91.189.88.140 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb)  Connection failed [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb)  Connection failed [IP: 91.189.88.140 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by HyRax on 2009-05-07
I just tried to install "build-essential" from archive.ubuntu.com within a virtual machine here where I am, and it worked fine.

The culprit is a bad Internet connection on your end.

Try pinging "archive.,ubuntu.com" and see what response rate you get, ie:

```

$ ping -c4 archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=1 ttl=46 time=318 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=2 ttl=46 time=322 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=3 ttl=46 time=320 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=4 ttl=46 time=320 ms
$

```

You'll get a different server everytime since it's using round-robin DNS, but your speeds shouldn't be much worse than my 300 or so milliseconds.

---

### Post by colau on 2009-05-07
Copy and paste this in /etc/apt/sources.list and have a try again.
[html]
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb http://bd.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://bd.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted
[/html]

aptitude update
aptitude install vim

---

### Post by HyRax on 2009-05-07
That won't fix anything - his issue is that the server doesn't respond for him, and he's installing build-essential - you haven't got any of the deb-src lines in that sources.list which means installation of build-essential will FAIL.

DO NOT REPLACE YOUR SOURCES.LIST WITH THE ABOVE!

---

### Post by geraldvillorente on 2009-05-07
@HyRax, 
> 
root@wizardsides:~# ping -c4 archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=1 ttl=49 time=391 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=2 ttl=49 time=395 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=3 ttl=49 time=395 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=4 ttl=49 time=401 ms


@colau, Here's the error after I used the code you've given...
> 
root@wizardsides:~# apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vim-runtime
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim vim-runtime
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 6662kB of archives.
After this operation, 26.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  vim-runtime vim
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main vim-runtime 2:7.2.079-1ubuntu5
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main vim 2:7.2.079-1ubuntu5
  Connection failed [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb)  Connection failed [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by geraldvillorente on 2009-05-07
Oh sorry I just replaced sir....how to get back my original source.list? I have no backup...huhuhu

---

### Post by HyRax on 2009-05-07
Well, your speed is not much worse than mine, but you still cannot connect to download.

I can only assume then that something on your connection is either redirecting your port 80 traffic or your ISP is not allowing you to get to the mirror servers.

Make sure you haven't got any proxy enabled and maybe fire up a LiveCD and see if you can install something within the Live environment. If you CAN, then you've enabled or blocked something in your actual install.

EDIT: Just copy & paste the original sources.list you posted up at tht start of this thread.

---

### Post by geraldvillorente on 2009-05-07
Tnx Sir...I'll try to dig dipper...I'll try your suggestion now

---

### Post by geraldvillorente on 2009-05-07
Just wondering why I cant access the address colored below:

> 
root@wizardsides:~# apt-get update
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty Release.gpg
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/main Translation-en_PH
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/multiverse Translation-en_PH
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_PH
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release              
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages        
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Get:1 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Packages [4757kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Packages                                                                                                   
Get:2 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Sources [2375kB]                                                                                         
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Sources                                                                                                    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/multiverse Packages                                                                                                 
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/multiverse Sources                                                                                                  
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/main Packages                                                                                               
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/restricted Packages                                                                                         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/main Sources                                                                                                
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/restricted Sources                                                                                          
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/universe Packages                                                                                           
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/universe Sources                                                                                            
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/multiverse Packages                                                                                         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty-updates/multiverse Sources                                                                                          
Get:3 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Packages [6180kB]                                                                                        
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Packages                                                                                                   
Get:4 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Sources [3042kB]                                                                                         
18% [Working]                                                                                                                              6264B/s 35min 25s
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Sources                                                                                                    
  Sub-process gzip returned an error code (1)
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) jaunty/universe Packages                                                                                                   
  [COLOR="DarkSlateBlue"]404 Not Found [IP: 91.189.88.140 80][/COLOR]
Fetched 1950kB in 10min 59s (2956B/s)                                                                                                                       
W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.gz](http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages) [COLOR="DarkSlateBlue"]404 Not Found [IP: 91.189.88.140 80][/COLOR]

E: Some index files failed to download, they have been ignored, or old ones used instead.


But if I ping it...it send me a reply...
> 
root@wizardsides:~# ping 91.189.88.140
PING 91.189.88.140 (91.189.88.140) 56(84) bytes of data.
64 bytes from 91.189.88.140: icmp_seq=1 ttl=49 time=387 ms
64 bytes from 91.189.88.140: icmp_seq=2 ttl=49 time=379 ms
64 bytes from 91.189.88.140: icmp_seq=3 ttl=49 time=387 ms
64 bytes from 91.189.88.140: icmp_seq=4 ttl=49 time=400 ms
64 bytes from 91.189.88.140: icmp_seq=5 ttl=49 time=379 ms
64 bytes from 91.189.88.140: icmp_seq=6 ttl=49 time=385 ms
64 bytes from 91.189.88.140: icmp_seq=7 ttl=49 time=403 ms


---

### Post by HyRax on 2009-05-07
Well that 404 error is a bit more promising - it says that you actually GOT to that server, but in this instance the file you were looking for is not found.

Clearly the ph mirror is not up to date, so you need to try another mirror.

It may be slower for you, but go to System->Administration->Software Sources, choose "Other Server", expand out "Australia" and choose "mirror.internode.on.net" - it's one of the most complete 3rd party Ubuntu mirrors in this country.

Basically I just want to see if you can at the very least complete the install of what you want and then you can look at why your local mirror isn't giving you what you want, or why your Internet connection is playing up afterwards.

---

### Post by geraldvillorente on 2009-05-08
I tried "mirror.internode.on.net" but still the same:
Here's the output...
> 
root@wizardsides:~# apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vim-runtime
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim vim-runtime
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Need to get 6662kB of archives.
After this operation, 26.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) jaunty/main vim-runtime 2:7.2.079-1ubuntu5
  Connection failed
Err [http://mirror.internode.on.net](http://mirror.internode.on.net) jaunty/main vim 2:7.2.079-1ubuntu5
  Connection failed
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/main/v/vim/vim-runtime_7.2.079-1ubuntu5_all.deb)  Connection failed
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


---

### Post by HyRax on 2009-05-08
Wow, man - all I can say it that you have a strange internet connection to be able to ping, browse but not retrieve.

Seriously, boot up on a LiveCD and see if downloading packages behaves in the same way.

---

### Post by geraldvillorente on 2009-05-08
Ok Sir..tnx for your patience...I have to boot on LiveCD now and follow your instructions.

---

### Post by geraldvillorente on 2009-05-08
> 
Wow, man - all I can say it that you have a strange internet connection to be able to ping, browse but not retrieve.

Seriously, boot up on a LiveCD and see if downloading packages behaves in the same way. 


still the same sir..."connection failed"

---

### Post by HyRax on 2009-05-08
Go find someone else's Internet connection and try it again. If it works, then it's neither you or your PC - it's your router/modem or ISP who's blocking your access.

---

### Post by geraldvillorente on 2009-05-08
Problem solved Sir...the problem is on the router...Tnx alot

---

### Post by dubhear on 2009-05-08
Could you please, tell how you finally fixed the problem, be specific if you want, cause that would help others with their router problems too

Just a suggestion

Wondering why I can't mark threads solved any more?!?
It's seems like there is no such thing any more...

---

### Post by geraldvillorente on 2009-05-08
> 
Could you please, tell how you finally fixed the problem, be specific if you want, cause that would help others with their router problems too


I just reset the "content filter" in the router...and created my new policy for web filtering...

---

