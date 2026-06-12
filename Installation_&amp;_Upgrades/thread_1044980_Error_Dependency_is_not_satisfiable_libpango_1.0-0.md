---
title: "Error: Dependency is not satisfiable: libpango 1.0-0"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by linuxmascot on 2009-01-20
Hello, 
     am new to linux. I want to install linuxdcpp on my ubuntu. Mine is a 64 bit amd processor, I downloaded the linuxdcpp amd64 deb. 
     But while installing am getting an error of this nature.

     error: dependency is not satisfiable: libpango 1.0-0 

     Kindly help me fix this problem!

---

### Post by wolfen69 on 2009-01-20
first, install [this]("http://packages.ubuntu.com/intrepid-updates/libpango1.0-common"). then [this]("http://packages.ubuntu.com/intrepid-updates/libpango1.0-0"). the download links are at the bottom of each page. just click to install them.

i am assuming you are using intrepid ibex. (8.10)

---

### Post by linuxmascot on 2009-01-21
thx sir for d reply ... 

but b4 dat, I think mine is ubuntu hardy heron (8.04) ...

I will try ur suggestion, bt ne idea whether dis will work for hardy?

---

### Post by Partyboi2 on 2009-01-21
If you are connected to the Internet it would be easier to install linuxdcpp by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install linuxdcpp
``` Or open Synaptic Package Manager and do a search for the package and install.

If you don't have Internet then you can go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/") and search for the package you need and download it.

---

### Post by linuxmascot on 2009-01-21
@ partyboi
hey when I tried executing dat command in the terminal I got a message like this

sudo: unable to resolve host spirit

I don't hav ne idea what that means ... i tried to make sure I have the super user privileges by running sudo bash command but got the same message ... wat shud i be doing??

@wolfen69

When I was trying out ur solution, it was giving a new dependency unsatisfied error ... libcairo2 

Guess I need to update my hardy heron ... 

Neways ... thx a lot people .. :)

---

### Post by Partyboi2 on 2009-01-21
> **linuxmascot said:**
> @ partyboi
hey when I tried executing dat command in the terminal I got a message like this

sudo: unable to resolve host spirit

I don't hav ne idea what that means ... i tried to make sure I have the super user privileges by running sudo bash command but got the same message ... wat shud i be doing??

@wolfen69

When I was trying out ur solution, it was giving a new dependency unsatisfied error ... libcairo2 

Guess I need to update my hardy heron ... 

Neways ... thx a lot people .. :)
Can you open a terminal and post the output to these commands
```
hostname
cat /etc/hosts
```

---

### Post by linuxmascot on 2009-01-22
@ partyboi

sorry for d delay in reply ... 

i excuted dose 2 commands u suggested:
hostname
SPIRIT

varun@SPIRIT:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 SPIRIT.DAIICT

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

This was the result of the second command, now i have got no idea wat dese are about... but my sudo bash command is still not working ... 

waiting for help!
thx...

---

### Post by linuxmascot on 2009-01-22
alright sir,

 thx for the info, I checked some other thread and fixed the problem... 

changed the second SPIRIT.DAIICT to SPIRIT

so, I can now be the super user ... :D

thx a lot ... but my linuxdcpp is still not working ... :P

---

### Post by Partyboi2 on 2009-01-23
> **linuxmascot said:**
> alright sir,

 thx for the info, I checked some other thread and fixed the problem... 

changed the second SPIRIT.DAIICT to SPIRIT

so, I can now be the super user ... :D

thx a lot ... but my linuxdcpp is still not working ... :P
Good to see your sorted yours /etc/hosts file out. :)
Did you manage to install linuxdcpp[FONT=monospace]?
[/FONT]```
sudo apt-get install linuxdcpp
```
then you can start it from the terminal if it install ok with
```
linuxdcpp
```

---

