---
title: "Intel Ethernet Card not recognized"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by Flux45 on 2009-09-26
Greetings,
I recently installed Unbuntu 9.04 on an external hard drive and it seems to not be recognizing my Ethernet card. I have (what windows reports to be) an Intel Pro 1000 PL card that is embedded on a D975BX2 motherboard (intel quad core 975 processor). I have looked at many threads regarding this issue, and was ultimately led to Intel's download website [http://downloadcenter.intel.com/Default.aspx](http://downloadcenter.intel.com/Default.aspx) where they have many linux drivers but none for the Pro 1000 PL. 
Is there something simple I am missing. I am linux semi-noob, first home install, but use it frequently at school. 

my output from lspci is as follows:

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
03:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
04:00.0 Multimedia audio controller: Creative Labs SB X-Fi
04:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

my output from ethtool -i eth0 is : cannot get driver information, no such device. 
this is the case for ethx where x is any value. 

someone please help me out with this!! iv spent hours researching for myself but have come up with nothing.

thank you

---

### Post by Flux45 on 2009-09-26
*bump*
anyone?

---

### Post by presence1960 on 2009-09-26
[http://ubuntuforums.org/showthread.php?t=868077](http://ubuntuforums.org/showthread.php?t=868077)

---

### Post by rreese6 on 2009-09-26
Linux sees the controller as an 82573L Gigabyte Ethernet Controller.
here is the driver file download 
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2198&lang=eng")

---

### Post by Flux45 on 2009-09-26
i followed the directions on the link and issued commands

sudo modprobe -r e1000
sudo modprobe e1000 eeprom_bad_csum_allow=1

and get back

FATAL: error inserting e1000 (/lib/modules/2.6.28-11-generic/kernal/drivers/net/e1000/e1000.ko): Unknown symbol in module, or unknown parameter

then ran simply sudo modprobe e1000 and it returned without feedback...still no changes as far as i can tell...

---

### Post by presence1960 on 2009-09-26
> **Flux45 said:**
> i followed the directions on the link and issued commands

sudo modprobe -r e1000
sudo modprobe e1000 eeprom_bad_csum_allow=1

and get back

FATAL: error inserting e1000 (/lib/modules/2.6.28-11-generic/kernal/drivers/net/e1000/e1000.ko): Unknown symbol in module, or unknown parameter

then ran simply sudo modprobe e1000 and it returned without feedback...still no changes as far as i can tell...

I did a search for that link. Try rreese6's link it is a driver for your card.

---

### Post by rreese6 on 2009-09-26
Follow my link download driver then
run the attached module script after you remove the ".txt" at the end. then reboot

---

### Post by Flux45 on 2009-09-26
so i download the driver linked and attempted to install with intel's readme instructions

when i make install on the drivers it comes back with a permission denied error

install: cannot remove /lib/modules/2.6.28-11-generic/kernel/drivers/net/e1000e/e1000e.ko Permission Denied

no idea what to do now

---

### Post by rreese6 on 2009-09-26
```
sudo make install
```

btw if it works with out the script, don't run it. the script basically detects when the wire is plugged in without rebooting if you don't have it plugged in doing boot. I had to use it on my main system

---

### Post by Flux45 on 2009-09-26
> **rreese6 said:**
> Follow my link download driver then
run the attached module script after you remove the ".txt" at the end. then reboot

wait, so I should not have tried to install the driver via intel's site? because that failed me

---

### Post by Flux45 on 2009-09-26
nevermind...im stupid

---

### Post by rreese6 on 2009-09-26
ok

---

### Post by Flux45 on 2009-09-26
> **rreese6 said:**
> ```
sudo make install
```btw if it works with out the script, don't run it. the script basically detects when the wire is plugged in without rebooting if you don't have it plugged in doing boot. I had to use it on my main system


ok...i did sudo make install and get:

cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode e1000e

---

### Post by rreese6 on 2009-09-26
close the terminal, open a new one and follow the instructions again.

in the readme file where it says:
" Compile the driver module:

     # make install"

the # means that you root, for ubuntu we use sudo at the $ prompt,
so at that step type sudo make install.

---

### Post by rreese6 on 2009-09-26
Oh and use modprobe not insmod
insmod would mean that you have to do this every time the kernel is updated.
you can add the options to /etc/modprobe.d/modules if need be, but we will do that later if necessary.

---

### Post by Flux45 on 2009-09-26
deleted all files, redownloaded, restarted, unpacked and reinstalled...
still same error message as before

---

### Post by Flux45 on 2009-09-26
anyone else have any suggestions?

---

### Post by rreese6 on 2009-09-27
of course since modprobe does not want to take the options. 
```
cd /etc/modprobe.d
sudo touch e1000
sudo nano e1000

```
once in nano add this line:
```
options eeprom_bad_csum_allow=1

``` then CTRL X to exit, save buffer Y
and enter.
then
```
sudo modprobe -r e1000
sudo modprobe e1000

```
then change directory to where you downloaded my script.
```
sudo ./e1000-mod-script
```
it will tell you to reboot
this should work, I just uninstalled my module on my main system and did this and it works.

If anyone else sees an error in my post please PM me and advise here...Thanks

---

### Post by Flux45 on 2009-09-27
> **rreese6 said:**
> of course since modprobe does not want to take the options. 
```
cd /etc/modprobe.d
sudo touch e1000
sudo nano e1000

```once in nano add this line:
```
options eeprom_bad_csum_allow=1

``` then CTRL X to exit, save buffer Y
and enter.
then
```
sudo modprobe -r e1000
sudo modprobe e1000

```then change directory to where you downloaded my script.
```
sudo ./e1000-mod-script
```it will tell you to reboot
this should work, I just uninstalled my module on my main system and did this and it works.

If anyone else sees an error in my post please PM me and advise here...Thanks

ok to sum up, im going to, after entering sudo -s and using e1000e instead of e1000e (is this ok? the intel installer README says it is using e1000e):

```
tar zxf e1000e-x.x.x.tar.gz

cd e1000e-x.x.x/src/

make install

cd /etc/modprobe.d

touch e1000e

nano e1000e

options eeprom_bad_csum_allow=1

CTRL X

save buffer y? do i have to do anything here?

rmmod e1000e

modprobe e1000e
```so after I do this, u suggest running the script, however, do you think this will be effective since I seem to be using e1000e throughout the install...

---

### Post by Flux45 on 2009-09-27
> **rreese6 said:**
> Follow my link download driver then
run the attached module script after you remove the ".txt" at the end. then reboot

also for this file (if i end up needing it, which it looks like i do) do i need to ADD and extension or just run it with ./e1000-mod-script

---

### Post by Flux45 on 2009-09-27
ALLLLSO (sorry for flooding my own thread) do i need to do anything similar to

sudo apt-get install linux-headers-generic
iv been doing a lot of reading and many people suggest this as a part of the process but never really explain why

---

### Post by rreese6 on 2009-09-27
The script should not have an extension, I put ".txt" on it so I could post it here.

Remember that some of the commands need sudo in front of them, from your list you made you left sudo off of some of the lines, like make install

---

### Post by Flux45 on 2009-09-27
im sorry for my total noob-ness, like i said its my first real experience with Ubuntu. I really appreciate that you are taking the time to help me out. After running through the steps I still have not had success unfortunatly. Hopefully you can read my console I/O and see exactly what is going on. Im anxious to get this fixed and hope we can get this solved tomorrow.
```

matt@matt:~/Desktop$ tar zxf e1000e-1.0.2.5.tar.gz
matt@matt:~/Desktop$ cd e1000e-1.0.2.5/src
matt@matt:~/Desktop/e1000e-1.0.2.5/src$ sudo make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/matt/Desktop/e1000e-1.0.2.5/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/netdev.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/ethtool.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/param.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_82571.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_ich8lan.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_80003es2lan.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_mac.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_nvm.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_phy.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000_manage.o
  CC [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/kcompat.o
  LD [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/matt/Desktop/e1000e-1.0.2.5/src/e1000e.mod.o
  LD [M]  /home/matt/Desktop/e1000e-1.0.2.5/src/e1000e.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
gzip -c ../e1000e.7 > e1000e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.28-11-generic -name e1000e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-11-generic -name e1000e.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000e.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/e1000e/e1000e.ko
/sbin/depmod -a || true
install -D -m 644 e1000e.7.gz /usr/share/man/man7/e1000e.7.gz
man -c -P'cat > /dev/null' e1000e || true
man: 
cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode
e1000e.
matt@matt:~/Desktop/e1000e-1.0.2.5/src$ cd /etc/modprobe.d
matt@matt:/etc/modprobe.d$ sudo touch e1000
matt@matt:/etc/modprobe.d$ sudo nano e1000

AT THIS POINT NANO OPENS AND I INSERT THE OPTION EEPROM_BAD_CSUM_ALLOW=1 LINE SUGGESTED. CTRL X, SAVE, SAVE AS E1000

matt@matt:/etc/modprobe.d$ sudo modprobe -r e1000
WARNING: All config files need .conf: /etc/modprobe.d/e1000, it will be ignored in a future release.
WARNING: /etc/modprobe.d/e1000 line 1: ignoring bad line starting with 'options'
matt@matt:/etc/modprobe.d$ sudo modprobe e1000
WARNING: All config files need .conf: /etc/modprobe.d/e1000, it will be ignored in a future release.
WARNING: /etc/modprobe.d/e1000 line 1: ignoring bad line starting with 'options'
matt@matt:/etc/modprobe.d$ cd /home/matt/Desktop/
matt@matt:~/Desktop$ ./e1000-mod-script
Usage: ./e1000-mod-script \<interface\>
       i.e. ./e1000-mod-script eth0
matt@matt:~/Desktop$ ./e1000-mod-script eth0
eth0: error fetching interface information: Device not found
matt@matt:~/Desktop$ ./e1000-mod-script eth1
eth1: error fetching interface information: Device not found
matt@matt:~/Desktop$ ./e1000-mod-script eth2
eth2: error fetching interface information: Device not found
```

---

### Post by rreese6 on 2009-09-27
Flux, Thank you for posting the output. there are things in your that are different than mine. I investigated my server and noticed that my interface is using e1000 whereas it appears that your will need to have the e1000e. So what we will do tomorrow is remove some of what we have done and reconfigure for the e1000e driver. Evidently you have a newer revision Ethernet port than I have.
I will give you some commands now to begin with.
```
cd /etc/modprobe.d
sudo rmmod e1000
sudo rmmod e1000e
sudo rm e1000

``` more to follow

---

### Post by rreese6 on 2009-09-27
At one time the ethernet did not work because it was disabled in 8.10 pre-release.
Check the output of the blacklist
```
 cd /etc/modprobe.d
less blacklist |grep blacklist

```
We are looking to see if the e1000e is listed there. If it isn't we will continue.
if it is there then the bug is not fixed and the interface has been disabled to protect your hardware.
if it is blacklisted, then you will need to get another NIC (Network Interface Card).

---

### Post by rreese6 on 2009-09-27
We are here because the driver is not blacklisted (see previous post)
I am assuming you are running Ubuntu 9.04?
Make sure you have the Kernel Headers
```
sudo apt-get install linux-headers-generic
```
If that was not already in the system.
Check to make sure the driver is still there
```
 ls /lib/modules/$(uname -r)/kernel/drivers/net/e1000e
```
if it is, continue, otherwise we will reinstall it

```
sudo rmmod e1000e
sudo modprobe e1000e 
sudo nano modprobe.conf
```
in nano add this line:
```
alias eth0 e1000e[/CODE
exit (CTRL X) and save

Restart the network
[CODE]sudo /etc/init.d/networking restart
```
Check for the interface
```
 ifconfig -a
```

---

### Post by rreese6 on 2009-09-27
Hi Flux45, let's start at post #25 today..

---

### Post by Flux45 on 2009-09-27
morning rreese, up bright and early i see...
here is the console output from said commands

```
matt@matt:~$ sudo apt-get install linux-headers-generic
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matt@matt:~$ ls /lib/modules/$(uname -r)/kernel/drivers/net/e1000e
e1000e.ko
matt@matt:~$ sudo rmmod e1000e
matt@matt:~$ sudo modprobe e1000e
matt@matt:~$ sudo nano modprobe.conf
matt@matt:~$ /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
                                                                         [fail]
matt@matt:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 6e:87:1c:59:9a:8d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

matt@matt:~$ 
```

---

### Post by rreese6 on 2009-09-27
Yes I was up very late and early :)
LOL I made a mistake...this time I forgot sudo....

here is the network restart
```
sudo /etc/init.d/networking restart
```

then do the ifconfig -a again

---

### Post by Flux45 on 2009-09-27
looks like maybe some progress was made...i still have no connection though

```
matt@matt:~$ ls /lib/modules/$(uname -r)/kernel/drivers/net/e1000e
e1000e.ko
matt@matt:~$ sudo rmmod e1000e 
matt@matt:~$ sudo modprobe e1000e
matt@matt:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
matt@matt:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 4e:6d:e8:0b:8e:46  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

matt@matt:~$ 
```

---

### Post by rreese6 on 2009-09-27
ok well we did get further. Try to unplug your ethernet cable for 20 seconds, then plug it back in. wait 15 seconds then do another ifconfig -a
the driver sould have fixed a problem about unplugging and replugging the cable..
I take it you did not see e1000e in the blacklist.

---

### Post by Flux45 on 2009-09-27
> **rreese6 said:**
> Do you have instant messenger (AIM or Pidgin)
If you do lets take this live to work it faster.
my user name is **

ok well we did get further. Try to unplug your ethernet cable for 20 seconds, then plug it back in. wait 15 seconds then do another ifconfig -a
the driver sould have fixed a problem about unplugging and replugging the cable..
I take it you did not see e1000e in the blacklist.

i dont have any form of IM...i have a google and MSN account but dont have any clients downloaded...do u have MSN or google talk (or iChat)

---

### Post by rreese6 on 2009-09-27
I will get on to MSN then we will post the solution here later

---

### Post by Flux45 on 2009-09-27
im online...

---

### Post by rreese6 on 2009-09-28
This problem was not being solved by all the normal methods because the e1000e driver kept failing during boot up.

Machine is running Ubuntu 9.04, fully updated.

The Device on this machine (from lspci command) showed:
Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

The output from 
```
dmesg |tail -n20
```
showed us that the driver was aborting during boot up
with a "NVM Checksum" error

Because the Driver was failing, it would not assign a MAC or IP address.

The Interface worked in Windows Vista because Vista does not check the NVM Checksum.

We knew the interface worked...but the NVM (EEPROM) had corrupted data. No other Linux with an earlier Kernel had ever been loaded on this machine. Current Kernel is 2.6.28-11-generic.

We downloaded the latest driver file from Intel: e1000e-1.0.2.5.tar.gz
to the user's desktop then moved it to /usr/local/src.
```
cd ~/Desktop
sudo mv e1000e-1.0.2.5.tar.gz /usr/local/src
```

Extracted it and changed to the src directory inside the new drive directory (e1000e-1.0.2.5).
```
sudo tar zvh e1000e-1.0.2.5.tar.gz
cd e100e-1.0.2.5/src
```

We followed the readme file and did the "sudo make install" removed the old driver (sudo rmmod e100e), and loaded the new one (modprobe e1001e). Rebooted the machine...and and.....
Nothing, the same error in the Dmesg list.

I decided it was time to hack somethng, but what?

THE WORK-AROUND:

I found a file in the /usr/local/src/e1000e-1.0.2.5/src directory called netdev.c
I opened it with ```
sudo gedit netdev.c
```
and searched (CRTL F in gedit) for "NVM Checksum". 
Once I found where NVM Checksum was I deleted two lines of code and saved the file. The code looked like this when i found it:
```
if (i == 2) {
	e_err("The NVM Checksum Is Not Valid\n");
        err = -EIO;
        goto err_eeprom;
      }
```
I changed to code by removing two lines and add "break;in their place:
```
if (i == 2) {
	e_err("The NVM Checksum Is Not Valid\n");
      break;
      }
```
Saved the file then ran make clean and make install:
```
sudo make clean
sudo make install
```

Then we changed to the /etc directory and created modprobe.conf
```
cd /etc
sudo nano modprobe.conf
```
once in nano we added this line: 
```
alias eth0 e1000e
```
then used CTRL X to exit, Y to save and ENTER

Next:
Removed the old module and installed the new one:
```
sudo rmmod e1000e
sudo modprobe e1000e
```
The ethernet came up and was working. we checked the HWaddr (MAC) with ifconfig -a and it was the same as windows had seen.

It was working, however after a reboot, it did not work and a new error showed up in the dmesg output.
......I had read some about the error we saw, but decided the do the rmmod and modeprobe again and the ethernet came up and worked.

LAST ITEM
At this point we decided it was time just to write a script and have it run during boot up. Basically removing the module and reinserting it.
(I know it's not clean, but it is working)
Created a script:
```
cd /etc/init.d
sudo nano eth_start
```
and added the following to it.
```
#!/bin/bash 
rmmod e1000e && modprobe e1000e
```
CTRL X to exit, Y to save and ENTER.
Back at the prompt we added it to the bootup
```
sudo update-rc.d eth_start
sudo chmod +x /etc/init.d/eth_start
```

Now every time the machine boots up, the module is unloaded and reloaded...but the main point is that the ethernet is working, at least in our case.
This did not really cause us any more problems, since the error with the NVM Checksum seemed to have come this way on the new Motherboard.
A very strange problem.. I guess we could have redone the checksum and such, but that would have taken more time and best left to the real experts of Linux.

We could not find much about the model(82573L) but we did see that many people were hard at work fixing the bugs since they started in the 2.6.27-rc1 Kernel. Their work and notes helped us understand the issue much better...
Kudos the the SourceForge Group e1000 and to Intel Engineers for getting involved.
[http://sourceforge.net/projects/e1000/support](http://sourceforge.net/projects/e1000/support)

Please PM me or leave a message here if you see any errors or omission
in this post...it was a long couple of days on this one and I am sure it was a unique problem since this motherboard has never seen Linux before 9.04.

---

### Post by Flux45 on 2009-09-28
confirmed SOLVED, was a headache to fix. thanks to rreese6 for is relentless efforts and walking me through the entire process...! writing this from my linux box as we speak!!
thanks again

---

### Post by crati on 2009-10-17
First thanks a lot for finding the solution for this problem. I just installed in a thinkpad T60 laptop ubuntu 9.04  and had exactly the same problem. Your solution fixed it in the same way as you described.
One small thing, when doing:
$sudo update-rc.d eth_start
usage: update-rc.d [-n] [-f] <basename> remove ....

That is, it seems to need to have expecified start|stop or defaults to add the script.
I just run it with defaults assuming that is correct and at least after the first restart it worked.
Im also quite new to this. But one think I noticed is that before adding this script to the init, lsmod was showing the old driver (at least the old size, around 120.000) after the restart, while after taking out the module and installing the new one it was showing a size of 140716 for it.
So just the old module is loaded after each restart, and the eth_start script is unloading it and loading the new one. 
Just in case someone knows how to override the module that is initially loaded, instead of reloading after the replacement.

Anyway, just for the record, in my case the Intel driver version I downloaded was the 1.0.15.

---

### Post by Blario on 2009-11-15
Is compiling the driver from intel completely necessary? Can these steps work if the driver included in the latest ubuntu kernel is used instead? 

Thanks.  I have this problem, been upgrading from release to release from hardy heron since yesterday... and i'd like to skip some steps if I can...

---

### Post by Blario on 2009-11-15
That was a dumb question. Yes, of course the source code is necessary in order to change the source code....

I just ran through the steps and they work! (actually I'm about to reboot & make sure, but right now my gigabit is working...) 
This was referred to as a hack, but actually it seems to be EXACTLY what the windows driver for this card does.  Windows doesn't care... I'm probably missing something but for most users, Linux doesn't have to care either.  

Anyway, until the driver is repaired to where it can fix the NVM checksum that it so badly cares about, I recommend that this gets included in the e1000e driver that ships with all ubuntu kernels as soon as possible. I first hit this problem in late 2007 with Gutsy Gibbon. If I new C better, maybe I could have fixed it, but I seriously doubted my skills at the time. There have to be many others facing this issue. I'm shocked canonical staff haven't hit this, since the T60 laptop (which has this chip) is soo commmon in the work place... Usually thinkpads work pretty well with linux distros due to the paid staff usually have them & fix those problems first.

Thanks so much! I now have gigabit after going 2 years with out...

---

### Post by huangzhe678 on 2010-11-23
I face the same problem.
tried all these above, it still does not work. when I reboot my computer, and exe 'rmmod e1000e', it tell me 'there is no module named e1000e'. what is the reason? I am so confused. Appreciate your suggestions.

---

### Post by mhgsys on 2010-11-29
> **rreese6 said:**
> WORK-AROUND 

Thank you for posting this workaround, 
Thnx to your post I was able to help a friend of mine who did not have wired internet for over a year.

Works beautiful now.

---

### Post by Silentzor on 2011-07-05
Thanks a lot for this thread, i managed to get ethernet to work on my old HP laptop.

---

