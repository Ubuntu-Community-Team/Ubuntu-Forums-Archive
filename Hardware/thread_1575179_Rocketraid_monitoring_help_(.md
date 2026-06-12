---
title: "Rocketraid monitoring help :("
date: 2010-09-15
forum: Hardware
---

### Post by ownaginatious on 2010-09-15
Now, I'm running Debian, but I figured it's close enough to Ubuntu that possible someone here could help me.

Anyway, I currently have a RocketRaid 2310 card installed, and I'm having trouble getting either of the monitoring applications to work with it

I downloaded the package CLI-Linux-3.3-2-090806.tar.gz from [here]("http://www.highpoint-tech.com/USA_new/product_support_sata3.htm#rr2300"), which contains the programs hptraidconf and hptsvr. Neither seem to be working right.

When attempting to start hptraidconf in the terminal, I'm prompted for a username and password (User : RAID, Password : hpt) as default. When I do that, I get the following message:

```

studio-server:~# hptraidconf 
	HighPoint RAID Management Command Line Utility v3.3
Copyright (C) 2009 HighPoint Technologies, Inc. All rights reserved.

Login:RAID
Password:
ERROR: System can't be connected

```

This also seems to happen if I enter the wrong username and password...

Now when I try to start hptsvr, I get this message:

```
studio-server:~# hptsvr
Driver is not loaded.

```

Now, I entered the driver as per the instructions in /etc/hptconf
```

rr2310_00

```

Now, I know the driver is in fact loaded, I can see it when running lsmod:
```

studio-server:~# lsmod | grep "rr2310_00"
rr2310_00             228594  1

```

If it matters, this is what installation looked like:
```

studio-server:/home/administrator/Downloads/CLI-Linux-3.3-2-090806/deb# dpkg -i hptsvr_3.13-6_amd64.deb 
Selecting previously deselected package hptsvr.
(Reading database ... 92415 files and directories currently installed.)
Unpacking hptsvr (from hptsvr_3.13-6_amd64.deb) ...
Setting up hptsvr (3.13-6) ...
Can't detect any supported driver automatically.
hptmv6 is used by default.

update-rc.d: using dependency based boot sequencing
insserv: warning: script 'hptdaemon' missing LSB tags and overrides
Starting hptsvr daemonDriver is not loaded.
.

```

Any idea what's going on here? I would really like to be able to monitor this raid card :(.

Thanks!

---

### Post by ownaginatious on 2010-09-16
Bump?

---

### Post by sidzen on 2010-09-16
I looked here [www.highpoint-tech.com/PDF/.../RR230x_UM_EN_1_1_031607.pdf]("http://ubuntuforums.org/www.highpoint-tech.com/PDF/.../RR230x_UM_EN_1_1_031607.pdf"), starting on page 57, and did not find what I was looking for -- the RAID driver for Linux.  I had similar problems with a cheap VIA card I bought only to find it was next to useless in Linux.  (I use mostly Debian-based distros, too)

Here' some results from research on the topic of RAID cards for Linux:

&#65279;From what I gather, preferred RAID drivers over the sata_via in the PCI card in question are:

***Driver***
*Manufacturer*        _Model_
___________________

***sata_sil24    ***
*Silicon Image*        _Sil 3124, Sil 3132, and Sil 3531_

***ahci ***
                    *Intel*           _ICH6-10, ESB2, Tolopai_
                            *VIA*           _VT 8251_
                       *Marvel*            _6121, 6145_
                           *SiS*             _966,968_
                          *AMD*            _SB600/700/800_
                     *JMicron*             3_60, 361, 363, 365, 366_
                           *ULi*             _M5288_
                      *nVidea*             [U]MCP65, 67, 73, 77, 79, 7B

[/U]In short, one gets what he pays for and pays for what he does not research!

---

### Post by ownaginatious on 2010-09-16
I'm not sure what you mean, but this RAID card is definitely supposed to work in debian. Rocketraid's download site has debian packages just for the driver and utilities...

---

### Post by sidzen on 2010-09-16
You will most likely need a script file to make your RAID card work if insructions from HighPoint cannot make it.    Best of luck!

---

### Post by ownaginatious on 2010-09-16
Any other ideas anyone?

---

### Post by ownaginatious on 2010-09-17
Great, so my suggested solutions so far are find some sort of illusive magical script or to go get a Toronto escort. haha

---

### Post by IcarusR on 2010-09-17
Have you tried the 'online websupport' on the highpoint website ??

---

### Post by ownaginatious on 2010-09-19
I would try the online web-support, but unfortunately the system I'm trying to fix is at a remote location... and they won't give me support unless I give them the serial number (which is of course not written down anywhere).

Anyway, I ran a 'strace' on the hptsvr program and found some interesting information:

```

open("/dev/rr2310_000", O_RDWR)         = -1 ENXIO (No such device or address)
unlink("/dev/rr2310_000")               = 0
open("/proc/scsi/rr2310_00/", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)

```

It appears the software is looking for the device in two different locations... both of which do not exist. I know this is probably a long shot, but is it possible to somehow create '/dev/rr2310_000' or '/proc/scsi/rr2310_000/"?

There are modules located at the following places:

```

/lib/modules/2.6.26-2-amd64/kernel/drivers/scsi/rr2310.ko
/lib/modules/2.6.26-2-amd64/kernel/drivers/scsi/rr2310_00
/lib/modules/2.6.26-2-amd64/kernel/drivers/scsi/rr2310_00/rr2310_00.ko
/lib/modules/2.6.32-5-amd64/kernel/drivers/scsi/rr2310_00
/lib/modules/2.6.32-5-amd64/kernel/drivers/scsi/rr2310_00/rr2310_00.ko

```

Are any of these at all the same thing?

---

### Post by ejcdke on 2010-10-09
Did you ever figure this out?  I just got an rr2680 card and I'm having the exact same problem.  The strace shows it looking for /dev/26800 and /proc/sccsi/2680.  lsmod shows the driver running, which makes sense given the raid array works--I just can't get the CLI tools to run.  I had to compile the drivers from source due to a customized kernel and I thought maybe that has something to do with it.  I just can't seem to figure this out.

---

### Post by ownaginatious on 2010-10-09
Hi,

Unfortunately, I never did figure this out.

I had a very long string of trading messages over their 'chat support', and all they said was "Uhh try our newest version" or "Are you sure you installed it?". Eventually they marked my support thread as "solved" when I started showing I was frustrated - even though it clearly wasn't solved.

I tried some newer packages, but they won't even install (corrupted RPMs... go figure), and of course, they won't release the source code to compile the thing yourself.

I had a look through some of the scripts that came with the CLI installation, and the WebGUI - and it was clearly designed by someone who didn't really know what they were doing - there was also no documentation whatsoever.

My advice is go with a different brand in the future (preferably not a Chinese brand). I've been finding a lot recently that software design and documentation principles are basically non-existent there.

RocketRaid is officially on my blacklist as absolute garbage. Going to be swapping out this card soon.

---

### Post by jjazz on 2010-11-18
Hey guys, not sure if this will help you, but I just spent hours messing around with a rocketraid 622 and finally got the utils to work.

The cli bombed on install and i had to manually edit the hptraidconf.postinst file to remove windows CRLF chars.

After CLI and srvr were installed, i had to manually add my driver to the /etc/init.d/hptdaemon file. In the first line there is a PRODUCT list and the rr62x driver was not listed. I added that to the list and then the server started and I was able to get in to the CLI. 

Agree with ownaginatious about HighPoint being on the black list. Huge pain...

HTH...

---

### Post by AllGamer on 2011-04-25
Just for your reference, for those that are still looking for an answer.

Here's a quick HOWTO Guide I wrote to get HighPoint RAID Management Console to work with all the versions
[http://ubuntuforums.org/showthread.php?t=1737847](http://ubuntuforums.org/showthread.php?t=1737847)

---

### Post by rickatnight11 on 2012-03-31
I just got this working with my rr2680.  I had to tweak around a bit, but here are the items I remember.

**hptraidconf**
[LIST]
[*]As was previously mentioned, the pre/post scripts contained Windows CRLF characters that need to be removed.
[INDENT][LIST][*]Follow the instructions [here]("http://www.idimmu.net/2008/02/05/Changing-deb-package-architecture") to deconstruct the deb file and extract **control.tar.gz**.
[*]Open **postinst** and **prerm** in vim binary mode (*vim -b filename*)
[*]Press *:* and use a string substitution to replace the ^M characters: **%s/^M//g**.  (To insert the control-M character, press Ctrl+V and then Ctrl+M.)  If you can't figure that out, just manually go through and delete them.
[*]Follow those same instructions to compress the control files back into **control.tar.gz** and generate a new deb.[/LIST][/INDENT]
[*]The deb should install now.
[/LIST]

**hptsvr**
[LIST]
[*]This deb had a number of things wrong with it.  The first thing I noticed is that it wouldn't find my driver during the installation.  Then it would just sit.....and wait.
[INDENT][LIST][*]I finally discovered that it's waiting for you to type the name of the driver.  (I discovered this by finally getting fed up and hitting enter, after which a bunch of errors promptly followed.)
[*]I extracted the deb via the above instructions and found the *read* line in the script...no prompt, just read.  (Nice coding, HighPoint.)
[*]Typing in my driver (rr2680) didn't help much, due to more bugs in the script, so I went through the scripts to figure out what they actually do.
[*]The script echos out the contents of the init script, based on your flavor of linux.  One of the first lines of the script is to check for the driver name.  The list had **rr26xx**, which explained why my driver, **rr2680**, wasn't working.  I added mine to the list and repacked the deb.
[/LIST][/INDENT]
[*]At this point the deb detected the driver and installed successfully, but the post script, which starts the service, failed, due to a missing **/usr/bin/hptsvr**.  Turns out the deb installs it to **/bin**...nice going again, HighPoint.  I just created a symbolic link to solve that, but the real fix is to fix the deb itself.
[*]Creating the symbolic link let me start the service successfully, and now everything's working.
[/LIST]

I realize these instructions are a disjointed stream of consciousness, but that's intentional.  I'm not sure if this will even help anyone, so I wanted to jot down my experience for posterity.  If anyone's still having issues let me know, and I'll expand the instructions into a real guide and host an updated deb on my webserver.

---

