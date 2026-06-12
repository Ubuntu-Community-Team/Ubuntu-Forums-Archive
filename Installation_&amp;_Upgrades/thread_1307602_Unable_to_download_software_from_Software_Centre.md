---
title: "Unable to download software from Software Centre"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by andypi on 2009-10-31
I've just installed 9.10, and I'm finding that I can't install any software with the Software Centre.

I'm behind a proxy, but believe I have configured it properly - I have specified both HTTP and FTP servers in Synaptic's network settings, and the Update Manager works fine. However, whenever I try and install software using Software Centre, it hangs at 5% before eventually telling me "Failed to download package files. Check your internet connection"

Anyone know what's going on here?

---

### Post by imail on 2009-11-02
Same here.
Tried to change it manually in the terminal but it didn't work either.

---

### Post by graham70 on 2009-11-05
I have the same problem this is what I have done so far 
1. Change the network settings in synaptic package manager for my proxy ( with login and passwords)
2. Add my proxy settings in system/proxy settings and applied system wide( with login and passwords)
3. Updated aptdaemon by terminal 
4. Run these commands in terminal 

export http_proxy=http://login:password@ip address:port/
export ftp_proxy=http://login:password@ip address:port/
export https_proxy=http://login:password@ip address:port/

(Why are there smiley faces on my p's)

this gave a different error of unauthorized software source ( thought I was on the right track for a wail but it went went back to proxy error again )

4 Remove password authorization from proxy server all good 

Not really now my proxy has no login. So I see the problem is in login and password area of software center and the deb installer ( same problem ) on to the proxy 

Any help on this will be great

---

### Post by graham70 on 2009-11-07
Gday again 
can anyone help me or direct me to a posting that has solved this problem 

thanks

---

### Post by appier on 2009-11-07
I have been running into the same problem.  The workaround for me has been to install everything either via Synaptic or through apt-get (or aptitiude) in the terminal.

First, set the proxy environment:

export http_proxy="username:password@yourdomain.org:port#"

Update apt-get:

sudo apt-get update

Then, install your package:

sudo apt-get install package-name

This is not the easy way to do it, but it works...

Mark

---

### Post by graham70 on 2009-11-10
Doing the same workaround thanks for the the reply. Also when install a deb file finding the dependencies by manually install them from the net. It sort of reminds me when I first tried Linux and gave up, gone too far now

---

### Post by Gumm on 2009-11-10
There is a bug report on Launchpad here:

[URL="https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/466142"]https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/466142
[/URL]
It seems that you can either edit some files by hand, or try a test package by Luke Symes from his personal ppa here:

[https://launchpad.net/~allsymes/+archive/ppa/]("https://launchpad.net/~allsymes/+archive/ppa/")

I have not tested either yet, but on Launchpad it seems that some users found joy.

EDIT: Can confirm, this works for me

---

### Post by graham70 on 2009-11-11
Gumm thanks for the reply will try soon and report back

---

