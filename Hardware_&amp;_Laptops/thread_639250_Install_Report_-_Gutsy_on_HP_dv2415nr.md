---
title: "Install Report - Gutsy on HP dv2415nr"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by gdselzer on 2007-12-13
I picked this laptop up at Best Buy as an open box special. It's a nice little computer for the $: AMD Turion 64X2, nVidia GeForce Go 6150, 160GB HD, nice looking monitor, and webcam among others. See attached lspci.log for all of the hardware.
 
I thought I would log the install since there are so many horror post about Gutsy on HPs, and also for myself to reference later. Overall I would say this went pretty smooth. The machine is currently dual booting with Vista.
 
**1. Set up partitions for install and Dual Boot**.
 
When I first tried to partition the drive from the Install utility it wouldn't do it for me. (I don't remember the exact language, but if someone can remind me I'll edit this post so others can search by it.) Turns out that you have to resize the Vista partition (assuming you want to keep it, which I do) from within Vista. Reboot into Vista, go to Disk Management and I freed up 20 GBs for the Ubuntu install. My plan was to use the Windows partition to store all big files (mp3s, vids, etc.) and use the Ubuntu partition primarily for the OS and applications.
 
**2. Install** 

Put in the install CD and started the computer and pressed esc on boot to choose boot drive. I chose CD drive. This would be a good time to plug the ethernet adapter into your router (more to follow on this). Ubuntu Live loaded with no extra options. Once the desktop was loaded I chose "Install". Selected the option to manually edit partitions. Created 17 gig ext3 partition and 3 gig swap partition with the space allocated in Vista. Set sda3 as /, sda1 as /windows, and sda4 as swap. After that, I let the installer do it's thing.
I did receive a message about security updates not being available from security.ubuntu.com. This was because I did not have the network not hooked up, I could have avoided this by having the ethernet plugged in. The install took about 15 mins. Rebooted.
 
**3. Cleanup and Update packages** 

Now I plugged in ethernet. Because of my timing on this, I had to go in and clean up my /etc/apt/sources.list. Open terminal and: 
```
sudo gedit /etc/apt/sources.list
``` 
Removed > deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted 
Uncommented all the lines that read > Line commented out by installer because it failed to verify 
Uncommented backports and partners 
Now ```
sudo aptitude upgrade
``` (started using aptitude vs. apt-get, but that's a different story) 

**4. Wireless** 

I used this [_How-To_]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")  to get me through.
I found my wireless Card by ```
lspci | grep bcm
``` 
That returned > 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) Notice the "rev 02", so I went with step 2a 
Reboot 

After the reboot, I clicked on Network Manager and I can connect to Wireless! For some reason, sound is now muted and can't unmute - just needed to turn up volume, duh! 

Now that I can unplug my computer and go back to the couch I can move on to... 

**5. Upgrading Packages** 

Time to upgrade and see if anything gets fixed (or broken) 
```
sudo aptitude upgrade
```

Nothing broke that I can find...
 
**6. Video Card** 

I activated nVidia drivers - System > Administration > Restricted Drivers > Enable nVidia.

Reboot to activate.
 
**7. Suspend to RAM** 

Next I tried to get Suspend to work. Added noapic and nosmp to the boot loader. Played around with settings in /etc/default/acpi-support. No love. 

A little help would be appreciated. This to me is the biggest issue with this laptop and Gutsy. No Suspend/Standby on a laptop. That's just not right! 

**8. Webcam** 

Webcam seemed to work right out of the box! Went into Ekiga, under Edit > Preferences > Devices > Video Devices changed Video Plugin to V4L2 and the blue light came on! Wow! 

**9. SAMBA/WINS/WINBIND** 

I wanted to get samba and WINS up and running because most of my network is smb. Installed winbind and smbfs 
```
sudo aptitude winbind smbfs
``` 
```
sudo gedit /etc/nsswitch.conf
``` 
Changed the line to 
> hosts: files mdns4_minimal dns mdns4 wins

Now we reboot network by 
```
sudo /etc/init.d/networking restart
``` 

**10. Medibuntu** 

Medibuntu has video codecs, GoogleEarth, and other cool stuff```
 
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list 
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``` 
Installed VLC ```
sudo aptitude install vlc
``` 
Install DVD support ```
sudo aptitude install libdvdcss2 
-
``` 
Install Windows Codecs ```
sudo aptitude install w64codecs 

``` 
Install non-free Codecs ```
sudo aptitude install non-free-codecs
``` 

**11. Setup User Drive on Windows Partition for use with Ubuntu** 

I want to save Docs, Music, Vids, and others in the User directory under windows so that I can access them from both Ubuntu and Vista. I Created symlinks from my Windows Vista Users Directory Music, Videos, Pictures, and Documents folders into my Ubuntu home directory so that I could store everything on the larger Windows partition and see it no matter what I booted up.
 
```
cd ~ 
rm -r Documents 
rm -r Downloads 
rm -r Music 
rm -r Pictures 
rm -r Videos 
ln -s /windows/Users/"myloginname"/Documents 
ln -s /windows/Users/"myloginname"/Downloads 
ln -s /windows/Users/"myloginname"/Music 
ln -s /windows/Users/"myloginname"/Pictures 
ln -s /windows/Users/"myloginname"/Videos 
```

**12. Speed things up a bit** 

Tried to speed up Firefox by doing what's here [http://ubuntuforums.org/showthread.php?t=181107]("http://ubuntuforums.org/showthread.php?t=181107") 
Tried to speed up internet by doing what's here [http://ubuntuforums.org/showthread.php?t=202838]("http://ubuntuforums.org/showthread.php?t=202838")

I'm not sure either one did much.

---

### Post by j9gillik on 2008-01-11
My friend ... my dear, dear friend ...

I have this exact same model of laptop.  I love it; I dual-boot Vista and Linux Mint 4.0 Daryna (which is based on Gutsy).  

I've tried all sorts of tricks with the Broadcom drivers and Ndiswrapper -- to no avail.  But I did what you did, and now, for the first time EVER (and I've tried Kubuntu 7.10 64-bit and openSUSE 10.3), I now have working wireless.

You are my hero!!! :)

---

### Post by FriedChips on 2008-01-23
I have this laptop as well, though it is currently into HP for repair ( only six months old ) :( ... I love this laptop, the only thing that could be better, ( aside from 2 GIGS of memory which is cheap and easily doable for ~40 USD on newegg :) ) is a more powerful graphics card. HP's repair service is being really slow about the repair. The issue is with my backlight, I see only a very dim picture. Started flickering one day then boom completely gone. Anyway, happy to hear there are some other users out there.

---

