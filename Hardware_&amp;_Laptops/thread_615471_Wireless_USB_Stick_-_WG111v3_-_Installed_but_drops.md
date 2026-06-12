---
title: "Wireless USB Stick - WG111v3 - Installed but drops out"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by jonathanpeter on 2007-11-17
I've managed to get the above working.  I have one problem, the connection keeps dropping out.  Does anyone have any ideas as to how to resolve this?


I've noticed people have been struggling to get as far as me - so here is how I did it:

Open Terminal (Applications > Accessories > Terminal)
```

wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz
wget http://www.avengergear.com/upload/WG111v3.tar.bz2
tar xvvf ndiswrapper-1.49.tar.gz
tar xvvf WG111v3.tar.bz2
cd ndiswrapper-1.49
make
sudo su -            (enter your password)
apt-get remove ndiswrapper-common
apt-get install build-essential
make install
ndiswrapper -i ../WG111/WG111v3.inf
depmod -a
modprobe ndiswrapper
ndiswrapper -m
exit
exit


```

(then setup in the normal way via network manager)

-----------

Teaching worth taking the time over:

[www.sermonsfortoday.org]("http://www.sermonsfortoday.org/")

---

### Post by jonathanpeter on 2007-11-17
More information:

It drops out when I encrypt the network.  If the network isn't encrypted it works fine.

Any thoughts?

---

### Post by mdurham on 2007-11-17
Same problem here, anybody know what the answer is?
Cheers, Mike

---

### Post by PaulStr on 2007-12-26
Every time I try(using ndiswrapper-1.49) I get this:

```
root@paul:~# ndiswrapper -i ../WG111/WG111.v3.inf
couldn't open ../WG111/WG111.v3.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
root@paul:~# 
```

could someone help me?

---

### Post by jonathanpeter on 2007-12-26
You've got the filepath wrong.  Which directory did you unzip the driver to?  If you were following my instructions, it should have been:

ndiswrapper -i ./WG111/WG111v3.inf

I think.

---

### Post by PaulStr on 2007-12-26
I copied directly from your posts.

I've had this problem every time I've tried to use ndiswrapper with every version I've tried.

---

### Post by mdurham on 2007-12-26
PaulStr, install the 'ndisgtk' GUI installer, that should make it easier.
Cheers, Mike

---

### Post by PaulStr on 2007-12-26
I'll try that.

[EDIT]

I tried ndisgtk and it told me that the driver was already installed. I followed through with the rest of the procedure and it's still no dice.

---

### Post by mdurham on 2007-12-27
> **PaulStr said:**
> I'll try that.

[EDIT]

I tried ndisgtk and it told me that the driver was already installed. I followed through with the rest of the procedure and it's still no dice.

Try removing and reinstalling the driver with ndisgtk, maybe that will help things?
It's worth a try!

---

### Post by jonathanpeter on 2007-12-27
If the driver is installed, sounds like the device cannot be found.  What happens when you do:

sudo modprobe ndiswrapper

?

Also, which version of WG111 hardware do you have?  I know theres lots of different versions.

Another suggestion:

You could try removing the existing WG111v3 driver and install it again.

---

### Post by PaulStr on 2007-12-27
Absolutely nothing happens when I do sudo modprobe ndiswrapper. 

I have WG111v3 and am using the WG111v3 driver linked to above.

ndisgtk doesn't show in the little window that there's a driver there, but file manager shows that there is in the /etc/ndiswrapper/WG111/WG111v3 folder.

The device is detected in Hardware Information, so I assume it's detected.

---

### Post by PaulStr on 2007-12-29
After restarting my computer, it started to work.


Thanks for the help all.

---

### Post by Maricaibo on 2008-01-10
Looks like driver for card was installed as I can see all the wireless networks in my area. But I CANNOT get an IP address, either thru Network Manager or in Terminal using the command 'sudo dhclient wlan0'

The Netgear card seemed to work in FFawn, but NOT Gutsy!

HELP please!!!

---

### Post by vesko on 2008-01-25
hi evryone i just installed ubuntu and i am totaly lost when it comes to computers i am trying to get my wg111v3 to work and here is what i get:
vesko@vesko-desktop:~$ wget [http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz](http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz)
--07:59:40--  [http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz](http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz)
           => `s...er-1.49.tar.gz'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net) [following]
--07:59:40--  [http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net)
           => `s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net) [following]
--07:59:40--  [http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net)
           => `s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://sourceforge.net/projects/s---er-1-49-tar-gz/files](http://sourceforge.net/projects/s---er-1-49-tar-gz/files) [following]
--07:59:41--  [http://sourceforge.net/projects/s---er-1-49-tar-gz/files](http://sourceforge.net/projects/s---er-1-49-tar-gz/files)
           => `files.1'
Resolving sourceforge.net... 66.35.250.203
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 10,222        --.--K/s             

07:59:41 (81.94 KB/s) - `files.1' saved [10222]

vesko@vesko-desktop:~$ wget [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)
--07:59:41--  [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)
           => `WG111v3.tar.bz2.1'
Resolving [www.avengergear.com](www.avengergear.com)... 66.98.190.41
Connecting to www.avengergear.com|66.98.190.41|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 286,410 (280K) [application/x-bzip2]

100%[====================================>] 286,410      582.51K/s             

07:59:41 (582.16 KB/s) - `WG111v3.tar.bz2.1' saved [286410/286410]

vesko@vesko-desktop:~$ tar xvvf ndiswrapper-1.49.tar.gz
tar: ndiswrapper-1.49.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
vesko@vesko-desktop:~$ tar xvvf WG111v3.tar.bz2
drwxr-xr-x nobody/nobody     0 2007-10-24 05:48 WG111/
drwxr-xr-x root/root         0 2007-10-24 05:48 WG111/Vista64/
-rwxr--r-- root/root     10722 2007-10-24 05:48 WG111/Vista64/wg111v3.cat
-rwxr--r-- root/root     11216 2007-10-24 05:48 WG111/Vista64/wg111v3.inf
-rwxr--r-- root/root    269824 2007-10-24 05:48 WG111/Vista64/wg111v3.sys
-rwxr--r-- nobody/nobody 236334 2007-05-15 06:19 WG111/wg111v3.sys
-rwxr--r-- nobody/nobody  13312 2007-10-24 05:22 WG111/WG111v3.PNF
-rwxr--r-- nobody/nobody  12705 2007-05-10 21:22 WG111/WG111v3.inf
vesko@vesko-desktop:~$ cd ndiswrapper-1.49
bash: cd: ndiswrapper-1.49: No such file or directory
vesko@vesko-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
vesko@vesko-desktop:~$ sudo su - (enter your password)
bash: syntax error near unexpected token `('
vesko@vesko-desktop:~$ apt-get remove ndiswrapper-common
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
vesko@vesko-desktop:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
vesko@vesko-desktop:~$ make install
make: *** No rule to make target `install'.  Stop.
vesko@vesko-desktop:~$ ndiswrapper -i ../WG111/WG111v3.inf
couldn't create /etc/ndiswrapper/wg111v3: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
vesko@vesko-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
vesko@vesko-desktop:~$ modprobe ndiswrapper
vesko@vesko-desktop:~$ ndiswrapper -m

the card is not working allthough ubuntu reckognizes it, card works on xp laptop
any suggestions?

---

### Post by sat@evolution on 2008-02-11
Excellent guide mate :):):):):)

thanks to you:guitar: thanks to you

---

### Post by jonathanpeter on 2008-02-18
> **vesko said:**
> hi evryone i just installed ubuntu and i am totaly lost when it comes to computers i am trying to get my wg111v3 to work and here is what i get:
vesko@vesko-desktop:~$ wget [http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz](http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz)
--07:59:40--  [http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz](http://easynews.dl.sourceforge.net/s...er-1.49.tar.gz)
           => `s...er-1.49.tar.gz'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net) [following]
--07:59:40--  [http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://prdownloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net)
           => `s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net) [following]
--07:59:40--  [http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net](http://downloads.sourceforge.net/s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net)
           => `s...er-1.49.tar.gz?download&failedmirror=easynews.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://sourceforge.net/projects/s---er-1-49-tar-gz/files](http://sourceforge.net/projects/s---er-1-49-tar-gz/files) [following]
--07:59:41--  [http://sourceforge.net/projects/s---er-1-49-tar-gz/files](http://sourceforge.net/projects/s---er-1-49-tar-gz/files)
           => `files.1'
Resolving sourceforge.net... 66.35.250.203
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 10,222        --.--K/s             

07:59:41 (81.94 KB/s) - `files.1' saved [10222]

vesko@vesko-desktop:~$ wget [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)
--07:59:41--  [http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)
           => `WG111v3.tar.bz2.1'
Resolving [www.avengergear.com](www.avengergear.com)... 66.98.190.41
Connecting to www.avengergear.com|66.98.190.41|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 286,410 (280K) [application/x-bzip2]

100%[====================================>] 286,410      582.51K/s             

07:59:41 (582.16 KB/s) - `WG111v3.tar.bz2.1' saved [286410/286410]

vesko@vesko-desktop:~$ tar xvvf ndiswrapper-1.49.tar.gz
tar: ndiswrapper-1.49.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
vesko@vesko-desktop:~$ tar xvvf WG111v3.tar.bz2
drwxr-xr-x nobody/nobody     0 2007-10-24 05:48 WG111/
drwxr-xr-x root/root         0 2007-10-24 05:48 WG111/Vista64/
-rwxr--r-- root/root     10722 2007-10-24 05:48 WG111/Vista64/wg111v3.cat
-rwxr--r-- root/root     11216 2007-10-24 05:48 WG111/Vista64/wg111v3.inf
-rwxr--r-- root/root    269824 2007-10-24 05:48 WG111/Vista64/wg111v3.sys
-rwxr--r-- nobody/nobody 236334 2007-05-15 06:19 WG111/wg111v3.sys
-rwxr--r-- nobody/nobody  13312 2007-10-24 05:22 WG111/WG111v3.PNF
-rwxr--r-- nobody/nobody  12705 2007-05-10 21:22 WG111/WG111v3.inf
vesko@vesko-desktop:~$ cd ndiswrapper-1.49
bash: cd: ndiswrapper-1.49: No such file or directory
vesko@vesko-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
vesko@vesko-desktop:~$ sudo su - (enter your password)
bash: syntax error near unexpected token `('
vesko@vesko-desktop:~$ apt-get remove ndiswrapper-common
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
vesko@vesko-desktop:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
vesko@vesko-desktop:~$ make install
make: *** No rule to make target `install'.  Stop.
vesko@vesko-desktop:~$ ndiswrapper -i ../WG111/WG111v3.inf
couldn't create /etc/ndiswrapper/wg111v3: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
vesko@vesko-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
vesko@vesko-desktop:~$ modprobe ndiswrapper
vesko@vesko-desktop:~$ ndiswrapper -m

the card is not working allthough ubuntu reckognizes it, card works on xp laptop
any suggestions?


Part of your problem is that you need to do some of the above stuff using root, the linux super user.  To do this, simply type 

sudo su -

at the command line... and enter your password.

---

### Post by deefa on 2008-02-25
Hi.
I'm quite new to this kind of thing and could use some advice. I double checked and followed your instructions to the letter and this happened:-


paul@paul-desktop:~$ tar xvvf ndiswrapper-1.49.tar.gz
tar: ndiswrapper-1.49.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
paul@paul-desktop:~$ 

Can you advise please?

---

### Post by jonathanpeter on 2008-02-25
Follow them again - copy and paste each command into the terminal.   A html link didn't download properly.

---

### Post by Durden on 2008-03-25
I just got this working but am having a problem I hope someone can help with. It doesn't seem to retain the module when I reboot, is there something I am missing?

---

### Post by stooshbunutu on 2008-04-10
Hello, the title says that the stick keeps dropping out.

If this is still a problem I have a solution as I have an encrypted and hidden router that doesn't drop out.

See how I did it on my site. [http://helpbuntu.iwarp.com/wireless.html](http://helpbuntu.iwarp.com/wireless.html)

I start exactly the same as you but but configure it differently (i believe) using network manager

Regards,stooshbunutu

---

### Post by terrifickid on 2008-05-28
Hey there,

Thanks for this post.

I've had my WG111v3 working fine with ndiswrapper for some time. But now its busted =[

For some reason, everytime I restart, the WG111v3 won't show up in network settings. I haft to run sudo modprobe ndiswrapper and then it will appear.

It looks like ndiswrapper is still there in modprobe.d? I don't know much about this stuff.

I think an ubuntu update busted it (as usual). 

I think I've tried removing/reinstalling it but no luck. Can anyone help a boy out?

THanks,
TK

---

### Post by jonathanpeter on 2008-05-29
I have the same problem.  An ubuntu update has mucked it all up.  As a temporary fix, I'm using Windows until they bring out an update which fixes the problem.

---

