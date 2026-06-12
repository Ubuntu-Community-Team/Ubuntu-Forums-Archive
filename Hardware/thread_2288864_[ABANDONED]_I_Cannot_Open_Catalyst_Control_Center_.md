---
title: "[ABANDONED] I Cannot Open Catalyst Control Center After Upgrading to 15.04"
date: 2015-07-30
forum: Hardware
---

### Post by lambdafox on 2015-07-30
I  upgraded from Xubunti 14.10 to 15.04.  After the upgrade, my system had  fglrx and fglrx-core installed.  I had to manually install  flgrx-andcccle.    When I tried to run amdcccle from the terminal the cursor moved down one line and nothing else happened.  No error messages.    I rebooted, and the problem was the same.  So I purged the fglrx packages, rebooted and installed  fglrx-updates versions.    Then, when I run pkexec amdcccle, I get an Initialization error that reads:    > There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.   No AMD graphics driver is installed or the AMD driver is not functioning properly.  Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.   When I run sudo aticonfig --initial --adapter=all    I get this error:    ```
Unable to open /etc/ati/control, please reinstall the driver. aticonfig: No supported adapters detected   ProblemType: Bug DistroRelease: Ubuntu 15.04 Package: xorg 1:7.7+7ubuntu4 ProcVersionSignature: Ubuntu 3.19.0-25.26-generic 3.19.8-ckt2 Uname: Linux 3.19.0-25-generic x86_64 ApportVersion: 2.17.2-0ubuntu1.1 Architecture: amd64 CurrentDesktop: XFCE Date: Wed Jul 29 23:02:03 2015 JournalErrors:  -- Logs begin at Wed 2015-07-29 22:12:49 EDT, end at Wed 2015-07-29 23:02:12 EDT. --  Jul 29 22:39:39 hostname org.gtk.vfs.Daemon[2253]: ** (gvfsd:2408): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused  Jul 29 22:39:39 hostname org.gtk.vfs.Daemon[2253]: ** (process:13132): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted SourcePackage: xorg UpgradeStatus: Upgraded to vivid on 2015-07-29 (0 days ago) 
```  I purged fglrx-updates and used the 14.12 installer.  14.12 did install.   aticonfig --init --adapters=all worked.  BUT, when I reboot the system,  my login screen is overlain with a black window that says:  "starting  version 219".  I found a post thru google that suggested this would eventually go away, so I left it on over night and +-8 hrs later the message was still on my screen this morning.  This is my first time doing a version upgrade; so, it did not occur to me that I might need to do the aticonfig initialization again at the very beginning.  I just purged fglrx, again.  I re-installed the fglrxc packages. aticonfig appears to work, but now amdcccle gives me the same error as the fglrx updates packages: > There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.   No AMD graphics driver is installed or the AMD driver is not functioning properly.  Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig. 

---

### Post by lambdafox on 2015-07-31
I have a long work day today, but tomorrow, I am going to pull out a spare hard drive and see if I can get catalyst to run with a fresh install of vivid or wiley.  If I cannot, I am going to go back to ubiquitous.

---

### Post by lambdafox on 2015-08-01
Well, I have never been so disappointed to have something work. CCC opens fine in a fresh install of Vivid... the next few hours will be a re-install... sigh

---

### Post by QIII on 2015-08-01
Don't reinstall.

Before you upgraded, did you first uninstall the fglrx driver AND remove /etc/X11/xorg.conf?

---

### Post by lambdafox on 2015-08-01
> **QIII said:**
> Don't reinstall.  Before you upgraded, did you first uninstall the fglrx driver?  Linux Noob = Not Knowing That Would Be A Good Idea

---

### Post by QIII on 2015-08-01
Yeah.  Need to do that on any upgrade.  Let's see if we can get you going without reinstalling.

Do you get the GRUB menu when you boot, or does it normally go directly to the Ubuntu login?

---

### Post by lambdafox on 2015-08-01
i get grub

---

### Post by QIII on 2015-08-02
Let's go to (I think it is) "Advanced Options"

When there, select "Root with networking"

After quite a bit of text scrolls by, you'll be at the root prompt.  But there's not much you will be able to do just yet, since your filesystem will be mounted read-only.  You need to remount read-write.

Issue the command 

```
mount -o remount,rw /
```

Note that there is no space in "remount,rw".

When your are remounted read-write, issue the following:

```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

You need to purge both pairs, because your system may try to install the other if you don't do this explicitly.

When that is done, issue

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

That will effectively rename xorg.conf.  By default, Ubuntu does not use xorg.conf.  However, when you install a  proprietary driver, the file is created.  If you don't remove or rename it and you have removed the fglrx driver, it will cause problems.  Your system will try to use it and choke on the settings.

This should bring you back to the default open source driver, but let's make sure by reinstalling a couple of things

```
apt-get purge xserver-xorg-video-ati xserver-xorg-video-radeon
```
```
apt-get install xserver-xorg-video-ati
```
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

That should have you back to the open source driver as it was when you first installed Ubuntu.

---

### Post by lambdafox on 2015-08-02
Sorry for the weird formatting.  The forum is ignoring my doubele CRs this morning...> Hey, QIII.  Thanks again for your help. I will continue with the post you made from last night.    Before I do, though I want to record a couple of info points here ...    > Yesterday, while mucking with the different releases, I messed up grub on my main drive.  I used the boot-repair-disk to fix that.  After doing that, I got an error that I had not seen before that pcspkr was already loaded and the boot process stopped before log-in.  I found that I could solve that by editing /etc/sysstem.d/blacklist.conf to include that.  I am not sure why I did not see this error before doing the boot recovery process?   > I got through that error, and now I am unable to log in due to a new problem.  Booting drops out to the root prompt. I see this:  ```
starting version 219
``` ```
[   10.800052] i2c i2c-0: Unrecognized stepping 0x45. Defaulting to ADM1026.
``` ```
Welcome to emergency mode! After logging in, type "journalctl -xb" to view
``` ```
system logs. "systemctl reboot" to reboot, "systemctl default" or^D to
``` ```
try again to boot into default  mode. root@randypc:~#
```  > When I was unable to log-in due to the black overlay that said "starting version 219" (see my original post) , I could not find any explanation of what it was or where it came from, just the recommended solution that did not work for me.  The new error appearing at log-in leads me to believe that I have a problem with lm-sensors.  That would also explain why my conky has not looked right since the upgrade.  I had assumed I just needed to redo lm-sensors  configuration similar to the aticonfig process, but maybe not...

---

### Post by Yellow Pasque on 2015-08-02
So did you run all of the 6 commands in the previous post? 

> Welcome to emergency mode!
Yes, this is where you're supposed to log in and run the 6 commands. Write them down if you don't have another system to view them.

> starting version 219
This is just an informational message that systemd is starting. It is always there, but when the GUI (X Windows) starts, you normally don't see it because it flies by too fast or is obscured by the startup splash screen.

---

### Post by Yellow Pasque on 2015-08-02
@QIII:
> I purged fglrx-updates and used the 14.12 installer.

The user installed Catalyst manually at some point. It's possible s/he needs to run at least the second command (after purging fglrx) if s/he did not build/install packages:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo rm -rf /etc/ati
```

---

### Post by QIII on 2015-08-02
Didn't see that.  

Thanks!  Quite right, of couse.

---

### Post by lambdafox on 2015-08-02
> **Temüjin said:**
> So did you run all of the 6 commands in the previous post? ...

Yes, I have now completed that.  When I boot normally, the system drops out of X before I can log in and still shows this:


```
starting version 219
[   10.800052] i2c i2c-0: Unrecognized stepping 0x45. Defaulting to ADM1026.
Welcome to emergency mode! After logging in, type "journalctl -xb" to view
system logs. "systemctl reboot" to reboot, "systemctl default" or^D to
try again to boot into default  mode. root@randypc:~#
```

I found [this conversation]("http://fixunix.com/kernel/342733-panic-about-sysfs-adm1026.html") about this problem, but I do not understand it.

---

### Post by lambdafox on 2015-08-02
> **Temüjin said:**
> @QIII:


The user installed Catalyst manually at some point. It's possible s/he needs to run at least the second command (after purging fglrx) if s/he did not build/install packages:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo rm -rf /etc/ati
```

When I did that I used the option to create packages and then used dpkg -i.

There was no fglrx-uninstall.sh to run.  I did delete the folder with the provided command.

---

### Post by Yellow Pasque on 2015-08-02
> **lambdafox said:**
> I used the option to create packages and then used dpkg -i.

Ah, good job.

At this point, the /var/log/Xorg.0.log will give more details beyond "X didn't start". When you login to the terminal, run:
```
sudo apt-get install pastebinit
cat /var/log/Xorg.0.log | pastebinit
```

Write down the link it outputs and share it here.

---

### Post by lambdafox on 2015-08-03
ok...  I found the source of the panic error I was getting.

Sorry if I use the wrong words to describe this, but here is the gist of it.

I have a udf drive that mounts into my home folder at boot and is then shared via ftp.  I had disconnected that drive and my main drive when I was installing the tests on my old spare.  Idiot me forgot to reconnect the sata cable on the UDF drive.  I corrected that stupid mistake and am now back into my desktop in my main PC --  woo hoo!!

Now, I will try again to get the catalyst control center to work.

---

### Post by lambdafox on 2015-08-03
> **Temüjin said:**
> ...```
sudo apt-get install pastebinit
```...

After fixing my latest problem, I get errors if I try to install the fglrx package. I tried before I saw this.  I tried repeating the root login with the six steps again.  I am seeing errors that did not show when I had my other problem.

> **Temüjin said:**
> ...```
sudo apt-get install pastebinit
```...

```
~$sudo apt-get install pastebinit
[sudo] password for randyb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pastebinit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 14.8 kB of archives.
After this operation, 168 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/main pastebinit all 1.4-4 [14.8 kB]
Fetched 14.8 kB in 0s (95.1 kB/s)     
Selecting previously unselected package pastebinit.
(Reading database ... 234803 files and directories currently installed.)
Preparing to unpack .../pastebinit_1.4-4_all.deb ...
Unpacking pastebinit (1.4-4) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libgl1-mesa-glx:amd64 (10.5.2-0ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Similar errors about libgl1-mesa-glx being a problem appeared when I tried to repeat the root process above.

---

### Post by QIII on 2015-08-03
Can you post the error messages for us to look at?

Even a snapshot from a cellphone would be helpful if you can't use the UI to do it.

---

### Post by Yellow Pasque on 2015-08-03
> update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status

You may have to manually fix this. Start reading :) (I won't have time until tonight).
```
man update-alternatives
```

---

### Post by lambdafox on 2015-08-03
> **QIII said:**
> Can you post the error messages for us to look at?

Even a snapshot from a cellphone would be helpful if you can't use the UI to do it.

I am at work for the next several jours.  would i find them in a log?

---

### Post by QIII on 2015-08-03
The easiest thing would be to attempt to install the driver from the command line, then copy and paste the results back here.

---

### Post by lambdafox on 2015-08-04
I did these in a terminal rather than at the root prompt off the grub menu.  The errors look the same to me:

```
~$sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
[sudo] password for randyb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libgl1-mesa-glx:amd64 (10.5.2-0ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lambdafox on 2015-08-04
```
sudo apt-get purge xserver-xorg-video-ati xserver-xorg-video-radeon
[sudo] password for randyb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'xserver-xorg-video-ati' is not installed, so not removed
Package 'xserver-xorg-video-radeon' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libgl1-mesa-glx:amd64 (10.5.2-0ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libgl1-mesa-glx:amd64
 xserver-xorg-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lambdafox on 2015-08-04
```
~$sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[sudo] password for randyb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,468 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for xserver-xorg-core:amd64
~$
```

---

### Post by lambdafox on 2015-08-04
```
~$sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
[sudo] password for randyb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,468 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for xserver-xorg-core:amd64

```

---

### Post by lambdafox on 2015-08-04
I wonder if I did this, might it fix the problem?

```
sudo apt-get clean
sudo apt-get install --reinstall *
```

---

### Post by Yellow Pasque on 2015-08-04
Again, there's a corrupt link in the alternatives system that needs to be fixed, or apt is going to continue to fail. Check its status and see if you can select a new alternative:
```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
If it's corrupted beyond fixing, blow it away and it should be recreated when you finish installing libgl1-mesa-glx
```
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo dpkg --configure -a
```

---

### Post by lambdafox on 2015-08-05
> **Temüjin said:**
> Again, there's a corrupt link in the alternatives system that needs to be fixed, or apt is going to continue to fail. Check its status and see if you can select a new alternative:

```
sudo update-alternatives --config x86_64-linux-gnu_gl_conf
[sudo] password for randyb: 
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
~$sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
~$sudo dpkg --configure -a
Setting up libgl1-mesa-glx:amd64 (10.5.2-0ubuntu1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-glx:amd64
 xserver-xorg-core
```

---

### Post by lambdafox on 2015-08-05
```
~$update-alternatives --query x86_64-linux-gnu_gl_conf
update-alternatives: error: /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf corrupt: invalid status
~$
```

---

### Post by Yellow Pasque on 2015-08-05
Hmm. Googling the error some more, it seems that folks had to manually delete the link file:
```
sudo rm /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf
sudo dpkg configure -a
```

---

### Post by lambdafox on 2015-08-06
> **Temüjin said:**
> Hmm. Googling the error some more, it seems that folks had to manually delete the link file:
```
sudo rm /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf
sudo dpkg configure -a
```

```
~$sudo rm /var/lib/dpkg/alternatives/x86_64-linux-gnu_gl_conf
[sudo] password for randyb: 
~$sudo dpkg --configure -a
Setting up libgl1-mesa-glx:amd64 (10.5.2-0ubuntu1) ...
update-alternatives: error: unable to read link `/etc/alternatives/x86_64-linux-gnu_gl_conf': Invalid argument
dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-glx:amd64
 xserver-xorg-core

```

At this point, I have decided to stop kicking this horse.  I am working up from the fresh install I did on my other drive.  Thank you all for your help!

---

