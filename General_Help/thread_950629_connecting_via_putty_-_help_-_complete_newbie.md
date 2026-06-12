---
title: "connecting via putty - help - complete newbie"
date: 2008-10-17
forum: General Help
---

### Post by wrathican on 2008-10-17
Hi people

I am a complete newbie when it comes ssh. I am wanting to expand my knowledge in linux. to do this i am following this tutorial: 
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

I have installed the server successfully and i can execute command and such. I installed the server on a Virtual Machine using VirtualBox. 

I'm just after some advice on what to enter into PuTTY/where to get that info from on ubuntu.

when setting up the server i entered ubuntu1 as the hostname. if i enter that in PuTTY it tells me the host does not exist. 

If someone could help me get it setup i would be most greatful.

Thanks

Wrathican

---

### Post by Flynn555 on 2008-10-17
i dont really know what you are trying to do 

but, you might try putting the ip of the server as the host...

you might have to forward port 22 on your router...if you are not ssh'ing localy.

---

### Post by wrathican on 2008-10-17
well, i am ssh'ing locally, sorry should have said that.
what hostname/ip should i enter/how do i know what the ip is?

Thanks

---

### Post by Flynn555 on 2008-10-17
well if you are sshing localy your ip is going to be 192.168.0.something 

the last int is whatever port your machine is pluged into (on your router)
type 192.168.0.1 in the address bar of your web browser... this should bring up router options and tell you which computers are pluged into which ports (at least this works for me)

so your machines local ip is 192.168.0.port#  

ex:
*should be something like 192.168.0.4 or 192.168.0.13*

sorry im no expert on the subject.

---

### Post by wrathican on 2008-10-17
because im using a virtual machine would my ip be same as the host OS? if not then how do i get my ip using the CLI?

Thanks for your help!

---

### Post by Flynn555 on 2008-10-17
wait is the virtual box the server or client?

i dont know y you would want to ssh into a virtual box...

sorry mabee im just not understanding the problem.

---

### Post by wrathican on 2008-10-17
the server is the virual box. because its the server its all CLI. Im practising setting up a webserver but only want to run it locally. when it comes to putting one live i would like to be able to ssh to it. so i can just let it run.

thanks

---

### Post by KeyserSoze93 on 2008-10-17
have you got networking from within this virtual server? try pinging an address, such and

> ping ubuntu.org

if you do have the network working with the virtual server, run the command > ip addr and see what it says the ip is (inet).

Then, see if you can ping that ip from within your host OS, and if you can, then in theory, assuming ssh server is correctly installed, you should be able to use putty to access this ip.

---

### Post by wrathican on 2008-10-17
i tried pinging ubuntu.org it said unknown host

so i tried ubuntuforums.org and that (seemed) to work
it said 
```
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
```

then it kinda just hung and didnt let me type any commands so i stopped it (ctrl + c)
then said 
```
202 packects transmitted, 0 received, 100% packet loss, time 201101ms
```

when running ip addrs i got 2 different inet addy's

i got lo: 127.0.0.1/8 and eth0: 10.0.2.15/24

i can ssh localhost and that brings back the message about keys etc...

in the host os:
i tried pinging both addresses withouth the / and the 10.... request timed out

i pinged the 127... and that got a reply

i tried the 127.. in PuTTY and it said connection refused. then i tried 10... and the connection timed out.

Whats going on? :P

---

### Post by panhandle on 2008-10-17
Seems like you have some studying to do!:)

Try the following links, as they are excellent guides:

1) [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

2) [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by gpsmikey on 2008-10-17
What is the address of the machine you are pinging from ? They both need to be on the same subnet.  If you are in a windows command window, "ipconfig" will return your address, if you are on the linux machine, "ifconfig" will return the address plus a bunch of other stuff.  Both need to be on the same subnet - if the netmask is 255.255.255.0 (typical for a 192.168.x.x type address), only the last number should be different.  If they are not in the same subnet, then as you indicate, it will time out.

Networking is fun -- billions and billions of bits go everywhere ... unless one is wrong, in which case, nothing goes anywhere at all !! :)

mikey

---

### Post by Flynn555 on 2008-10-18
sorry i was way out of my element ;)

---

