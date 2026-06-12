---
title: "Sudo issue"
date: 2005-11-29
forum: General Help
---

### Post by Stormspace on 2005-11-29
I'm getting this message when I log on.

> Could not look up internet address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts

When I try to use sudo it tells me unknownhost. Here is my hosts and hostname files.

```

/etc/hosts
127.0.0.1 localhost.localdomain localhost ubuntu

192.168.1.103 	tivoserver
192.168.1.109	marg 		
192.168.1.111	mccalll		
192.168.1.113	DOO		
192.168.1.117	zack		
192.168.1.200	printer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hostname
ubuntu

```

---

### Post by Stormspace on 2005-11-30
I can only assume by the lack of replies here that my issue is unrecoverable. That being the case I am very reluctant to reformat my harddrive and start over with Ubuntu just to gain sudo access again, and then loose it thus creating an endless loop of the same issue. I am at a dead end with regard to anything as a result of this. I cannot install or configure any apps, install updates, or anything. :(

---

### Post by tseliot on 2005-11-30
About the sudo issue:
Use a livecd (mepis, etc.) and log in as root
Open your /etc/sudoers with a text editor
Where you can see something about root (like sudo password all)
add a line below (copy the one with root) and replace the word "root" with your username.
Save the file. 
Boot in Ubuntu and you will have administrator's priviledges.

---

### Post by Stormspace on 2005-11-30
Good. I did set up a root account at one point and can su to get root access. Should I just check that file to make certain the entry exists, or is this something special?

---

### Post by teaker1s on 2005-11-30
hi I've started a bug for this your not alone and if you look at the bug you may be able to use my suggestions to work round it[ here]("https://launchpad.net/distros/ubuntu/+bug/4738/")

you should also be able to use synaptic with ubuntu cd to completely remove and  reinstall networking components if they are affected too

---

### Post by tseliot on 2005-11-30
[QUOTE=Stormspace]Good. I did set up a root account at one point and can su to get root access. Should I just check that file to make certain the entry exists, or is this something special?[/QUOTE]
It's just a workaround. I had the same problem (it's a bug)

---

### Post by Stormspace on 2005-11-30
[QUOTE=tseliot]It's just a workaround. I had the same problem (it's a bug)[/QUOTE]

This is a really nasty bug, since it disables your ability to update the PC via synaptic. I'll try the workaround and see what happens.

---

### Post by Stormspace on 2005-11-30
I edited the sudoers file but I get the same message at login and when i try to sudo I get:

```
sudo: unable to lookup ubuntu via gethostbyname()
```

---

### Post by Stormspace on 2005-12-01
I was able to fix it. I had edited my nsswitch.conf file changing this line

```
host: 		files dns 
```

to this

```
hosts: 		files dns 
```

---

