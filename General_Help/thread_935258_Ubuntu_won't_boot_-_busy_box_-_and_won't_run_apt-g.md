---
title: "Ubuntu won't boot - busy box - and won't run apt-get or aptitude"
date: 2008-10-01
forum: General Help
---

### Post by mamendes on 2008-10-01
Ok,

Then 3 days running Ubuntu and now it won't boot, always got into busy box stuff.

I booted the live cd, changed root to /dev/disk (which was detected and mounted by live cd). When I try to run apt-get update or aptitude update I get:


root@ubuntu:/home/mamendes# sudo aptitude update
sudo: unable to resolve host ubuntu
Get:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release.gpg [189B]
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Translation-en_US                   
Get:2 [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy Release.gpg [189B]                     
Ign [http://directhex.mfgames.com](http://directhex.mfgames.com) hardy/main Translation-en_US                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://debian.meebey.net](http://debian.meebey.net) ./ Release.gpg    
96% [Working]FATAL -> Could not set non-blocking flag Bad file descriptor
E: Method http has died unexpectedly!


This time after so many problems I did thought that ubuntu would work, so I have some data on disk that I would not like to loose... If anyone has any idea on how to solve boot, or how to write a dvd during a live cd session (I only have one optical drive).

---

### Post by briandu on 2008-10-01
Boot from the Ubuntu disk then open a terminal session.

Then run update-grub and the booting will start again once you reboot.

---

### Post by mamendes on 2008-10-01
I did not work, same problem.

You mean after chroot?

```
root@ubuntu:/# update-grub
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=e9e620b4-5e43-4ad3-9a33-ffe071486f8a'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
/usr/sbin/update-grub: line 324: /dev/null: Permission denied
/usr/sbin/update-grub: line 253: /dev/null: Permission denied
/usr/sbin/update-grub: line 259: /dev/null: Permission denied
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Can't open /dev/null: Permission denied
```


And if you mean without chroot?

```
ubuntu@ubuntu:~$ update-grub
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###
```

And how can I make sure it will install grub on the correct hd?

---

### Post by mamendes on 2008-10-01
I restarted the livecd, chroot to /dev/sda3 and this time I could run aptitude update.

The grub menu.lst is alright. Maybe it's a superblock problem?

I'll try to install ubuntu-minimal and see if I can boot again.

---

### Post by theDaveTheRave on 2008-10-02
Mamendes

I'm having a similar but different issue, and I may have a solution for yours?

first the similarity between your problem and mine is based on the error message

> 
davem@[COLOR="Red"]Dartagnan[/COLOR]:~$ sudo /etc/init.d/samba stop
sudo: [COLOR="Red"]unable to resolve host Dartagnan[/COLOR]
[sudo] password for davem: 
 * Stopping Samba daemons                                                [ OK ] 
davem@Dartagnan:~$ 


What is interesting about this to me is that my hosts certainly looks like it is < Dartagnan > , which I can confirm by this....

> 
davem@[COLOR="Red"]Dartagnan[/COLOR]:~$ hostname
[COLOR="Red"]Dartagnan[/COLOR]
davem@Dartagnan:~$ 


And the output of my /etc/hosts file

> 
davem@[COLOR="Red"]Dartagnan[/COLOR]:~$ more /etc/hosts
127.0.0.1 localhost
127.0.1.1 [COLOR="Red"]Dartagnan[/COLOR].Mousquetaires

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
134.157.195.42 Anticlimax
davem@Dartagnan:~$


I can only assume it is something to do with the  <[COLOR="Red"]Dartagnan.Mousquetaires[/COLOR] line that is causing me grief?

if I may suggest that you post your /etc/hosts file you may find that that is where your problem is!

However for you problem you aren't going to be able to get to the main /etc/hosts system by the normal method, as you are going to be booting from the live CD, this means that you may have to hunt around for the file on your HDD, it will be there somewhere!

Alternatively you may be able to access one of the alternative terminals (tty). There are normaly 6 floating around underneath the main one that runs the xserver - (the 7th running x, and the others running various other "services" - at least that is the way I understand it).

Anyway they are normally available to log into, they can be access via an <Alt FKey> combination. AltF1 for the first AltF2 for the second etc... you may find you can log into one of these and run the various commands above and send them to a file eg.

> 
davem@Dartagnan:~$ more /etc/hosts >myHosts
davem@Dartagnan:~$ more myHosts
127.0.0.1 localhost
127.0.1.1 Dartagnan.Mousquetaires

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
134.157.195.42 Anticlimax
davem@Dartagnan:~$ 


As you can see the first line sent the results of the <more /etc/hosts> command to the file 'myHosts' in my local home directory, and then (just so as to prove that it had worked) I did a <more myHosts> to output the file to the terminal.

Thinking about it you may even be able to start the Xwindow system from inside the alternative tty, like this...

> 
davem@Dartagnan:~$ startx
hostname: Unknown host
xauth: (argv):1:  bad display name "Dartagnan:0" in "list" command
xauth: (stdin):1:  bad display name "Dartagnan:0" in "add" command

X: user not authorized to run the X server, aborting.

xinit:  unexpected signal 2.
xauth: (argv):1:  bad display name "Dartagnan:0" in "remove" command
Couldnt get a file descriptor referring to the console
davem@Dartagnan:~$ 


Obviously I get an error when I do this on my terminal as I've allready got an XWindows session running!

I hope the above information helps, and good luck with your rather anoying issue.... I know how awkard this is as I had something very similar last week, and I ended up doing a re-instalation of my system - the great thing is if you have set up your home directory on a separate partition all your old setting will be retained, so there is a lot less messing around after you have loaded everything!

good luck.

Dave

---

