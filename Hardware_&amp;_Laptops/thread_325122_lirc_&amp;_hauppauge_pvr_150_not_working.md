---
title: "lirc &amp; hauppauge pvr 150 not working"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by mariuss on 2006-12-25
I followed the instructions at [Install Lirc Edgy]("https://help.ubuntu.com/community/Install_Lirc_Edgy"), I am using a Hauppauge PVR 150, with the silver remote.

I used the 3rd party repository suggested by superm1. I configured and installed only the **i2c** driver.

All nice and dandy until I get to "Start Lirc & Test". Running irw will return back to the prompt right away, no messages. It also kills the lircd daemon.

Running dmesg | grep lirc gives only:
```
[17180719.460000] lirc_dev: IR Remote Control driver registered, at major 61 
[17180719.464000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
```

Not sure when the above mentioned **Install Lirc Edgy** works and when one should use [HOWTO: Lirc in Edgy]("http://www.ubuntuforums.org/showthread.php?t=288229").

Any suggestions?

Thanks,
Marius

UPDATE:

After lircd dies running lircd -n and then irw in another window gives:
```
$ sudo lircd -n
lircd-0.8.0[7499]: lircd(userspace) ready
lircd-0.8.0[7499]: accepted new client on /dev/lircd
lircd-0.8.0[7499]: could not open /dev/lirc
lircd-0.8.0[7499]: default_init(): No such device
lircd-0.8.0[7499]: caught signal
Terminated
```

But:
```
$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2006-12-24 23:04 /dev/lirc
srw-rw-rw- 1 root root     0 2006-12-24 23:39 /dev/lircd
prw-rw-rw- 1 root root     0 2006-12-24 23:04 /dev/lircm
```

---

### Post by mariuss on 2006-12-29
I got lirc working, at least as far as the irw test goes.

There were a couple of problems.

First, the correct driver for me was **mceusb2** and not **i2c**.

After installing the proper driver lircd was running properly, irw would not kill it, but irw was not seeing any events coming from the remote.

Second, I found the proper lircd.conf for my remote on the [Sysop.ca blog.]("http://www.sysop.ca/?p=55")

So, I have a Hauppauge PVR-150 MCE, with a USB IR adaptor. The remote is labelled "RC6" on the back and it has a silver/grey color.

Marius

---

### Post by superm1 on 2007-01-01
> **mariuss said:**
> I got lirc working, at least as far as the irw test goes.

There were a couple of problems.

First, the correct driver for me was **mceusb2** and not **i2c**.

After installing the proper driver lircd was running properly, irw would not kill it, but irw was not seeing any events coming from the remote.

Second, I found the proper lircd.conf for my remote on the [Sysop.ca blog.]("http://www.sysop.ca/?p=55")

So, I have a Hauppauge PVR-150 MCE, with a USB IR adaptor. The remote is labelled "RC6" on the back and it has a silver/grey color.

Marius
Marius, Thanks for the comments.  For those who may come across this thread with similar problems:
Here are some shots of what the MCE Remote looks like.  [http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)


Also, this lircd.conf is on the Install_Lirc_Edgy page on help.ubuntu.com.

My comments about the HOWTO: Lirc in edgy page, I wish the author would edit it to mention the help.ubuntu.com page and place some comments about when his howto is appropriate versus when the one on help.ubuntu.com is.  But he is MIA now.

---

### Post by daveyiv on 2007-01-05
> **mariuss said:**
> 

UPDATE:

After lircd dies running lircd -n and then irw in another window gives:
```
$ sudo lircd -n
lircd-0.8.0[7499]: lircd(userspace) ready
lircd-0.8.0[7499]: accepted new client on /dev/lircd
lircd-0.8.0[7499]: could not open /dev/lirc
lircd-0.8.0[7499]: default_init(): No such device
lircd-0.8.0[7499]: caught signal
Terminated
```

But:
```
$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2006-12-24 23:04 /dev/lirc
srw-rw-rw- 1 root root     0 2006-12-24 23:39 /dev/lircd
prw-rw-rw- 1 root root     0 2006-12-24 23:04 /dev/lircm
```

I am having this exact problem, however I am using the retail PVR150 card and IR receiver. It worked prior to my 3 week vacation, and now that I have returned it has stopped working. But my errors are exactly as they are above, with the exception of where above says (userspace) mine says (hauppauge).

Anyone know what my problem is?

---

### Post by superm1 on 2007-01-05
> **daveyiv said:**
> I am having this exact problem, however I am using the retail PVR150 card and IR receiver. It worked prior to my 3 week vacation, and now that I have returned it has stopped working. But my errors are exactly as they are above, with the exception of where above says (userspace) mine says (hauppauge).

Anyone know what my problem is?
As long as you used edgy packages, its a matter of modifying /etc/lirc/hardware.conf and making sure it is referring to /dev/lirc and not /dev/lirc0.

If you installed from source at some point to overwrite edgy packages/init scripts - this is where the trouble is coming from.

---

### Post by daveyiv on 2007-01-05
> **superm1 said:**
> As long as you used edgy packages, its a matter of modifying /etc/lirc/hardware.conf and making sure it is referring to /dev/lirc and not /dev/lirc0.

If you installed from source at some point to overwrite edgy packages/init scripts - this is where the trouble is coming from.

I think I did install from source at one point. Is there anyway to fix this mess I've got without starting from scratch?

---

### Post by superm1 on 2007-01-05
> **daveyiv said:**
> I think I did install from source at one point. Is there anyway to fix this mess I've got without starting from scratch?
Yup.

Backup your /etc/lirc/ folder.

```
sudo apt-get remove --purge lirc lirc-modules-source lirc-x

```

Also, if you have another package lirc-modules-`uname -r` or something like that installed, remove this.

Remove anything else that may have been built from source in /lib/modules/`uname -r`.  Bascially anything that is lirc*ko.

Remove any binaries sitting in /usr/local/bin that are lirc related.

Remove any shared libriares in /usr/local/lib that are lirc related.

```
sudo apt-get install lirc lirc-modules-source
```

Put your files back into /etc/lirc.  
Make sure that your /etc/lirc/hardware.conf has things pointing to /dev/lirc0.

Rebuild the modules per the guide to building them.  Try again.


----------
This is why source installations are bad in my opinion, see how much work it was to clean up after a dirty source install?

---

### Post by daveyiv on 2007-01-05
I did all that stuff and I guess I missed something, or the problem is elsewhere. I removed everything you said I think and am still having the same issue. Here is the error I am getting now when running 

sudo lircd -n

irw

```
mythtv@spork:/dev$ sudo lircd -n
lircd: could not open config file '/etc/lircd.conf'
lircd: No such file or directory
lircd: lircd(hauppauge) ready
lircd: accepted new client on /dev/lircd
lircd: could not open /dev/lirc
lircd: default_init(): No such device
lircd: caught signal
Terminated

```

I just don't know what to do, it worked last time I used it 3 weeks ago before my vacation and now it doesn't work.

---

### Post by superm1 on 2007-01-05
> **daveyiv said:**
> I did all that stuff and I guess I missed something, or the problem is elsewhere. I removed everything you said I think and am still having the same issue. Here is the error I am getting now when running 

sudo lircd -n

irw

```
mythtv@spork:/dev$ sudo lircd -n
lircd: could not open config file '/etc/lircd.conf'
lircd: No such file or directory
lircd: lircd(hauppauge) ready
lircd: accepted new client on /dev/lircd
lircd: could not open /dev/lirc
lircd: default_init(): No such device
lircd: caught signal
Terminated

```I just don't know what to do, it worked last time I used it 3 weeks ago before my vacation and now it doesn't work.
Okay next thing,
start it with the init script 
```
sudo /etc/init.d/lirc start
```

Also make sure that /etc/lirc/hardware.conf is reflecting /dev/lirc as your device and not /dev/lirc0 since that is what your device is listing.

The init script sets these paths  right and will find your /etc/lirc/lircd.conf in the right place.  Starting lircd like that uses /etc/lircd.conf

---

### Post by daveyiv on 2007-01-05
> **superm1 said:**
> Okay next thing,
start it with the init script 
```
sudo /etc/init.d/lirc start
```

Also make sure that /etc/lirc/hardware.conf is reflecting /dev/lirc as your device and not /dev/lirc0 since that is what your device is listing.

The init script sets these paths  right and will find your /etc/lirc/lircd.conf in the right place.  Starting lircd like that uses /etc/lircd.conf

When I try to start it in this way, and then I try to do a 

ps ax | grep lirc

It doesn't list the process as running. 

```
mythtv@spork:/var/run$ sudo /etc/init.d/lirc start
Starting lirc daemon: lircd lircmd.
mythtv@spork:/var/run$ ps ax | grep lirc
31562 pts/3    R+     0:00 grep lirc
mythtv@spork:/var/run$ irw
connect: Connection refused

```

My hardware.conf is as follows:

```
  GNU nano 1.3.12            File: /etc/lirc/hardware.conf                               

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc"
MODULES="lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

Here are my running modules dealing with i2c:

```

mythtv@spork:/$ lsmod | grep i2c
i2c_ec                  7808  1 sbs
lirc_i2c               14468  0 
lirc_dev               19880  1 lirc_i2c
i2c_algo_bit           11784  3 cx88xx,bttv,ivtv
i2c_viapro             11928  0 
i2c_core               29312  13 i2c_ec,cx88xx,bttv,lirc_i2c,wm8775,cx25840,nvidia,tda9887,tuner,ivtv,i2c_algo_bit,i2c_viapro,tveeprom

```

What else can I try to do?

---

### Post by daveyiv on 2007-01-05
Well, I tried reinstalling it again and lirc will now run using the command, but it will close whenever I execute irw.

```
mythtv@spork:/dev$ sudo /etc/init.d/lirc start
Starting lirc daemon: lircd.
mythtv@spork:/dev$ ps ax | grep lirc
 1717 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc
 1747 pts/0    R+     0:00 grep lirc
mythtv@spork:/dev$ irw
mythtv@spork:/dev$ ps ax | grep lirc
 1760 pts/0    R+     0:00 grep lirc
```

Also dmesg is listing the following:

```
[   49.632097] lirc_dev: IR Remote Control driver registered, at major 61 
[   49.641674] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

```

If I do a 

ls /dev/lirc*

all it returns is
```

mythtv@spork:/dev$ ls lirc*
lircd

```

So am I correct in assuming that a device doesn't exist? What could be my problem here?

---

### Post by superm1 on 2007-01-06
> **daveyiv said:**
> Well, I tried reinstalling it again and lirc will now run using the command, but it will close whenever I execute irw.

```
mythtv@spork:/dev$ sudo /etc/init.d/lirc start
Starting lirc daemon: lircd.
mythtv@spork:/dev$ ps ax | grep lirc
 1717 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc
 1747 pts/0    R+     0:00 grep lirc
mythtv@spork:/dev$ irw
mythtv@spork:/dev$ ps ax | grep lirc
 1760 pts/0    R+     0:00 grep lirc
```Also dmesg is listing the following:

```
[   49.632097] lirc_dev: IR Remote Control driver registered, at major 61 
[   49.641674] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

```If I do a 

ls /dev/lirc*

all it returns is
```

mythtv@spork:/dev$ ls lirc*
lircd

```So am I correct in assuming that a device doesn't exist? What could be my problem here?
The device not existing is exactly the problem here.  In the last few weeks, trying to think what could have changed - has anything else (even something that is seemingly insignificant changed, automatic kernel security updates, moved the card to a different slot)

---

### Post by cdekter on 2007-10-23
Bumping this thread.

I have a winfast dtv2000h and on Feisty the remote worked perfectly without any additional messing around. Now on Gutsy, I am having the exact problem described in this thread. Whether this is a bug or some problem with the default config for Lirc, come on guys we need to work out what's going on!

---

