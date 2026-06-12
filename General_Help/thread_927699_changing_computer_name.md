---
title: "changing computer name?"
date: 2008-09-23
forum: General Help
---

### Post by lanr01 on 2008-09-23
Can one change the computer name that was entered during the initial install of ubuntu? can this be done without re-installing?

Thanks,
Rick

---

### Post by NoReflex on 2008-09-23
Yes, of course. 
Go to System->Administration->Networking and select the General section. Enter the name of the computer in the Hostname field, click Ok and reboot.
Or you can edit the /etc/hostname file : 
```
sudo gedit /etc/hostname
```

Bets wishes,
NoReflex

---

### Post by Krupski on 2008-09-23
> **NoReflex said:**
> Yes, of course. 
Go to System->Administration->Networking and select the General section. Enter the name of the computer in the Hostname field, click Ok and reboot.
Or you can edit the /etc/hostname file : 
```
sudo gedit /etc/hostname
```

Bets wishes,
NoReflex

Not exactly.

To change the hostname, two things need to be done:

```

sudo hostname newname
sudo /etc/init.d/hostname.sh start

```

First line changes the old hostname to "newname". Second line makes the change active.

-- Roger

---

### Post by lanr01 on 2008-09-23
> **Krupski said:**
> Not exactly.

To change the hostname, two things need to be done:

```

sudo hostname newname
sudo /etc/init.d/hostname.sh start

```

First line changes the old hostname to "newname". Second line makes the change active.

-- Roger
 Well did this, and now I am getting this error msg..

rick@main:~$ sudo /etc/init.d/main.sh start
sudo: unable to resolve host main

---

### Post by NoReflex on 2008-09-23
Doing **gksudo gedit /etc/hostname** is the same as **sudo hostname newname** and the reboot has the same effect as **sudo /etc/init.d/hostname.sh start**.

---

### Post by lanr01 on 2008-09-23
> **NoReflex said:**
> Doing **gksudo gedit /etc/hostname** is the same as **sudo hostname newname** and the reboot has the same effect as **sudo /etc/init.d/hostname.sh start**.

I have tried doing it both ways. and either way after I do and I try to install something via the terminal window using sudo, I get this

sudo: unable to resolve host main

the  host name in the network settings under the system administration netowrk shows it as main.

---

### Post by NoReflex on 2008-09-23
That's odd...Please post the output of this command **cat /etc/hostname**.
Did you restart your computer?

---

### Post by jerome1232 on 2008-09-23
No it's not odd at all it's expected they forgot to add a step.

You need to edit your hosts file
```
gksudo gedit /etc/hosts
```

change the entry that says 127.0.1.1   *hostname* to reflect your new hostname

so to sum it up you would do these commands, editing your hosts file to reflect the new,  hostname.
```
sudo hostname newhostname
gksudo gedit /etc/hosts
sudo /etc/init.d/hostname.sh start
```

OR gui

System>>Administration>>Network
click unlock; type your password
click General; Change the hostname
#not sure if this step is needed in this case
Click hosts; change the entry for 127.0.1.1 *hostname* To reflect the new hostname.
Logout, then log in change done.

---

### Post by windozehater on 2008-09-23
try downloading ubuntu tweak it has a section to rename your machine.

---

### Post by Atsuko on 2008-09-23
[ubuntu-tweak](http://ubuntu-tweak.com/)
It does that and more. good program but watch using it as it does not ask for password to change the files.

---

### Post by lanr01 on 2008-09-23
[QUOTE=jerome1232;5841370]No it's not odd at all it's expected they forgot to add a step.

You need to edit your hosts file
```
gksudo gedit /etc/hosts
```

change the entry that says 127.0.1.1   *hostname* to reflect your new hostname

so to sum it up you would do these commands, editing your hosts file to reflect the new,  hostname.
```
sudo hostname newhostname
gksudo gedit /etc/hosts
sudo /etc/init.d/hostname.sh start
```


That was it. I actually figured it out prior to reading this. I knew it had to be something I was overlooking. Thanks for all the help and being patient with someone that had never even looked at Linux before a few days ago. I am loving this... It is one heck of a powerful tool to say the least. I can't wait to get more up to speed on things. I am starting to catch on to some of the commands. I like that I can do more via the terminal than I ever would have done in windows... And FAST... and so configurable to boot..

 Now I just need to find a way to get a custom login manager that has an Ohio State Buckeyes logo  ;-) or find someone that would be willing to do one for me...

Thanks for all the help and take care. I will have more questions

---

### Post by Krupski on 2008-09-23
> **lanr01 said:**
> [QUOTE=jerome1232;5841370]
change the entry that says 127.0.1.1   *hostname* to reflect your new hostname


Hmmm... I purposely delete the 127.0.1.1 entry in my hosts file. What is the purpose of that? 

:confused:

---

### Post by doas777 on 2008-09-23
> **Krupski said:**
> [QUOTE=lanr01;5841891]

Hmmm... I purposely delete the 127.0.1.1 entry in my hosts file. What is the purpose of that? 

:confused:

well, as I;'m sure you know, 127.0.0.1 is your loopback adapters addr. 

the reason to add this line, is so you can resolve your logical hostname. otherwise you would have to use 'localhost' or the ip.

---

### Post by Krupski on 2008-09-23
> **doas777 said:**
> [QUOTE=Krupski;5842816]

well, as I;'m sure you know, 127.0.0.1 is your loopback adapters addr. 

the reason to add this line, is so you can resolve your logical hostname. otherwise you would have to use 'localhost' or the ip.

I have localhost 127.0.0.1 it's *127.0.1.1* that I'm wondering about.

---

### Post by jerome1232 on 2008-09-23
Apparently any 127.x.x.x address is a loopback address and it's used to give your loopback interface multiple names

127.0.0.1 localhost
127.0.1.1 hostname
127.0.2.2 anothername

at least that's the impression I get. 

edit: And according to debian manuals it's there for a reason.
This is section 10.4
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns)

> 10.4 Domain Name Service (DNS)

Hosts are referred to by domain name as well as by IP address. DNS is a client-server system in which name resolvers consult nameservers in order to associate domain names with IP addresses and other properties of hosts. The GNU C Library resolver(3) can also look up IP addresses in files or consult Network Information Services (NIS).

Some software (e.g., GNOME) expects the system hostname to be resolvable to an IP address with a canonical fully qualified domain name. This is really improper because system hostnames and domain names are two very different things; but there you have it. In order to support that software, it is necessary to ensure that the system hostname can be resolved. Most often this is done by putting a line in /etc/hosts containing some IP address and the system hostname. If your system has a permanent IP address then use that; otherwise use the address 127.0.1.1.

        127.0.0.1 localhost
        127.0.1.1 uranus

To see whether your system hostname can be resolved to an IP address with a fully qualified domain name, use the hostname --fqdn command. 

---

### Post by doas777 on 2008-09-23
> **Krupski said:**
> [QUOTE=lanr01;5841891]

Hmmm... I purposely delete the 127.0.1.1 entry in my hosts file. What is the purpose of that? 

:confused:

ok, lets say you are running apache on your host (named Host1), and developing on it locally. you want to run the page you've been working on, so you type in http://<servername>/site/page.htm .
if your host file is configured correctly you could use for your servername parameter:

localhost,
127.0.0.1
192.168.x.y
or 
**Host1**

in your case, sudo does not check it's lookup with localhost, but with the host name. since the host name is synonomous with localhost in default cases, you should map it to 127.0.0.1. you could theoretically map it to your local IP if you are using a static IP and will not move your computer. 


hope that helps clarify,
frank

---

### Post by doas777 on 2008-09-23
> **jerome1232 said:**
> Apparently any 127.x.x.x address is a loopback address and it's used to give your loopback interface multiple names

127.0.0.1 localhost
127.0.1.1 hostname
127.0.2.2 anothername

at least that's the impression I get. 

edit: And according to debian manuals it's there for a reason.
This is section 10.4
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns)

your hostname and localhost must be the same addr (127.0.0.1). do not change that address.
you can bind multiple names to an IP like so:

```
127.0.0.1 localhost hostname
```

never use an address in teh 127.x.y.z range for anything except loopback, unless you REALLY know what you are doing. I'm not sure it would work even if you did.

---

### Post by jerome1232 on 2008-09-23
That's the default setup. So no they don't have to be the same address.

---

### Post by doas777 on 2008-09-23
> **jerome1232 said:**
> That's the default setup. So no they don't have to be the same address.

are you saying that the localhost variable, and the name of the local host do not need to be the same addr? that doesn't make much sense.
127.0.0.1 is the TCP/IP reserved address for loopback.

---

### Post by bab1 on 2008-09-23
> 127.0.0.1 is the TCP/IP reserved address for loopback.
Well sort of...

The entire 127.0.0.0 range is reserved for the loopback interface.

jerome in post #15 gave the resaon that some use 127.0.1.1 for the loopback.  See: > [COLOR="Blue"]**Some software (e.g., *(GNOME) expects the system hostname to be resolvable to an IP address with a canonical fully qualified domain name.[/COLOR]* [COLOR="Green"]This is really improper because system hostnames and domain names are two very different things; but there you have it.[/COLOR] In order to support that software, it is necessary to ensure that the system hostname can be resolved. Most often this is done by putting a line in /etc/hosts containing some IP address and the system hostname. [COLOR="Magenta"]If your system has a permanent IP address then use that; otherwise use the address 127.0.1.1.[/COLOR]**

127.0.0.1 localhost
127.0.1.1 uranus


---

### Post by jerome1232 on 2008-09-23
Anything from 127.0.0.0 to 127.255.255.255 is a loopback address. That's what I'm saying.

```
cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 lifebane

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

ping -c 3 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.046 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.042 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.042/0.043/0.046/0.005 ms


ping -c 3 lifebane
PING lifebane (127.0.1.1) 56(84) bytes of data.
64 bytes from lifebane (127.0.1.1): icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from lifebane (127.0.1.1): icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from lifebane (127.0.1.1): icmp_seq=3 ttl=64 time=0.041 ms

--- lifebane ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.040/0.041/0.042/0.000 ms

ping -c 3 127.255.255.254
PING 127.255.255.254 (127.255.255.254) 56(84) bytes of data.
64 bytes from 127.255.255.254: icmp_seq=1 ttl=64 time=0.045 ms
64 bytes from 127.255.255.254: icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from 127.255.255.254: icmp_seq=3 ttl=64 time=0.043 ms

--- 127.255.255.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.042/0.043/0.045/0.005 ms

```

---

### Post by doas777 on 2008-09-23
fair enough, ya learn somthin everyday.

have fun,
frank

---

