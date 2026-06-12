---
title: "RocketRAID 1740 - 8.04"
date: 2008-10-11
forum: Hardware
---

### Post by pucenavel on 2008-10-11
I've looked through every thread I can find looking for a solution to my issue.  None of the discussions have been able to fully solve the issue, though each has helped to make some gains here and there.

Here is my situation:
AMD XP2700+ (i686 architecture)
Ubuntu 8.04 is installed and running quite happily on internal IDE drive - and I want to keep it that way
I have a RocketRAID 1740 controller card - PCI connected to (4) 1TB Drives
The RAID BIOS sees the drives and they are configured in two RAID5 arrays, one of 2TB and one of 1TB
I want to actually see these drives and, I don't know, maybe copy a file or two onto them.


Please help! I've got too much $$$ tied up in this.  If I can't make Ubuntu work I will have to fall back to Windows (more $$$).


What I know:

RocketRAID 1740 is not expressly supported on Ubuntu, but there is a source code driver available on the Highpoint website - the latest version (today being 10/11/08) is 2.1-080710
The drives are NOT initialized - online manufacturer documentation states that redundant arrays are not initialized by the BIOS, but by the software
In attempting to get the driver loaded, I have actually gotten as far as building it, installing it and loading it.  What I don't know is if anything has gone awry.  The best I've been able to do is get the RAID card to beep (alarm indicating array failure), but the BIOS shows all drives as OK.  I believe the driver has fully loaded because I am able to disable it under Hardware Drivers - which (thank god) stops the beeping after a reboot.

Do I need to figure out how to "initialize" the disks from the OS?

Highpoint has a link to a file that unpacks as *.rpm files (those are RedHat, right?).  No luck trying to install - apt-get doesn't like them.

The command I used was
```
sudo apt-get install hptsvr-3.13-4.i586.rpm
```

Please - please - there must be someone out there who has already done this and can give me some clear step by step instructions.

---

### Post by thinkdez on 2009-02-01
I don't have a RAID card myself but as for the software you are trying to install RPM's as you stated are not installable by apt.  That's because RPM's are for REDHAT flavor's of Linux ie REDHAT,SuSE,CENTOS etc.  Debian based distributions such as Ubuntu use .deb files as packages.  Don't give up though, there is a way you can get RPM's to work in Debian based distro's with alien.  

Run the following to install alien:
```
sudo apt-get install alien
```

Next download the RPM file
Then to convert a rpm to a deb file use the following:
```
sudo alien <insert rpm file name here>  
```

That should provide you with a .deb file that you should be able to install.  To install run the following:
```
sudo dpkg -i <Insert .deb file that was created above>
```

I hope this helps you out.

---

### Post by bvanaerde on 2009-02-12
I've got the same RAID controller... managed to install it using the source files. But I have to run some scripts in order to make them visible in Ubuntu.

When I get home, I'll post here what I did.

---

### Post by bvanaerde on 2009-02-17
Sorry, I made a little howto, but can't find it anymore.
This might be even better though:
[http://www.highpoint-tech.cn/China/bios_rr1740c.htm](http://www.highpoint-tech.cn/China/bios_rr1740c.htm)

Don't ask me why, but there are Ubuntu files on the Chinese website of HighPoint. Why can't they put them on the english pages too :o

---

### Post by bvanaerde on 2009-02-17
Ok, I got it working!
Those drivers found on the Chinese website (see my post above), didn't work here, probably because I'm using **Ubuntu 8.10 64bit**. But there are drivers for up to 8.04, so they might work for you.

This is what I did:
Download the opensource driver:
[http://www.highpoint-tech.com/USA/bios_rr1740.htm#opensourcedriver](http://www.highpoint-tech.com/USA/bios_rr1740.htm#opensourcedriver)
Extract the files to a folder (I used: rr174x-linux-src-v2.1).
Then do this in the terminal:
> cd rr174x-linux-src-v2.1/product/rr1740pm/linux
sudo make install
After a reboot, the RAID was loaded. I'm a bit surprised it was so simple...

> dmesg | grep rr174x 
gave me this:
> [   12.832738] rr174x:RocketRAID 174x controller driver v2.1.08.0710 (Feb 17 2009 21:43:21)
[   12.832780] rr174x:adapter at PCI 5:2:0, IRQ 18
[   13.401941] rr174x:start channel [0,0]
[   13.403378] rr174x:start channel [0,1]
[   13.404000] rr174x:start channel [0,2]
[   13.404000] rr174x:start channel [0,3]
[   13.608011] rr174x:[0 0] Start channel soft reset.
[   13.608031] rr174x:[0 1] Start channel soft reset.
[   13.608050] rr174x:[0 2] Start channel soft reset.
[   13.608068] rr174x:[0 3] Start channel soft reset.
[   13.916002] rr174x:channel [0,0] started successfully
[   13.916002] rr174x:channel [0,1] started successfully
[   13.916002] rr174x:channel [0,2] started successfully
[   13.916002] rr174x:channel [0,3] started successfully
[   14.269157] scsi16 : rr174x


I guess this will also work for 8.04.

---

### Post by babeliak on 2009-06-18
Great, this way it worked for me.Strange that manufacturers driver doesn't work and user has to use "make" on souce.

---

### Post by bvanaerde on 2009-06-18
I have yet to try this on 9.04, but I don't see why it wouldn't work.
I saw that they updated their [drivers page]("http://www.highpoint-tech.com/USA/bios_rr1740.htm"), a lot of version specific drivers are available now. They should work too.
> Strange that manufacturers driver doesn't work
Mind that those opensource drivers are also from the manufacturer.;)

---

### Post by babeliak on 2009-06-18
true, but I had to use "make" like you did, since february they posted Ubuntu drivers on [http://www.highpoint-tech.com](http://www.highpoint-tech.com), unfortunately they did NOT work for me (8.04 LTS, x86_64bit fresh install)
Now I have RAID webgui functional (converted using alien -d) and my new RAID5 seem alive ;) Thanks for help
I'm totally new to Linux, will try now to set SAMBA and the rest for winXP stations

---

### Post by bvanaerde on 2009-06-19
Nice to know that the WebGUI also works, thanks for mentioning that :D

---

### Post by Nebb on 2009-07-07
Thanks to both of you for your posts i was able to get my 1740 highpoint up and working. 

I did find it a bit difficult so I made a HOW TO for anyone else. Credit goes to everyone ;)

1740 Rocket Raid HOWTO
By Ben Murray July 7th 2009

This is a basic how to install and setup a highpoint rocket 
raid card 1740 with 4 sata hard drives and by no means perfect. 


First get the driver from highpoint-tech for your distro.

# sudo mkdir /temp/dd
# sudo tar xzvf rr174x-yourdistro.tgz -C /tmp/dd
# cd /tmp/dd
# sudo sh install.sh


once install has finished 

# sudo modprobe "XXXX"  <--- your module name in this case rr174x

or ou can reboot the system but your module may not start so you may need to still do this.
after reboot

# sudo dmesg | grep rr174x

Should get something like this

[ 12.832738] rr174x:RocketRAID 174x controller driver v2.1.08.0710 (Feb 17 2009 21:43:21)
[ 12.832780] rr174x:adapter at PCI 5:2:0, IRQ 18
[ 13.401941] rr174x:start channel [0,0]
[ 13.403378] rr174x:start channel [0,1]
[ 13.404000] rr174x:start channel [0,2]
[ 13.404000] rr174x:start channel [0,3]
[ 13.608011] rr174x:[0 0] Start channel soft reset.
[ 13.608031] rr174x:[0 1] Start channel soft reset.
[ 13.608050] rr174x:[0 2] Start channel soft reset.
[ 13.608068] rr174x:[0 3] Start channel soft reset.
[ 13.916002] rr174x:channel [0,0] started successfully
[ 13.916002] rr174x:channel [0,1] started successfully
[ 13.916002] rr174x:channel [0,2] started successfully
[ 13.916002] rr174x:channel [0,3] started successfully
[ 14.269157] scsi16 : rr174x 

Next assuming your raid array has been configured via high point bios (crtl-h on boot) 
locate in /dev your raid drive in this case it was /dev/sdb . 

so partion the raid drive

# sudo fdisk /dev/sdb

in the fdisk command use m for help pretty straight forward (google is you friend for fdisk)

after fdisk 

# sudo mkfs.ext3 /dev/sdb1

and wait


configure system to mount volume when startup

modify the /etc/fstab to add the following line 


/dev/sd"X"  /mnt/raid    ext3   defaults  0 0


("X" being your raid drive found in /dev i.e. /dev/sda1 or /dev/sdb1 so on)

/mnt/raid may need to be created or you could use another name

to make "raid" directory use:

# sudo mkdir /mnt/raid

thats all

---

### Post by hedefalk on 2009-07-14
babeliak, could you tell me how you got the webgui up and running?

I figured this much:
# wget [http://www.highpoint-tech.com/BIOS_Driver/HRM/Linux/WebGui-Linux-v1.4-8-080829.tgz](http://www.highpoint-tech.com/BIOS_Driver/HRM/Linux/WebGui-Linux-v1.4-8-080829.tgz)
# tar xzvf WebGui-Linux-v1.4-8-080829.tgz
# cd WebGui-Linux-v1.4-8-080829/
# sudo apt-get install alien
# alien hptsvr-https-1.4-8.i386.rpm
# sudo dpkg -i hptsvr-https_1.4-9_i386.deb

and it all seems to work just fine, but I'll need to do something more to start the gui up right? The manual I look at just states that it would run on port 7402:

"To run the management interface, start your browser and enter the following URL 
address: 
https://localhost:7402"

---

### Post by gregom on 2009-07-16
I'm at the same point hedefalk... I have a RR2320 running on 8.04 32bit. I got the driver installed file and was able to create the volume/filesystem. It is up and running but i'd like the WebGUI to initialize the array and monitor its status.

I downloaded the RPM packages from Highpoints site for the 2320 for the WebGUI v1.4-8, then I used alien to convert the RPM package to DEB, installed the package, then tried to access the webserver but got nothing... Tried manually launching the server and it says the driver is not loaded.

```
root@dvr:/tmp# alien --to-deb hptsvr-https-1.4-8.x86_64.rpm
Warning: Skipping conversion of scripts in package hptsvr-https: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
hptsvr-https_1.4-9_amd64.deb generated
root@dvr:/tmp# dpkg -i hptsvr-https_1.4-9_amd64.deb
Selecting previously deselected package hptsvr-https.
(Reading database ... 40355 files and directories currently installed.)
Unpacking hptsvr-https (from hptsvr-https_1.4-9_amd64.deb) ...
Setting up hptsvr-https (1.4-9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

root@dvr:/tmp# hptsvr
Driver is not loaded.
```Obviously something didnt run that was supposed to as there are missing files that the WebGUI readme says it needs:

>  The following files will be installed/configured:

/usr/bin/hptsvr - service program
/etc/hptcfg - service config file
/etc/rc.d/init.d/hptdaemon - service control script
/usr/share/hpt/webguiroot - data files
The /etc/hptcfg file doesn't exist and even trying the readme's suggestion of adding it manually by echoing the controller did nothing...

> 
If there is no /etc/hptcfg, you can add it manually by echo the controller
driver name to /etc/hptcfg. For example for RR3220

# echo hptiop >/etc/hptcfgThe /usr/bin/hptsvr file is there, but there is no /etc/rc.d/ folder... I only have rc0.d through rc6.d folders and an rcS.d folder. None of which have an init.d subfolder.

The /usr/share/hpt/webguiroot is there and everything in there looks normal...


I'm sure one could manually add the necessary folders and files and get the web server running, but I really have no idea what is needed. Hopefully someone else here does and can share how to do it with us.

---

### Post by babeliak on 2009-08-17
This is inside MY hptcfg file, I remember, I had to use echo to create it:
> rr174xdepending on your controller name, use echo command as follows:
```
echo <your driver module name> >/etc/hptcfg
```where <your driver module name> is rr174x in my case (I have RocketRaid1740) or different name depending on what model of controller card from HighPoint you have :) 
I remember I looked up my by displaying preinst.sh in gedit, it should be easy to look it up in any of those scripts (change path to fit yours to installation package):
```
georg@server:~$ ls /home/georg/install/rr174x-ubuntu-8.04-x86_64-v2.2.08.1017
boot  install.sh  postinst2.sh  postinst.sh  preinst.sh  readme.txt
``````
gedit /home/georg/install/rr174x-ubuntu-8.04-x86_64-v2.2.08.1017/install.sh
```Your desired and needed module name is > #!/bin/sh
# Post installation for debian 3.1 installation

# THis is the module name. Should be valid.
HPTMOD=rr174xyou guessed it > HPTMOD=<your driver module name>```
georg@server:~$ hptiop
bash: hptiop: command not found
```...I guess this is an error in the manual, because ```
echo hptiop
``` does write "hptiop" in /etc/hptcfg config file, which is of course useless.
After this Raid Management should be working, I had no issues with it. Just that above is a bit tricky.

---

### Post by babeliak on 2009-08-17
> **gregom said:**
> 

The /usr/bin/hptsvr file is there, but there is no /etc/rc.d/ folder... I only have rc0.d through rc6.d folders and an rcS.d folder. None of which have an init.d subfolder.
.

That above is the same for me.

README says only this: "If you can't connect to local system, please check if hptsvr is running on 
   the system. If not, start it manually by running "hptsvr""
...but must be run as SUDO:
```
sudo hptsvr
```

I have performance issues with this RAID since kernel update. I did not do this, maybe that's the cause:
"7 Rebuilding Driver Module for System Update
    When the system updates the kernel packages, the driver module rr174x.ko should be built
    and installed manually before reboot.
    To build the driver module, the RR174x open source package and the following building
    packages are needed: gcc, kernel-headers. The open source package can be got from
    HighPoint website: [http://www.highpoint-tech.com](http://www.highpoint-tech.com) while the building tools can be
    installed from the Ubuntu project website: [http://www.ubuntu.com](http://www.ubuntu.com)
    Note: the package version of kernel-headers should be the same to the version of updated
    kernel package.
    Refer to the REAME file distributed with HighPoint RR174x open source package on how
    to build and install the driver module.
"

---

### Post by babeliak on 2009-08-17
AHA, you must run it with sudo:
```
georg@server:~$ sudo hptsvr
```
Otherwise you get "Driver is not loaded" error message:
```
georg@server:~$ hptsvr
mknod: `/dev/rr174x0': Permission denied
Driver is not loaded.
```

---

### Post by babeliak on 2009-08-17
> **bvanaerde said:**
> Ok, I got it working!
Those drivers found on the Chinese website (see my post above), didn't work here, probably because I'm using **Ubuntu 8.10 64bit**. But there are drivers for up to 8.04, so they might work for you.

This is what I did:
Download the opensource driver:
[http://www.highpoint-tech.com/USA/bios_rr1740.htm#OpenSourcedriver](http://www.highpoint-tech.com/USA/bios_rr1740.htm#OpenSourcedriver)
Extract the files to a folder (I used: rr174x-linux-src-v2.1).
Then do this in the terminal:

After a reboot, the RAID was loaded. I'm a bit surprised it was so simple...


gave me this:


I guess this will also work for 8.04.

Wow, redownloaded [source]("http://www.highpoint-tech.com/BIOS_Driver/rr1740/Linux/newformat/rr174x-linux-src-v2.2-090407-1348.tar.gz") (just to make sure, it's same version 2.2 :)), unpacked, checked readme (note the latest tested linux kernel is 2.6.25, I'm running 2.6.24-24-generic), than:
```
~$ cd /home/georg/Desktop/rr174x-linux-src-v2.2/product/rr1740pm/linux
~$ sudo make install
```reboot and up and running full-speed again:
```
georg@server:~$ dmesg | grep rr174x
[   44.705244] rr174x: module license 'Proprietary' taints kernel.
[   44.705971] rr174x:RocketRAID 174x controller driver v2.2 (Aug 17 2009 20:23:09)
[   44.706015] rr174x:adapter at PCI 5:0:0, IRQ 20
[   45.281038] rr174x:start channel [0,0]
[   45.282489] rr174x:start channel [0,1]
[   45.283937] rr174x:start channel [0,2]
[   45.285385] rr174x:start channel [0,3]
[   45.481480] rr174x:[0 0] Start channel soft reset.
[   45.481502] rr174x:[0 1] Start channel soft reset.
[   45.481520] rr174x:[0 2] Start channel soft reset.
[   45.481539] rr174x:[0 3] Start channel soft reset.
[   45.840181] rr174x:channel [0,0] started successfully
[   45.922175] rr174x:channel [0,1] started successfully
[   46.004165] rr174x:channel [0,2] started successfully
[   46.086154] rr174x:channel [0,3] started successfully
[   46.149672] scsi0 : rr174x
```
```
$ sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  212 MB in  3.01 seconds =  70.36 MB/sec
```
:guitar:
Cheers again **bvanaerde** :) (have to save this page somewhere safe 8))

---

### Post by bvanaerde on 2009-08-19
> **babeliak said:**
> 
Cheers again **bvanaerde** :) (have to save this page somewhere safe 8))

Glad to hear you got it working!

---

### Post by bvanaerde on 2009-09-02
I tried to install the opensource drivers on Karmic Koala (kernel 2.6.31-9), without success :(
Has anybody managed to get those specific drivers (e.g. for ubuntu 9.04 x86_64) to work?

**edit:**

I installed Ubuntu 9.04 64bit, because that's the last version that HighPoint has drivers for. After the install, I installed every update from the update manager, **which installed a new kernel**.

I rebooted, and then installed the RocketRaid drivers.

> sudo sh install.sh

The install seemed to be successful and at the end, it said a reboot was needed. After the reboot, it seemed like the drivers were removed: nothing worked! It looked like the drivers were never installed (permanently?).

I guess this is because the driver files that can be found in the "boot" folder of the install, are named "rr174x**2.6.28-11**-genericx86_64.ko.gz" and "rr174x2.6.28-11-serverx86_64.ko.gz", which are meant for kernel 2.6.28-11. So, I just renamed "rr174x2.6.28-11-genericx86_64.ko.gz" to "rr174x**2.6.28-15**-genericx86_64.ko.gz" (to match my current kernel version).

After this, I reinstalled the driver (see above), rebooted, and voila: everything works!

edit: you'll now it works when you see these lines (the second line being the most important: when it's not there, you did something wrong)
> The disk you insert is for linux kernel 2.6
Update initrd file /boot/initrd.img-2.6.28-17-generic for 2.6.28-17-generic
Please reboot the system to use the new driver module.


My guess is this will also work on Ubuntu 9.10, but I haven't tried this yet. Enough OS installs for one day :)

---

### Post by hedefalk on 2009-09-08
You saved my day once more, bvanaerde!

I lost my raid after an upgrade, as described here: [http://ubuntuforums.org/showpost.php?p=7918394&postcount=2](http://ubuntuforums.org/showpost.php?p=7918394&postcount=2)

This was all i needed:
> 
$ uname -a
Linux .... 2.6.28-15-server
$ mv rocketraiddriversfolder/boot/rr174x2.6.28-11-serverx86_64.ko.gz rocketraiddriversfolder/boot/rr174x2.6.28-15-serverx86_64.ko.gz
$ sudo rocketraiddriversfolder/install.sh
$ sudo reboot now


Back in business!

---

### Post by babeliak on 2009-09-11
Good stuff guys!
Anyway I stay with 8.04 Hardy for longer support period.
Do you use also Highpoint Web Management Console?

---

### Post by tgrimley on 2009-09-11
Any chance you guys have some advice about [my situation here]("http://ubuntuforums.org/showthread.php?t=1262957")?

---

### Post by bvanaerde on 2009-10-03
**update**: after applying today's kernel upgrade, you'll have to install the RocketRaid drivers again.
Keep in mind that you have to manually edit the driver files prior to installing (as I mentioned earlier in this thread).

---

### Post by babeliak on 2009-11-10
I love this machine, it works flawlessly, just wondering how could I speed up my array?
```
georg@server:~$ sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  196 MB in  3.01 seconds =  65.06 MB/sec
georg@server:~$ dmesg | grep rr174x
[   31.036006] rr174x: module license 'Proprietary' taints kernel.
[   31.037566] rr174x:RocketRAID 174x controller driver v2.2 (Nov 10 2009 20:43:53)
[   31.037619] rr174x:adapter at PCI 5:0:0, IRQ 20
[   31.612040] rr174x:start channel [0,0]
[   31.613491] rr174x:start channel [0,1]
[   31.614938] rr174x:start channel [0,2]
[   31.616386] rr174x:start channel [0,3]
[   31.820702] rr174x:[0 0] Start channel soft reset.
[   31.820723] rr174x:[0 1] Start channel soft reset.
[   31.820741] rr174x:[0 2] Start channel soft reset.
[   31.820760] rr174x:[0 3] Start channel soft reset.
[   32.175371] rr174x:channel [0,0] started successfully
[   32.257305] rr174x:channel [0,1] started successfully
[   32.339234] rr174x:channel [0,2] started successfully
[   32.421163] rr174x:channel [0,3] started successfully
[   32.484401] scsi0 : rr174x
georg@server:~$ 
```I find 65 MB/s lil bit slowish, my array is made of 3x 500 GB SATA II NCQ Western Digital drives ([throughput 300 MB/s]("http://static.tigerdirect.com/html/sataarticle1.html")), what you think could be wrong? Our small office depends on this RAID. sorry for OT.

---

### Post by bvanaerde on 2009-11-30
Today I asked HighPoint if there are already drivers for Ubuntu 9.10:

[QUOTE="bvanaerde"]Hello

I wanted to upgrade my Ubuntu 9.04 installation to 9.10.
Will the RocketRaid 1740 still be supported in this distro?

At the drivers page, I can only find drivers up to version 9.04:
[http://www.highpoint-tech.com/usa/bios_rr1740.htm](http://www.highpoint-tech.com/usa/bios_rr1740.htm)

Greetings

Ben[/QUOTE]

The reply:

[QUOTE="HighPoint"]Hello,

Drivers are planned for 9.10, but are still being developed.

Regards,

HighPoint Technologies, Inc.
Customer Support Department[/QUOTE]

---

### Post by bvanaerde on 2009-12-08
**For those with Ubuntu 9.04:**

After the latest upgrade to 2.6.28-17, a reinstall of the RocketRaid is required again (see [my previous post]("http://ubuntuforums.org/showpost.php?p=7885168&postcount=18") if you don't know how)

When installing, it should display these lines:
> The disk you insert is for linux kernel 2.6
**Update initrd file /boot/initrd.img-2.6.28-17-generic for 2.6.28-17-generic**
Please reboot the system to use the new driver module.


**For those with Ubuntu 9.10:**

I couldn't wait any longer, and installed 9.10 today. As the driver page doesn't have a driver for 9.10, you have to use the opensource driver.
Download the file, unzip it, and with the terminal, browse to: 
> your_download_map/rr174x-linux-src-v2.4/product/rr1740pm/linux
and use this command:
> sudo make install
After this, restart.

**edit**: after today's kernel upgrade (for 9.10), I had to reboot into recovery mode and reinstall the drivers from there. After that, everything was fine again.

---

### Post by topkatz on 2009-12-11
First wanted to say thanks for this post, as I dont think I would have gotten my raid card up with out it.

I'm using the open source driver with 9.1 , but have some questions.

I keep tempting fate and updating the recent header files.  The problem is I dont know what I should do about the raid card.  This last time it split my raid in two, and I have been rebuilding it all day.  What is the correct procedure to update?  I'm thinking its something like

1 -uninstall driver
2 -restart
3 -update
4 -install driver
5 - reboot

but Im not sure what I should be doing to ensure my raid is kept in one peice.

Thanks

---

### Post by topkatz on 2009-12-11
It sounds like what I should be doing is rebuild the driver before restarting the box after update.  Can anyone confirm that this works.  It can not be any worse then what Im doing now, which is crashing and burning.

---

### Post by bvanaerde on 2010-01-08
> **topkatz said:**
> It sounds like what I should be doing is rebuild the driver before restarting the box after update.  Can anyone confirm that this works.  It can not be any worse then what Im doing now, which is crashing and burning.

The problem is: before the restart, you're still in the previous kernel version. So I guess you'll have to restart first.
What I do is:
[LIST=1]
[*]install new kernel
[*]reboot
[*]install RocketRaid driver
[*]reboot
[/LIST]

---

### Post by topkatz on 2010-01-22
The problem with that is my raid usually gets splintered into two raids.  Then I have to break the new one and rebuild.  Im obviously worried that this procedure wont go so well one time.

---

### Post by bvanaerde on 2010-01-22
> **topkatz said:**
> The problem with that is my raid usually gets splintered into two raids.  Then I have to break the new one and rebuild.  Im obviously worried that this procedure wont go so well one time.

What do you mean with splintered? I can't even access the drives when the drivers aren't installed yet.

---

### Post by babeliak on 2011-02-24
Any  news on HighPoint releasing RocketRAID 1740 driver for Ubuntu 10.04 LTS ?
That  would be cool...

---

### Post by AllGamer on 2011-04-25
> **babeliak said:**
> Any  news on HighPoint releasing RocketRAID 1740 driver for Ubuntu 10.04 LTS ?
That  would be cool...

You, can actually compile your own, it's very easy & quite straight forward

[http://ubuntuforums.org/showthread.php?t=1612915&highlight=rr1740](http://ubuntuforums.org/showthread.php?t=1612915&highlight=rr1740)

---

### Post by bvanaerde on 2011-11-14
I managed to get the drivers work on Ubuntu 11.10, using this thread.
[http://ubuntuforums.org/showthread.php?p=11456793](http://ubuntuforums.org/showthread.php?p=11456793)

---

### Post by babeliak on 2012-02-14
So are you up and running using your own compiled driver from open-source driver source code?
If so, I could try using first USB-stick test installation of 10.04.3 LTS and if all is OK, upgrade working environment file server...

---

