---
title: "Network Card Driver &quot;Active but not in use&quot;"
date: 2009-11-27
forum: Hardware
---

### Post by vrr on 2009-11-27
Hello,

Just installed Ubuntu on my USB-HDD.
All went well. I installed the drivers for my network card.
"Broadcom STA wireless driver"
rebooted
and I was on the internet :D
Next I installed the driver for my graphics card
"NVIDIA accelerated graphic driver (version 185) [Recommended]"
it downloaded the driver from the internet
I rebooted
but this time I was not connected to the internet
I opend the "Hardware Drivers" window and I could see that the "Broadcom STA wireless driver" was green, but it said something like "Active but not in use"
I could not figure out how to put it "in use" so I removed it and reinstalled
and it is now activated and currently in use so I'm back on line.
any ideas why I have to remove and reinstall?

TIA

---

### Post by efflandt on 2009-11-27
I had a similar problem when I used live/install iso on bootable USB on a Dell laptop.  I activated Broadcom STA and it then said I needed to reboot.  But then Hardware Drivers said it was "Activated, but not in use".  So I did **sudo depmod**, looked for the likely looking module, then **sudo modeprobe wl**.  Then it worked, but was not active on next boot.  Since I did not want to tamper with init, I just added something to live default upbuntu's .profile to sudo modprobe wl if (using grep) that specific Broadcom model was listed in lspci, and wl was not already listed in lsmod.

But I have not installed a normal working Linux system on that laptop, so I am not sure how a normal installation sets up Broadcom STA to be used automatically.

---

### Post by vrr on 2009-11-27
OK, good to know it wasn't just me.

Thanks for the info, I'm super noob and will take me some time to figure out exactly what you said.:shock:

for the record...
I am using an HP laptop.
I did not install onto my hard drive, which has windows vista.
Instead, I'm running Ubuntu on a 16 GB partition off my 1TB USB-HDD.

---

### Post by lbrooks303 on 2009-11-27
I just installed Ubuntu 9.10 on my HP Pavlion dv9620us laptop.  This machine has 2 hard drives.  I have Windows Vista on the primary drive and installed Ubuntu 9.10 on the second hard drive.  I have a dual boot system set up.  My problem is the same as the above.  I installed the Broadcom driver and was told to reboot.  I did and also got the "Active but not in use" message and did not know what to do with it.  I also removed the Broadcom driver and tried to reinstall it.  However, the system "hangs up" when it is downloading the driver and I had to shut down. I tried this several times.
Additionally, I no longer have the "wireless networking" choice from the Network Manager drop down menu just "wired networking".  
  I am new to Linux.  What should I do?
Thanks,
Preston

---

### Post by djuber on 2009-11-27
I too have the same issue. I have a native install of 9.10 on an HP dv4 laptop. It is using the broadcom 4322 wireless card. I had issues ever getting the wireless to work from 9.10, and installed 9.04, where it worked fine, then upgraded to 9.10. The wireless worked alright until a reboot. I now see the same message : active but not in use in the restricted drivers section. I am unwilling to downgrade to 9.04 due to issues with the audio output from the speaker (9.04 incorrectly routed all output to the front headphone jack). 

I understand that there was a problem in the 9.10 installer where STA drivers which worked fine under the live install ceased working after a harddrive installation. I feel like either an update or clear instructions on a work around would ease a lot of peoples pain here.

---

### Post by lbrooks303 on 2009-11-29
I found a procedure in the forums that did the following:
1.  Add the Ubuntu CD to your drive
2. Go to Settings>Repositories>Ubuntu Sofrware
3.  Check the installable from CD and close
4.  Refresh
5.  Search for "bcmwl-kernel-source
6.  Mark for installation
7.  Install
8.  Reboot

I was able to resolve the Broadcom driver hanging problem but still have "Active but not in use".

---

### Post by lbrooks303 on 2009-11-29
I followed the advice of a recent post describing the "Active but not in use" problem.  
I used the following terminal commands after downloading the "bcmwl-kernel-source from the Ubuntu installation CD.

sudo dpkg-reconfigure bcmwl-kernel-source

then

sudo modprobe -r43 ssb wl

then

sudo modprobe wl

(Being new to Linux I have no idea what these commands mean.)

My Broadcom wireless card then connected to my Linksys wireless router.  However, I could not get an internet connection.  Firefox could not find any servers.  Additionally I have to reconfigure each time I reboot to connect to the wireless router.  

Any ideas why Firefox cannot get to the net and why I have to reconfigure each boot?  I have no problem connecting to the Internet using Windows Vista with the same Broadcom wireless card and router.

---

### Post by lbrooks303 on 2009-12-01
I was able to solve the Broadcom wireless card problem using the post from "beloved88".  This user used the "readme" file from the Broadcom website for downloading the Linux Broadcom drivers found here 

                                  [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) 
 
All you are really doing is deleting the generic Linux drivers that come with the Ubuntu 9.10 distro and replace them with the genuine Broadcom driver for Linux.
It works great!  Thanks Beloved88!
The only problem I have now is that I have to type 

sudo modprobe wl

in the terminal on each startup.  How can I persist this command on each boot?
Thanks again to all!
Preston

---

### Post by ZadokAllen on 2010-03-25
I registered this account to say THANK YOU.

---

### Post by Rytron on 2010-08-18
Could you post a quick guide to installing the 32-bit drivers at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) for Ubuntu 10.04? Thanks.

---

### Post by frankgirard903 on 2010-09-20
I took "lbrooks" advice and entered 'sudo modprobe wl' in the Terminal. My Linksys WEC 600N wireless card (Broadcom BCM4328) immediately activated. Like a later post, I would like to have the card come up on startup. How can I do that? Thanks.

---

### Post by frankgirard903 on 2010-09-20
I took "lbrooks" advice and entered 'sudo modprobe wl' in the Terminal. My Linksys WEC 600N wireless card (Broadcom BCM4328) immediately activated. Like a later post, I would like to have the card come up on startup. How can I do that? Thanks.

---

### Post by grejanter on 2011-04-21
Hey guys, I have this problem with the driver being enabled but not active, I do the sudo modprobe wl and I get this:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting wl (/lib/modules/2.6.35-28-generic/updates/dkms/wl.ko): Invalid argument


Any ideas how to fix ?

---

### Post by MZBKA on 2011-05-01
> **grejanter said:**
> Hey guys, I have this problem with the driver being enabled but not active, I do the sudo modprobe wl and I get this:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting wl (/lib/modules/2.6.35-28-generic/updates/dkms/wl.ko): Invalid argument


Any ideas how to fix ?

I have the same problem.  Is there any solution?

---

