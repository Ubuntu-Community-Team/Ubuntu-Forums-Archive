---
title: "Help with sudo apt-get command"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by ninja123 on 2009-03-04
Hi I cannot install any libraries from synaptic Packet manager.

I am going via proxy to the internet however it doesnt work.


Also I get following error for any library i try to install via sudo apt-get command.

I do not have any apt.conf file. however there is a sources.list. Should I make any changes there??


 sudo aptitude update
[PHP]
Writing extended state information... Done
Err http://security.ubuntu.com intrepid-security Release.gpg                                              
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com intrepid-security/main Translation-en_US                                   
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US                             
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_US                               
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_US                             
  Unable to connect to security.ubuntu.com http:
Err http://de.archive.ubuntu.com intrepid Release.gpg                                                     
  Could not connect to de.archive.ubuntu.com:80 (141.76.2.130), connection timed out [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid/main Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid/restricted Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid/universe Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid/multiverse Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid-updates Release.gpg
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid-updates/main Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid-updates/universe Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
  Unable to connect to de.archive.ubuntu.com http: [IP: 141.76.2.130 80]
Reading package lists... Done [/PHP]

Do help me.

I have this easy peasy in my Eee PC 1000 installed and I am very new to Ubuntu

---

### Post by stumbleUpon on 2009-03-04
You seem to be having network problems.

Are you able to connect to the internet using your proxy. If yes, then check if you have set the same proxy to be used in synaptic.

System > Administration > Synaptic : your password : > Settings > Preferences > Network -- change the proxy to what you are using to access the internet.

---

### Post by ninja123 on 2009-03-04
Yes there must be a network problem. but i dont know how to resolve.I have given exactly the same setting in synaptic manager as i have given in my browser. But i can very well access the internet..

How do i solve this??

---

### Post by stumbleUpon on 2009-03-04
Is your proxy the same as the output of

more /etc/apt/apt.conf

Have you set your GNOME proxy properly in System > Preferences > Network Proxy...?

---

### Post by ninja123 on 2009-03-04
The file /etc/apt/apt-conf doesnt exist in my computer.

there is an apt.confd folder though

---

### Post by Bachstelze on 2009-03-04
try this

```
export http_proxy="http://username:password@proxy.domain.org:port"
sudo apt-get update
```

---

### Post by ninja123 on 2009-03-04
Many thanks to you!!

Yes, now i changed network proxy settings as u told and now atleast the sudo get command works :)

The synaptic manager doesnt though...

---

### Post by ninja123 on 2009-03-05
Yes i checked the apt.conf and it is set to the same proxy.

Well i think i can access the internet via sudo as i am able to do the sudo apt-get update command and all.

what i cant is:

the synaptic manager shows only installed packets... if i type valid libraries like lipcap, liblame,g++ or anything it simply gives me no search results or shows those already installed. i cant search n download any non-existing libraries..


PLease help

---

### Post by stumbleUpon on 2009-03-05
Put these lines in your .bashrc file

```
export http_proxy="http://username:password@proxy.domain.org:port"
export ftp_proxy="http://username:password@proxy.domain.org:port"
```

then do 

```
source .bashrc
```

this should set the proxy for all your sessions

---

