---
title: "new 9.04 install, create mdadm raid0, reboot, then keyboard,mouse not working"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by aels on 2009-04-26
I used ubuntu server 8.10, now upgraded (clean new install) the new ubuntu 9.04.

My disk setup is 3 SATA disks, 1 x 160GB used for root/swap/other
The other 2 SATA disks are identical 320GB disks.
I would like to configure them into RAID 0.

I have done this via mdadm.

After configuration and formatting my new partition on the RAID 0 array, I perform a reboot. 
The system does not pickup my Array.  
I can get the array working, if I stop the array, then assemble it again.

Following some searching I found this bug recommendation :
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298)

After doing this, I perform a reboot.

I get the login screen as normal, but the mouse and keyboard is disabled.

If I boot into Safe mode, using command line and networking option, I can see that the Array is picked up and seem to work.   If I remove the entries as per the bug above from the /etc/mdadm/mdadm.conf file that specify the ARRAY, reboot, then all is working again, but I cannot see the Array, unless I again stop it, and assemble it again.

I tried adding mouse/keybord details to xorg.conf and reboot with the ARRAY definition in /etc/mdadm/mdadm.conf, but still same problem, mouse and keybord is disabled on login screen, so I cannot do anything.

This is frustrating.  Tried it with Kubuntu 9.04 that did not work, then switch to Ubuntu 9.04 and still same thing.

Any help with this would be appreciated.

---

### Post by talking_walnut on 2009-04-28
Same problem here. Had the RAID0 in 8.10 and then upgraded. Installed mdadm, rebooted and computer freezes on login screen. 

If I boot to recovery mode and uninstall mdadm everything works again so it's definitely something to do with mdadm. I'm reinstalling 8.10 now cause I don't have the time to try and figure this out at the moment but if someone finds a solution I'll try it :)

P.S. Forgot to say RAID is for storage. root, home and swap are all on a normal SATA drive.

---

### Post by rui.vapps on 2009-04-28
dbus / hal problem. I have same problem. upgrade from 8.10 to 9.04. lost keyboard and mouse on 2.6.28-11. 

how to fix:
reboot into recovery mode, then get into system (command line interface)
run following command:
 
update-rc.d -f dbus remove
update-rc.d -f hal remove
update-rc.d defaults dbus
update-rc.d defaults hal
reboot

it fix my.

---

### Post by micster on 2009-04-29
If I booted with my RAID plugged in I would get an error stating:
"**Failed to initialize HAL!**" and my system would lock up. So I tried this...
> **rui.vapps said:**
> update-rc.d -f dbus remove
update-rc.d -f hal remove
update-rc.d defaults dbus
update-rc.d defaults hal
reboot
Except the last two commands should be
```
update-rc.d **dbus** defaults 
update-rc.d **hal** defaults
```I didn't catch that they were written wrong before I rebooted. If you don't re-add them after removing them you will be in a world of hurt. Just spent the last hour trying to get my system to boot again :(

Oh, and that did not seem to fix my problem either.

---

### Post by rui.vapps on 2009-05-02
well. my mistake. it should be update-rc.d basename defaults :-)

I just fount it looks like random lock my keyboard and mouse. it happened again yesterday. but everytime if I login without X, it won't give me any problem. So what I did was: add dbus and hal restart on rc.local
echo -e "/etc/init.d/dbus restart\n/etc/init.d/hal restart" >> /etc/rc.local 
at least for now, it looks good. didn't have problem again.

---

### Post by mobrien118 on 2009-05-05
> **rui.vapps said:**
> well. my mistake. it should be update-rc.d basename defaults :-)

I just fount it looks like random lock my keyboard and mouse. it happened again yesterday. but everytime if I login without X, it won't give me any problem. So what I did was: add dbus and hal restart on rc.local
echo -e "/etc/init.d/dbus restart\n/etc/init.d/hal restart" >> /etc/rc.local 
at least for now, it looks good. didn't have problem again.

This looks promising for someone who has a user set to autologin. I, however have a fresh install off of the alternate CD, am having the same problem, and get stuck at the login screen.

I can access the system via the root shell with networking, have SSH installed, and thus can run X sessions on a remote system, but when I run "users-admin" as root (the gnome app that allows you to setup a user for autologin) I get "The configuration could not be loaded" "You are not allowed to access the system configuration".

Any idea how to set a user to autologin from the command prompt?

Ultimately, this is s CRITICAL bug. I mean, I already trashed my system trying to figure it out and spent the last 2 days on it. Did anyone file a bug?

Thanks,

--mobrien118

---

### Post by micster on 2009-05-05
FIXED IT!

If I booted with my RAID drives connected I would get an error "Initialization of HAL failed!" and if I disconnected them during boot everything would be fine. I checked my syslog and came across a segfault error for hald.

This bug report [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/361689]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/361689") seems to address my problem exactly.

I upgraded Hal using the PPA listed in the above bug report and now my problem is fixed! I can successfully boot and mount my software raid again (and I no longer lose my keyboard and mouse either).

-Mic

---

### Post by jayshomebrew on 2009-05-18
> **micster said:**
> I upgraded Hal using the PPA listed in the above bug report and now my problem is fixed! 
-Mic

How does one upgrade HAL using the PPA listed in the bug report?

I see the code is here:
[http://bugs.freedesktop.org]("http://bugs.freedesktop.org/attachment.cgi?id=25568")

---

### Post by lajo01 on 2009-05-23
Hi,
Also having this issue with server hanging with HAL error using mdadm I found the update package on the link above but trying to install it there is a depencancy on a newer version of libblkid1 than I have (1.41), 2.15. I can only find 1.45, does anyone know where to look?

Also, I'm running mythbuntu 9.04, if that matters....

Cheers
Anders

---

### Post by micster on 2009-05-28
> **jayshomebrew said:**
> How does one upgrade HAL using the PPA listed in the bug report?

I see the code is here:
[http://bugs.freedesktop.org]("http://bugs.freedesktop.org/attachment.cgi?id=25568")

I was also using Mythbuntu 9.04 and I simply upgraded through synaptic package manager. With the default desktop manager of Mythbuntu (I think it's KDE?) under settings or something, there is the Synaptic Packet Manager. Once you click on it, select one of the tabs that says something similar to "sources" where you can add what is called 3rd party sources or repositories. Enter the link that is given in that bug report above it should be:
```
deb http://ppa.launchpad.net/chrisccoulson/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chrisccoulson/ppa/ubuntu jaunty main
``` There is also a link somewhere within that window when you are adding your source called "authenticate" and this is where you put the signed OpenPGP key located [here]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2524246B1CC723DB") (also listed in the bug report).

After adding the new sources run an "update" to your system and reboot.

---

### Post by micster on 2009-05-28
Just to clarify, I fixed my problem after reading the bugreport and applying the fix created by [Chris Coulson]("https://launchpad.net/~chrisccoulson/+archive/ppa").

 I don't know if something changed since I applied the patch, it looks like Chris might have rewritten his fix and now it requires some new dependency? Maybe that is only a problem for 64 bit systems. When I updated, all the dependencies where automatically installed for me.

Good Luck,
Mic

---

### Post by mobrien118 on 2009-07-07
I am having this problem again.

Coincidentally, a new patch for HAL was released today and after installing it, now HAL is failing againg.

According to [the bug report]("https://bugs.launchpad.net/bugs/361689") it hasn't regressed, but why is HAL failing again for me now, after an update?

Anyone else having this issue again?

I was able to coach my sister through starting up this computer, launching it into a root terminal with networking and starting SSH, but other than that I am remote from this system. She said a message popped up about "failed to initialize HAL" or something of the sort, but I don't see any record of it (or hal at all) in the archived dmesg.0 (or .1, which also failed) or in "/var/log/messages"

Any help with this issue (even diagnosing it) would be very much appreciated!!!

--mobrien118

---

### Post by mobrien118 on 2009-07-07
OK, I see the error in "/var/log/gdm/:0.log"

It is "(EE) config/hal: couldn't initialise context: (null) ((null))"

Any ideas or know how I can dig deeper to find more information?

---

### Post by mobrien118 on 2009-07-07
Ok, I'm getting somewhere.

Over ssh, I ran /etc/init.d/gdm start and my network didn't drop.

I then used VNC to connect to the box and I saw that some gnome applet failed, but I'm sure it is caused by the error under it which reads "Internal Error" - "failed to initialize HAL!" - "X - _C_lose" (Screenshot attached).

Anyone, ANYONE having this issue, or is it just me?!?!?

(Maybe it's not related to the title where I mention mdadm, anymore)

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

### Post by mobrien118 on 2009-09-30
> **edvar said:**
> It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

Really? Wow! I will have to check that. I have just been having someone at the location of my server go and manually start it into "admin console" and start ssh, from there I start webmin and load all my services that way. Quite a tedious way to start a PC.

Where did you get the folder contents from? Did you just copy it off of your Mint box? I can probably do that with another Ubuntu installation I have, if my case is the same.

Thanks for the info. I have a bug posted and if this solves it for me, I will pass the info on. How strange!

---

