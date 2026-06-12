---
title: "Wifi on Acer ASpireOne, wrestling n00b"
date: 2009-01-14
forum: Hardware
---

### Post by Modred189 on 2009-01-14
OK, first and foremost, I am a complete Linux noob. 
However, I would like to try and get Ubuntu up and running on my AAO. So far, so good, 8.10 is installed and working well, but the wireless refuses to get up and working. 
After installing Ubuntu, I began following the instructions here:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
So I make sure I am doing it right, let me recap.
First, I open the terminal and copy :
wget [http://snapshots.madwifi-project.org/ma](http://snapshots.madwifi-project.org/ma) ... ent.tar.gz
and let it do it's thing. 

Then I enter the following into the terminal:
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/

And then finally:
make
sudo make install
modprobe ath_pci

Once these have finished, nothing seems to have changed. SO I continue and enter the following:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci

However, as it runs it's little thing, when it gets to 'fuse', the next line is 'bash: fuse: command not found'
and after lp, the line reads 'lp: Error- no default destination available.'
Then when I try to get the LED's working, the above page says to 'create /etc/pm/sleep.d/00wireless', but when I try to create it in that folder, I am told I do not have permission.

HELP!

---

### Post by sp0nge on 2009-01-14
Please go to the terminal and enter:
```
lspci
```

Then paste the output here for review.

---

### Post by Modred189 on 2009-01-14
Spits out:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

---

### Post by timcredible on 2009-01-14
it's much simpler, go into synaptic and install linux-backports-module and reboot.  i thought i had got those instructions from the community page you referenced, but i don't find them anymore, they've changed to that convoluted method you outlined, or i found the info somewhere else.  anyway, i think this is all i did to get 8.10 wireless working on my granddaughter's acer aspire one.  if not, you might also have to blacklist the atheros card that 8.10 originally thinks it is.

---

### Post by Modred189 on 2009-01-14
Thanks for the input, tim, but I have no idea what that means.  :oops:
Is it easy to do? How?

---

### Post by Modred189 on 2009-01-15
Morning Bump for a n00b!

---

### Post by doug1212 on 2009-01-15
Hi, I have just go the wireless running for someone on an AAO, there are two ways to go with it, you can enable backports and install the ath5k or the way you are describing which is to build madwifi ath_pci from source.

I went with the ath_pci as described here:

[HTML]https://help.ubuntu.com/community/AspireOne110L[/HTML]

Now comes my divergence, I used wicd for the network manager as I find it far more reliable than the Gnome one.
Instructions for adding the repo are found here:

[HTML]http://wicd.sourceforge.net/download.php[/HTML]

If you do build the driver leave source directory on the machine as you will have to rebuild after kernel upgrades.

Good luck
Doug.

---

### Post by Modred189 on 2009-01-19
Again, I am sorry, but as a non-coder, none of that makes any sense to me.

---

### Post by doug1212 on 2009-01-23
ok, run it past me again where you are up to.

You have compiled the latest madwifi driver from source, yes?
have you blacklisted ath_hal by editing:

```
sudo nano /etc/default/linux-restricted-modules-common
```

and adding the line:

```
DISABLED_MODULES="ath_hal"
```

to the end of the file.

Doug.

---

### Post by appzattak on 2009-01-23
did you get this to work? If not let me know. I got mine to work yesterday.

---

### Post by Modred189 on 2009-01-23
ok, doug first.
I typed in the sudo... common line you gave, which brought up a screen saying "This file is sourced....yada yada...

Now, "madwifi ltm wl" is listed first. 
Now, at the botoom, there is a line that looks like this:
```
DISABLED_MODULES=""
```
SO I placed ath_hal in between the quotes. But what do I do to save that?

---

### Post by Modred189 on 2009-01-23
> **appzattak said:**
> did you get this to work? If not let me know. I got mine to work yesterday.

WHat did you do to get it to work?

Also, these instructions will work for kubuntu as well, right?

---

### Post by stchman on 2009-01-23
> **Modred189 said:**
> OK, first and foremost, I am a complete Linux noob. 
However, I would like to try and get Ubuntu up and running on my AAO. So far, so good, 8.10 is installed and working well, but the wireless refuses to get up and working. 
After installing Ubuntu, I began following the instructions here:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
So I make sure I am doing it right, let me recap.
First, I open the terminal and copy :
wget [http://snapshots.madwifi-project.org/ma](http://snapshots.madwifi-project.org/ma) ... ent.tar.gz
and let it do it's thing. 

Then I enter the following into the terminal:
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/

And then finally:
make
sudo make install
modprobe ath_pci

Once these have finished, nothing seems to have changed. SO I continue and enter the following:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci

However, as it runs it's little thing, when it gets to 'fuse', the next line is 'bash: fuse: command not found'
and after lp, the line reads 'lp: Error- no default destination available.'
Then when I try to get the LED's working, the above page says to 'create /etc/pm/sleep.d/00wireless', but when I try to create it in that folder, I am told I do not have permission.

HELP!

I have a tutorial to install Intrepid on an Acer Aspire One with a hard drive.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

Works very well on my AA1.

---

### Post by Modred189 on 2009-01-23
Thanks, all, for your help. I ended up following these directions here:
[http://ubuntuforums.org/showthread.php?t=1012973](http://ubuntuforums.org/showthread.php?t=1012973)
And I am up and working. Thanks again!

---

