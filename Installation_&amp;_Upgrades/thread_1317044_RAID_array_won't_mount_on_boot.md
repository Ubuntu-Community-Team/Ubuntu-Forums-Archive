---
title: "RAID array won't mount on boot"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Steve Roscio on 2009-11-06
Howdy -

Upgraded from Intrepid to Jaunty then right up to Karmic.
After this, my RAID0 array disappeared.
I noticed that the device changed from /dev/md0 to /dev/md/d0, so I redid the ARRAY line in /etc/mdadm/mdadm.conf, and updated /etc/fstab .

Now [FONT=Courier New][COLOR=DarkRed]mount -a[/COLOR][/FONT] works, and the array appears and I can access it, all is good.
Except on boot, the array does not appear.  After every boot I have to do a [FONT=Courier New][COLOR=DarkRed]mount -a[/COLOR][/FONT] to get it back.

How can I make it appear after each boot?

Thanx,
- Steve

Line in fstab:[FONT=Courier New][SIZE=2]
 /dev/md/d0      /srv    ext3    defaults,relatime        0       0[/SIZE][/FONT]
Line from mdadm.conf:
[FONT=Courier New][SIZE=2] ARRAY /dev/md/d0 level=raid0 num-devices=2 UUID=a6572a66:130f1ca5:ad1d4314:9df85527
[/SIZE][/FONT]

---

### Post by Steve Roscio on 2009-11-06
FWIW, I tried the solution posted in [http://ubuntuforums.org/showthread.php?t=1310224](http://ubuntuforums.org/showthread.php?t=1310224) , where /etc/default/grub is (created|modified), but that did not work for me.

---

### Post by Steve Roscio on 2009-11-09
I tried a [FONT=Courier New][COLOR=DarkRed]dpkg-reconfig mdadm[/COLOR][/FONT] .  That didn't fix it, but I did notice a warning that the startup/shutdown points I'm using (S25 and K25) are not matching LSB recommendations. 

This problem always felt like a timing thing - what are the recommended points for mdadm to start?

---

### Post by scram69 on 2009-11-15
I'm staring at the same problem - except fdisk reports it as md_d0, while mdadm --detail --scan calls it md/d0.

Did you ever find a solution to get the array to start at boot?

thanks-

---

### Post by burkeerr on 2009-11-23
I have my system set up a little different then what you have but this may help and was pretty simple.
System Setup:
1 TB Drive  -  Mounted to \
2 TB Raid (raid-0 2xTB Drives) - Mount \swap \home \windows(fat32)

I did a usb drive install of the desktop version of ubuntu and during the setup and install phase the system was able to see the raid drive correctly. Everything went great until i restarted the computer.

I received and error that the drives listed in fstab could not be mounted and to drop to recovery shell.

Fix: 
I downloaded the package
[]("http://packages.ubuntu.com/karmic/dmraid")[DMRAID]("http://packages.ubuntu.com/karmic/dmraid")
and the support 
[Libraid]("http://packages.ubuntu.com/karmic/libdmraid1.0.0.rc15")
[SIZE=1]booted into the recovery mode and reinstalled the dmraid
dpkg -i [/SIZE]libdmraid1.0.0.rc15[SIZE=1]
dpkg -i[/SIZE][SIZE=1] dmraid_1.0.0.rc15-11ubuntu3_amd64.deb[/SIZE]
reboot done!

Looks like even though the install has the dmraid it did not get installed to the system. This is partly why i don't boot from the raid.

---

### Post by Steve Roscio on 2010-01-13
Thanx for the ideas.  I didn't try using recovery mode (yet), but I gave this a shot:
```
# sudo apt-get install --reinstall dmraid libdmraid1.0.0.rc15
```
It downloaded the packages again and reinstalled them.  I rebooted, but...
No luck.  So I'll give it a shot from recovery mode when I get a chance.

---

### Post by Steve Roscio on 2010-01-31
Update:

Due to a hardware failure, I've had to reinstall my O/S.  So now with a fresh Karmic install, my RAID mounts fine.  Numerous other Karmic problems I had are now OK; I think there were problems when doing an _upgrade_ to Karmic, vs. a fresh install.

- Steve

---

