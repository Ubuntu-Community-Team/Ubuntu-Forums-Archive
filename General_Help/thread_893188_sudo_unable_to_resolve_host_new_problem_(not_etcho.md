---
title: "sudo unable to resolve host new problem (not /etc/hosts /etc/hostname difference)"
date: 2008-08-18
forum: General Help
---

### Post by Dejavou42 on 2008-08-18
I am having a problem with sudo. anytime I use a sudo command I get "sudo: unable to resolve host LinMyron" although the sudo command works. 

here is my /etc/hosts and /etc/hostname:
```
 1

/etc/hosts:

127.0.0.1 localhost
127.0.1.1 LinMyron


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hostname

LinMyron

```

any help is appreciated.

---

### Post by Dejavou42 on 2008-08-18
could avahi cause this problem?

I just noticed under system monitor that there is an entry for: avahi-daemon: running [LinMyron.Local]

---

### Post by Dejavou42 on 2008-08-18
so, after editing /etc/sudoers with gedit...booting into recovery mode (luckily I made a backup)  and restoring the file, I am back to the sudo error. (*INFO: lesson learned) 

I just noticed that the auth.log in syslog shows a very interesting pattern

```
Aug 18 06:17:08 ubuntu sudo:    myron : unable to resolve host ubuntu
Aug 18 06:17:08 ubuntu sudo:    myron : TTY=pts/0 ; PWD=******* ; USER=root ; COMMAND=/usr/bin/apt-get update now
Aug 18 06:17:08 ubuntu sudo: pam_unix(sudo:session): session opened for user root by myron(uid=0)
Aug 18 06:17:08 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Aug 18 06:17:22 ubuntu sudo:    myron : unable to resolve host ubuntu
Aug 18 06:17:22 ubuntu sudo:    myron : TTY=pts/0 ; PWD=******** ; USER=root ; COMMAND=/usr/bin/apt-get update
Aug 18 06:17:22 ubuntu sudo: pam_unix(sudo:session): session opened for user root by myron(uid=0)
Aug 18 06:17:22 ubuntu sudo: pam_unix(sudo:session): session closed for user root
Aug 18 06:17:49 ubuntu sudo:    myron : unable to resolve host ubuntu
Aug 18 06:24:13 ubuntu sudo:    myron : unable to resolve host ubuntu
Aug 18 06:25:01 ubuntu CRON[7084]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 06:25:01 ubuntu CRON[7084]: pam_unix(cron:session): session closed for user root
Aug 18 06:26:43 ubuntu sudo:    myron : unable to resolve host ubuntu
Aug 18 06:30:48 ubuntu sudo:    myron : unable to resolve host ubuntu
Aug 18 06:31:17 ubuntu last message repeated 2 times
```

notice the pam_unix open and close entry right before the sudo errors.

again, I have all functionality of sudo, but I still get this annoying error message. 

any thoughts? all help is greatly appreciated.

btw I also edited my hostname between the last post and this post...just to make sure....

---

### Post by michael_1234 on 2008-08-19
"sudo" tries to resolve "localhost" to an IP address, and, if it can't, you get this error.  If your hostname resolution includes /etc/hosts, then this file can map the localhost IP address to the name "localhost".  

Now, here's kind of the weird thing: in Ubuntu, in addition to the traditional 127.0.0.1 being "localhost", 127.0.1.1 is also used internally as localhost. So both should be included.

Try setting up your /etc/hosts file to include (at the top) the following, where "yourhost" is your short hostname, and "yourhost.yourdomain.com" is your fqdn:

( using your favorite editor, eg: $ sudo vim /etc/hosts )

127.0.0.1   localhost.localdomain   localhost   yourhost
127.0.1.1   yourhost  yourhost.yourdomain.com


I'm not sure if the fqdn is necessary or not, but I've included it for now in mine.  The following should also be fine,

$ cat /etc/hosts
127.0.0.1   localhost.localdomain   localhost   yourhost
127.0.1.1   yourhost

(Hopefully I don't have any typos.)

Cheers,
-m

---

### Post by Dejavou42 on 2008-08-19
I think that the fix you are describing is the is the fix for the difference between /etc/hosts and /etc/hostname. This is not the problem that I am experiencing. posted above are my /etc/hosts and /etc/hostname files, which are not different. That problem would also make the sudo command inoperable including all updates and administrative functions. I have full functionality of sudo commands and administrative functions. 

example: 

```
myron@ubuntu:~$ sudo ls -l
sudo: unable to resolve host ubuntu
total 582000
-rw-------  1 root  root   27841788 2008-08-18 04:35 2008-08-18-08-04-16.059-VBoxSDL-8405.log

```

the sudo command works, it just displays the error message: sudo: unable to resolve host ubuntu.

p.s. I just pasted part of the response from the ls-l command.

---

### Post by fethio on 2008-08-20
see this thread: [http://ubuntuforums.org/showthread.php?t=770801]("http://ubuntuforums.org/showthread.php?t=770801")

---

### Post by Dejavou42 on 2008-08-20
Thanks for the reply, but unfortunately that thread is still discussing the same problem that I mentioned above (/etc/hosts /etc/hostname difference), which is also not the problem that I am experiencing. As said in a post above, this would make sudo commands not work. My sudo commands all work, as well as administrative functions, it just gives me that error message. Thanks for the attempt though.... I appreciate any help that someone can send my way.

---

### Post by michael_1234 on 2008-08-21
> **Dejavou42 said:**
> unfortunately that thread is still discussing the same problem that I mentioned above (/etc/hosts /etc/hostname difference), which is also not the problem that I am experiencing. 

...Have you tried the proposed solution?  Your hosts file still looks basically incomplete; it's NOT the same thing as I've posted.

> **Dejavou42 said:**
> As said in a post above, this would make sudo commands not work. My sudo commands all work, as well as administrative functions, it just gives me that error message.

Well, this is not true; I've just tried this, myself. I do get the warning message, but sudo works.  I'll post exactly what I have (only the hostname / domain name changed to protect the innocent):

In both cases, I have my hostname:
```
$ cat /etc/hostname 
myhost

```=== good configuration ====
```
$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost myhost
127.0.1.1 myhost myhost.mydomain.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

$ whoami
userfoo

$ sudo ls
[sudo] password for userfoo: 
file1 file2 ....    

```=== bad configuration (slightly different, yes, but it causes the problem) ====
```
$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost
127.0.1.1 myhost.mydomain.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

$ sudo ls
sudo: unable to resolve host myhost
file1 file2 ...  

```*(Note: it doesn't ask my passwd the second time, since it remembered that I had just run a sudo command).*

And, auth.log,
```

/var/log/auth.log:Aug 21 10:49:19 myhost sudo: userfoo : unable to resolve host myhost

```

So, your problem may be completely unrelated, but this still sounds quite similar like what you're experiencing.  

Try posting your updated hosts file that tries this suggested solution, and you might get people looking for other possible solutions ... but until you try this (until we *know* you've tried this), there's not much reason to pursue & post alternative solutions. Nothing is a substitute for physical hands-on the keyboard, so we can only suggest things & hope the feedback you provide is sensible (cause/effect from our suggestions) & can generate new ideas.

Thanks & good luck,
-m

ps: btw, you might also check the sudo config, 

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by Dejavou42 on 2008-08-25
Ok, I checked sudoers file (it actually got me into alot of trouble because I didn't edit it with Visudio Read Above^) I checked my hosts and hostname file again. they looked ok.  I went to System --> Administration --> Network and changed Domain to local. Afterwards I changed the /etc/hosts file to match it like this:

```
/etc/hosts:

127.0.0.1 localhost.local localhost ubuntu
127.0.1.1 ubuntu


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I didn't put the myhost.mydomain.com part because I was not sure about the mydomain.com. All of this did not yield any different results. I still recieved the sudo error, but this time the terminal was sluggish to open and trying to edit /etc/hosts would not work because the editor froze. I changed it all back. Thanks for the help, but it didn't seem to work. Any suggestions? Maybe the mydomain.com thing. does my ISP go there? Thanks for all the help everyone.

---

### Post by Dejavou42 on 2008-08-30
OK I have some new information. I just installed ubuntu on a hp laptop for a friend. In the meantime, I compared my /etc/hosts ; /etc/hostname ; /etc/sudoers ; and /etc/modprobe.d/aliases files to the brand new installation. With the exception of the hostnames, my  files are exactly identical to his. so, this tells me that the problem is not in one of the previously mentioned files. I do however have a bridge set up between eth0 and a connection called VBox0 to give my Virtual Machine a unique ip address on my local network. Could something like that cause an unresolvable host issue? Any help is appreciated.

---

### Post by Dejavou42 on 2008-09-05
I Thought I would post /etc/network/interfaces:
```


auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

auto lo
iface lo inet loopback



iface eth4 inet ipv4ll

auto eth4


iface eth0 inet ipv4ll

auto eth0

```

Does this look like it would cause any problems? 

My network is unavailable sometimes at startup, I am using the "Local Zeroconf Network (IPV4LL)" setting...it seems to work the best.

```

myron@ubuntu:~$ sudo gedit /etc/network/interfaces
sudo: unable to resolve host ubuntu
[sudo] password for myron: 
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]


```

Also, I'm getting the usage message alot. It usually pops in after I close a program that's running with a terminal in the background. Any thoughts on that?

---

### Post by pigphish on 2008-09-05
Fixed my issue. Editing my /etc/hosts as described worked for me. 

I changed first line in my /etc/hosts from:
127.0.0.1 localhost  

to:
127.0.0.1 localhost localhost.local myhost
127.0.0.1 myhost

BTW, myhost is the same as listed in /etc/hostname 

didnt have to reboot just worked. 

hope this helps, george

---

### Post by Dejavou42 on 2008-09-06
Just to let everyone know, I tried the above mentioned solution again. Below is my current /etc/hosts, /etc/hostname, /etc/sudoers, /etc/network/interfaces, and the persisting sudo error. 

/etc/hosts:
```

127.0.0.1 localhost localhost.local ubuntu
127.0.1.1 ubuntu


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/hostname:
```

ubuntu

```

/etc/sudoers:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

/etc/network/interfaces:
```


auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

auto lo
iface lo inet loopback



iface eth4 inet ipv4ll

auto eth4


iface eth0 inet ipv4ll

auto eth0

```

Persisting Sudo error:
```

myron@ubuntu:~$ sudo gedit /etc/hosts
sudo: unable to resolve host ubuntu
[sudo] password for myron: 
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]myron@ubuntu:~$ sudo gedit /etc/hostname
sudo: unable to resolve host ubuntu
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]myron@ubuntu:~$ sudo gedit /etc/sudoers
sudo: unable to resolve host ubuntu
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]myron@ubuntu:~$ sudo gedit /etc/network/interfaces
sudo: unable to resolve host ubuntu
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]myron@ubuntu:~$ 


```

Difference in error message when running a command that does not start another program:

```


myron@ubuntu:~$ sudo uname
sudo: unable to resolve host ubuntu
Linux
myron@ubuntu:~$ 

```

Here is the current state of all of the files that have been requested in the duration of this post. This is not the normal Sudo hostname / hosts difference problem from what I have seen and read so far. Any help is appreciated on this issue.

---

### Post by michael_1234 on 2008-09-07
Sorry, I don't have an answer: but, I would like to correct a previous comment I made, after reading [a comment]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906/comments/90")  in a [bug related]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906") to [this issue]("https://bugs.launchpad.net/ubuntu/+bug/203593") (apparently fixed, tho). I'm not sure if what I had was entirely incorrect, but nonetheless, the [comment]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906/comments/90") on the aforementioned post suggests that 127.0.0.1 should never be mapped to a hostname; rather, use 127.0.1.1 for this (and this should map to /etc/hostname). 

But it doesn't sound like that's the problem described in this thread; I'm just correcting myself.

Another possible thing to look at is how, exactly, hostnames are being resolved.  (Otherwise, I'm out of ideas):

```
$ cat /etc/nsswitch.conf 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


Good luck,
-m

references:
[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)
[*][https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906/comments/90](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906/comments/90)
[*][https://bugs.launchpad.net/ubuntu/+bug/203593](https://bugs.launchpad.net/ubuntu/+bug/203593)
[/LIST]

---

### Post by Dejavou42 on 2008-09-08
Do programmers for the Ubuntu OS actually look at these forums, or would I be better to post a bug report to get help from one of them?

Thanks everyone.

---

### Post by thewindupman on 2008-09-10
I'm also having the same problem, and editing the hosts and hostname files as mentioned above didn't help at all.  Sudo works, but still complains everytime I try to use it.

---

### Post by Dejavou42 on 2008-09-10
I didn't have this problem when I first installed ubuntu, When I installed Ubuntu on this hard drive it was in another computer. I really noticed the problem when I added a Virtual Machine to the computer. Also, I remember that the internet was registering as being slower with some internet tests so I tried some things to disable IPV6. I would expect neither of the two things to cause a problem. I am also having a simultaneous problem with hcd_ehci, (driver for usb 2.0), I had to disable it. I'm not worried about these other things, I'm just listing them to narrow down some common variables.

---

### Post by Dejavou42 on 2009-04-11
It's been a while since I have updated this post, but I have finally found some new information. I have a domain name that points to my ip address. When I change my hostname to "mydomain.net", the sudo: unable to resolve host: (hostname) error goes away. So, I started look through the apps that I have installed to see if one of them was causing this. I had installed apache2 to this computer at one time to play with the configuration, but this computer is not a webserver. I found that apache2-utils includes a program called logresolve which "resolves ip addresses to host name in log files." 
I had hoped that this program was causing my issue since the description sounds like it would cause my problem. Uninstalling apache2-utils did not help. I am going to continue to look through my installed applications. In the mean time, does anyone know of another package that could cause this issue?

Thanks.

---

### Post by Dejavou42 on 2009-04-14
Setting my hostname to my domain name works, but I noticed that if the internet connection goes down, sudo will not work, and an error message pops up for gnome saying that it can not start the gnome settings daemon.

---

### Post by pikamoku on 2009-07-18
just for the record I have to say that changing 
> 127.0.0.1 myhostname
127.0.1.1 myhostname.WORKGROUP
in **/etc/hosts** to
> 127.0.0.1 localhost myhostname
127.0.1.1 myhostname myhostname.WORKGROUP
solved the problem.



being *myhostname* the result of
> cat /etc/hostname
and WORKGROUP
the work group for samba config file.

Maybe samba or other network sharing system may cause this problems with names resolution. I had an issue, time ago, with apache and samba too.

---

