---
title: "Lirc not working on Ubuntu 12.04"
date: 2012-04-27
forum: Hardware
---

### Post by bergqvistjl on 2012-04-27
Hi, whenever I try to install lirc on ubuntu 12.04 64bit (up-to-date) it installs, but I get this output during the install:

```
(Reading database ... 155708 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.9.0-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up lirc (0.9.0-0ubuntu1) ...
ls: cannot access /lib/modules/3.2.0-24-generic/kernel/drivers/staging/lirc: No such file or directory
 * Loading LIRC modules                                                                                                                                                                              [ OK ] 
 * Starting remote control daemon(s) : LIRC
```

The install completes, yet the remote does not get picked up in irw (where it used to in 11.10) I presume because of the ls error. Any ideas? 

Thanks

---

### Post by bergqvistjl on 2012-04-28
Bump. Anyone got any ideas on how to fix it, or experiencing the same issues?

---

### Post by Veerappan on 2012-04-29
> **bergqvistjl said:**
> Bump. Anyone got any ideas on how to fix it, or experiencing the same issues?

I was experiencing similar issues post-upgrade to 12.04.

If you look in /dev/ for lirc*, there's both lirc0 and lirc1 (at least on my system).

When I switched from /dev/lirc0 to /dev/lirc1, irw started picking up my mceusb remote again.

---

### Post by danieleverywhere on 2012-06-25
Depending on what remote you use maybe this thred (the last post) may help you
[http://ubuntuforums.org/showthread.php?t=2000733](http://ubuntuforums.org/showthread.php?t=2000733)
I'm guessing it is a module or race condition problem

Good luck! I hope to hear some positive report ):P

---

### Post by jonas_t on 2012-06-27
Bump...

I've got the same problem. It used to work on 11.10. On my system (MBP 6,2) there isn't event any /dev/lirc* device. lsusb, however, lists the apple remote as before on 11.10...

isn't just the lirc kernel driver missing? that error
```

ls: cannot access /lib/modules/3.2.0-25-generic/kernel/drivers/staging/lirc: No such file or directory

```seems to me to be the main reason...

---

### Post by jonas_t on 2012-06-27
> **jonas_t said:**
> On my system (MBP 6,2) there isn't event any /dev/lirc* device. 

Ok, at least there is a lirc0 device in /dev now. I had to manually modprobe the 'irc_serial' module...


> **jonas_t said:**
> 
```

ls: cannot access /lib/modules/3.2.0-25-generic/kernel/drivers/staging/lirc: No such file or directory

```seems to me to be the main reason...

After doing some filesystem search and grep, I found that this is problably just an error in the package setup caused by moving kernel modules. The lirc modules are now in drivers/staging/media rather than in drivers/staging.

---

### Post by Zac280 on 2012-07-03
This is the bug report filed for this issue:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/1004239](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/1004239)

The workaround is 

```
sudo ln -s /lib/modules/3.2.0-25-generic/kernel/drivers/staging/media/lirc /lib/modules/3.2.0-25-generic/kernel/drivers/staging/lirc
```

with your version inserted.

---

### Post by ntsc525 on 2013-03-30
Well, here it is, March 30, 2013 and the problem persists.  Only the version has been changed to protect the obsolete.

I'm running Ubuntu 12.04 with all updates applied as of this date.

```

Preconfiguring packages ...
Selecting previously unselected package lirc.
(Reading database ... 190459 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.9.0-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Processing triggers for man-db ...
Setting up lirc (0.9.0-0ubuntu1) ...
ls: cannot access /lib/modules/3.2.0-39-generic/kernel/drivers/staging/lirc: No such file or directory
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC

```

After installation, I get the following:
```

irexec: could not open config files /home/silvad/.lircrc and /etc/lirc/lirc/lircrc
irexec: No such file or directory

```

Anyone?  Is there a workaround for this?  Is this the reason local configuration files aren't created, resulting in lirc not working with vlc?  Or should I look elsewhere for the solution to my problem?

---

### Post by ntsc525 on 2013-03-30
Well, I searched and searched before posting here, and THEN found the following fix for this particular problem ("ls: cannot access /lib/modules...").

It's a bug in the install script because the directory has changed from .../staging/lirc to .../staging/media/lirc, so you have to create a symbolic link unless you can hack the install script and fix it there.

So, you can fix it thusly:

```

sudo ln -s /lib/modules/3.2.0-39-generic/kernel/drivers/staging/media/lirc /lib/modules/3.2.0-39-generic/kernel/drivers/staging/lirc

```

Be sure to copy/paste the file name from your message because the version, in my case 3.2.0-39 changes over time.  So, I pasted the path twice, and inserted "/media" at the proper point in the first paste.

Then remove and reinstall lirc:
```

sudo apt-get remove lirc
sudo apt-get install lirc

```

Now that problem is solved, but my other problem remains, so I'm off to search for that one.

---

