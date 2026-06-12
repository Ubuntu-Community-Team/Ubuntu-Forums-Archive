---
title: "Ubuntu 8.04  - Broadcom wireless not working"
date: 2008-04-25
forum: Hardware
---

### Post by digisoft on 2008-04-25
Hi,
I installed the latest release on my Gateway MX6453 laptop and everything installed perfect but I can't seem to get the wireless to work. I am new to Ubuntu but I did try something I found in another thread and I'm posting it below in hopes it will help. Everything else works perfect, but I really need to get the wireless working so I can finally remove Microsloth winblows. Any help would be greatly appreciated.

WPA personal
TKIP
shared key: *********
  	 
Mode:  	 Mixed  	  	 
SSID:  	 ByteMe  	  	 
DHCP Server:  	 Enabled 	  	 
Channel:  	 6 




owner@owner-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

owner@owner-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by Patsoe on 2008-04-25
Which Broadcom model is it? Did you manage to get the firmware installed?

---

### Post by digisoft on 2008-04-25
I'm not sure which broadcom, in windows hardware manager it says broadcom 802.11g. I've looked on the gateway site and they don't say what model broadcom this is. 

Also, how do I install firmware? it never asked me to install firmware.

---

### Post by adult swim on 2008-04-25
to determine what broadcom card you have type this in a terminal, post your output
```
lspci | grep Broadcom\ Corporation
```

---

### Post by ScoobyDooobyD00 on 2008-04-25
Hi, I'm having the same problem... My wireless card is a 

```

Broadcom 440x 10/100 Intergrated Controller

```

I don't understand how the terminal works ect. (I just got Ubuntu today) so please tell me what I need to type into the terminal.

Thanks in advance

---

### Post by adult swim on 2008-04-25
sorry about that!  go to your taskbar, where it says applications, then choose accessories and finally Terminal.
open that up and copy and paste the command in the terminal and hit enter.  it will spit you out some data, copy that and paste it here.

---

### Post by digisoft on 2008-04-25
lspci | grep Broadcom\ Corporation

owner@owner-laptop:~$ lspci | grep Broadcom\ Corporation
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

No worries, I knew how to run terminal :)

---

### Post by MRiGnS on 2008-04-25
I guess b43-fwcutter isn't working with this model, is it?

---

### Post by adult swim on 2008-04-25
> **digisoft said:**
> lspci | grep Broadcom\ Corporation

owner@owner-laptop:~$ lspci | grep Broadcom\ Corporation
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

No worries, I knew how to run terminal :)

you've got two options, you can use the b43-fwcutter package via the hardware drivers (formerly known as restricted drivers manager)  or you can use ndiswrapper.  the b43-fwcutter will be the easiest but it only is capable of 10-15 MB/s (im not fully sure on these numbers, but i know for a fact it wont get 54 MB/s.) if you want to use the b43-fwcutter package from a terminal ```
sudo dpkg-reconfigure b43-fwcutter
```
if you want to use ndiswrapper i would suggest this guide, [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) (at the part that says ndiswrapper -m you dont have to do that ) followed by this guide [http://ubuntuforums.org/showthread.php?t=734003&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=734003&highlight=ndiswrapper)

---

### Post by digisoft on 2008-04-25
ok, I'll try the b43-fwcutter first to egt it working, then I can play with the other one once I have internet access so I don't have to reboot into windows to get the info, copy it to a USB drive and then boot back into linux. I'm running dual boot right now until I can be sure that Ubuntu will work 100% on my laptop. I'll also be configuring wither WINE or using that software (can't recall the name) that allows me to install windows XP inside of linux so I can run a few apps that are not made for linux. BRB, I'll reboot and try it now...

and thanks!

---

### Post by digisoft on 2008-04-25
owner@owner-laptop:~$ sudo dpkg-reconfigure b43-fwcutter
[sudo] password for owner: 
Package `b43-fwcutter' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: b43-fwcutter is not installed
owner@owner-laptop:~$

I tried going to add/remove programs and did a search for b43-fwcutter but it didn't find it. So here I am back in windows, lol

---

### Post by adult swim on 2008-04-25
easy fix!  you can download the package here
[http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)
if youve got a pen drive or something like that throw it on there and load up ubuntu and double click the package

---

### Post by digisoft on 2008-04-25
I found it on the CD and installed it through synaptics (sp)? 

b43-fwcutter: subprocess post-installation script returned error exit status 1

now what? lol

---

### Post by adult swim on 2008-04-26
several people have reported this to work, ive never tried it though!
since you cant connect to the internet with your ubuntu install, you'll need to go to [http://bu3sch.de/b43/fwcutter](http://bu3sch.de/b43/fwcutter) and download b43-fwcutter-011.  next go to [http://downloads.openwrt.org/sources](http://downloads.openwrt.org/sources) and download broadcom-wl-4.80.53.0.tar.bz2.  save these on something that you can access with your ubuntu install, disk, pen drive, etc. boot up ubuntu and place both of the files you downloaded into your home folder.  
now you will need to use the synaptics package manager via cd and install the build-essential package, the same way you installed the b43-fwcutter package that didn't work earlier.  
now you can get to work
from a terminal, one line at a time ```
tar xjf b43-fwcutter-011.tar.bz2

cd b43-fwcutter-011

make

cd

export FIRMWARE_INSTALL_DIR=&#8221;/lib/firmware&#8221;

tar xjf broadcom-wl-4.80.53.0.tar.bz2

cd broadcom-wl-4.80.53.0/kmod

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```

now you will need to restart
if your wireless isnt on, go to system/administration/hardware drivers and make sure that the b43 driver box is checked.

---

### Post by azulojos84 on 2008-04-26
Hi, I had similar problems here is the simple fix I stumbled upon

1. Make sure you are plugged into a wired network and make sure the connection is working (you can check with System/Administration/Network) 

2. Go to System/Administration/Hardware Drivers and see if it has firmware support available for your card (for example mine stated Broadcom B43 wireless diver in use or something similar.) make sure to check the box and wait for it to download the firmware from the repository)

3. After it has installed the firmware make sure it make sure it installed fw cutter and ask it to extract the firmware.

4. download and install ndiswrapper from the Add/Remove application

5. download the appropriate driver for your card from the list on the ndiswrapper website the link is [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

6. what I did at this point was install the exe file on a windows system and then copy the folder over. With some of these files you should be able to unpack the exe with archive manager. 

7. Once you have the files simply use System/Administration/windows wireless drivers and select the .inf file from your wireless driver folder that you unpacked. 

That worked for me I hope it Helps

---

### Post by digisoft on 2008-04-26
I got an error after this one:

sudo ../../b43-fwcutter-011/b43-fwcutter -w &#8220;$FIRMWARE_INSTALL_DIR&#8221; wl_apsta.o

I thought I saved it to the file on my USB drive, but for some reason I must have missed because its not there now. The error was something about not being able to find the directory. I have to reboot into Ubuntu to run it again to get the error again so I'll reboot and grab it and BRB...

Thanks!


PS azulojos84 I don't have a network cable handy or I'd try that, the last cable I had died and I haven't got around to getting another one yet.

---

### Post by adult swim on 2008-04-26
if either of the files was misplaced, you would have gotten errors everywhere
lets try cutting out the variable

try this
```
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```

---

### Post by digisoft on 2008-04-26
This is the error I got, I'll try the new way you just posted and BRB...


owner@owner-laptop:~$ cd broadcom-wl-4.80.53.0/kmod
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$ sudo ../../b43-fwcutter-011/b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to create output directory: No such file or directory
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$

---

### Post by digisoft on 2008-04-26
OK, I went back and tried what yo said (at least I think I got it right) and then I tried a couple other things just to see if I could get it to work, below is the output from the terminal.


owner@owner-laptop:~$ sudo ../../b43-fwcutter-011/b43-fwcutter -w “/lib/firmware” wl_apsta.o
[sudo] password for owner: 
sudo: ../../b43-fwcutter-011/b43-fwcutter: command not found
owner@owner-laptop:~$ cd broadcom-wl-4.80.53.0/kmod
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$ sudo ../../b43-fwcutter-011/b43-fwcutter -w “/lib/firmware” wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to create output directory: No such file or directory
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$ sudo ../../b43-fwcutter-011/b43-fwcutter -w “/lib/firmware” wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to create output directory: No such file or directory
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$ sudo ../../b43-fwcutter-011/b43-fwcutter -w wl_apsta.o
b43-fwcutter version 011

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: ../../b43-fwcutter-011/b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$ ls
wl_apsta_mimo.o  wl_apsta.o
owner@owner-laptop:~/broadcom-wl-4.80.53.0/kmod$

---

### Post by adult swim on 2008-04-26
it looks like the answer may be in your error message at the very end! "Example: ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
to extract the firmware blobs from wl_apsta.o and store
the resulting firmware in /lib/firmware"
try ```
cd broadcom-wl-4.80.53.0/kmod

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```

if you get no errors, youll need to restart ubuntu for it to work

---

### Post by digisoft on 2008-04-26
I figured out my mistake at the end, I was forgetting the sudo, once I noticed my mistake the last one worked and the command completed successfully. I rebooted and then I looked in admin/hardware and saw that the driver was in use, but still no internet connection.

I went back and verified that the network was set to WPA - personal and that my password was correct and it was. So now the drivers are installed, but no connection yet. With a little luck we are getting closer :)

---

### Post by adult swim on 2008-04-26
good deal! run from terminal and post your output
```
sudo iwlist scanning
```

---

### Post by digisoft on 2008-04-26
ok, BRB....

---

### Post by adult swim on 2008-04-26
> **digisoft said:**
> ok, BRB....

i keep forgetting you have to reboot 2 times every time! we really need to get your wireless working!

---

### Post by digisoft on 2008-04-26
here ya go, once I get it working I'll have to do it all over again because I plan on wiping the drive to remove XP and run only Ubuntu on my laptop, I just need to make sure I can get the network going and also see if either Wine or? will let me run a couple windows apps I need.


owner@owner-laptop:~$ sudo iwlist scanning
[sudo] password for owner: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:A0:4E:9C
                    ESSID:"ByteMe"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=91/100  Signal level=-42 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000005f657253aa
          Cell 02 - Address: 00:14:BF:F0:3A:8B
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal level=-79 dBm  Noise level=-71 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000030b9a2187

owner@owner-laptop:~$

---

### Post by adult swim on 2008-04-26
hmm, go to system/adminstration/network and click the unlock button.  then go to wireless and see if the roaming mode is enabled.  see if you can connect to byteme after that.  ive got to go to sleep for now but i will search for a solution to get you up and running if this doesnt work.  
as far as having to do this again, you wont have to do that if you get the gparted live cd.  you can boot from it and delete your windows partition and then expand your ubuntu partition to fill out the whole drive.  ill chekc this thread in the morning to see how it goes!  good luck

---

### Post by digisoft on 2008-04-26
I know roaming is not enabled, should I enable it? and yeah, I need sleep too, thanks! We'll try more tomorrow.

---

### Post by lswest on 2008-04-26
Yes, roaming mode should be enabled, and then try left-clicking the network icon on the top panel, it should give you a list of in-range networks, choose the one you want to connect to, it will prompt for the key, and then it should work.

---

### Post by goslings on 2008-04-26
Thought I would give this a go but the make falls over with many errorrs
I see to have lost amy ref to b43 in harware drivers though ?

> **adult swim said:**
> .....  
now you will need to use the synaptics package manager via cd and install the build-essential package, the same way you installed the b43-fwcutter package that didn't work earlier.  
now you can get to work
from a terminal, one line at a time [code]tar xjf b43-fwcutter-011.tar.bz2

cd b43-fwcutter-011

make



---

### Post by adult swim on 2008-04-26
i cant sleep!
digisoft, as lswest pointed out, you need to have roaming mode enabled!

goslings, moslty this has been directed solely at digisoft as he does not have an internet connection from within ubuntu.  post 9 in this thread may be of interest to you.  if you have never installed the b43-fwcutter package, or ubuntu has never suggested it for you, you may wish to run from a terminal ```
sudo apt-get install b43-fwcutter
```

---

### Post by goslings on 2008-04-26
> **adult swim said:**
> 
goslings, moslty this has been directed solely at digisoft as he does not have an internet connection from within ubuntu.  post 9 in this thread may be of interest to you.  if you have never installed the b43-fwcutter package, or ubuntu has never suggested it for you, you may wish to run from a terminal ```
sudo apt-get install b43-fwcutter
```

sorry to butt in and thanks for the suggestion 
wont disrupt this thread so put up my own
[http://ubuntuforums.org/showthread.php?t=768197](http://ubuntuforums.org/showthread.php?t=768197)
thanks again

---

### Post by sanderella on 2008-04-26
> **MRiGnS said:**
> I guess b43-fwcutter isn't working with this model, is it?

It doesn't seem to be working on my Inspiron 1300 either. No wireless connection since Hardy upgrade. It would be nice if I could fix this myself without having to go to the LUG and confess I couldn't do it, so any help gratefully appreciated.

---

### Post by digisoft on 2008-04-26
Adult Swim,

I am posting this with a WORKING wireless connection now! I am in Ubuntu, firefox beta 3 and posting!!!! I enabled the roaming and saw the list of wireless networks in range and was able to connect to my ByteMe network :)
:guitar:

Now I just need to remember the name of that software I used about a year  ago to install XP inside of linux then I can format this drive and do a fresh linux install. I know you mentioned that I didn't need to, but if I don't wipe the drive I'll be stuck with NTFS, right?

Also, I just checked and I'm only connected at 2mbs, so now I will have to figure out how to speed it up....

Thanks so much for all the help!

---

### Post by Patsoe on 2008-04-26
Hi, glad it's solved - sorry I tuned out for sleep but there are gladly plenty of people around :)

As for running WinXP, here's a starting point [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) but note that that information may be a bit outdated because Hardy has better built-in KVM support, I think.

---

### Post by digisoft on 2008-04-27
Well, I was happy with how things were working so I removed the Ubuntu I installed through windows and did a fresh install The first thing I did was try to setup the wireless again but I got a ton of errors when running the make
> 
fwcutter_list.h:140: warning: excess elements in struct initializer
fwcutter_list.h:140: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[22]’)
fwcutter_list.h:141: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:141: warning: excess elements in struct initializer
fwcutter_list.h:141: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[23]’)
fwcutter_list.h:141: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:141: warning: excess elements in struct initializer
fwcutter_list.h:141: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[23]’)
fwcutter_list.h:141: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:141: warning: excess elements in struct initializer
fwcutter_list.h:141: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[23]’)
fwcutter_list.h:142: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:142: warning: excess elements in struct initializer
fwcutter_list.h:142: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[24]’)
fwcutter_list.h:142: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:142: warning: excess elements in struct initializer
fwcutter_list.h:142: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[24]’)
fwcutter_list.h:142: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:142: warning: excess elements in struct initializer
fwcutter_list.h:142: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[24]’)
fwcutter_list.h:143: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:143: warning: excess elements in struct initializer
fwcutter_list.h:143: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[25]’)
fwcutter_list.h:143: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:143: warning: excess elements in struct initializer
fwcutter_list.h:143: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[25]’)
fwcutter_list.h:143: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:143: warning: excess elements in struct initializer
fwcutter_list.h:143: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[25]’)
fwcutter_list.h:144: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:144: warning: excess elements in struct initializer
fwcutter_list.h:144: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[26]’)
fwcutter_list.h:144: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:144: warning: excess elements in struct initializer
fwcutter_list.h:144: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[26]’)
fwcutter_list.h:144: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:144: warning: excess elements in struct initializer
fwcutter_list.h:144: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[26]’)
fwcutter_list.h:145: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:145: warning: excess elements in struct initializer
fwcutter_list.h:145: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[27]’)
fwcutter_list.h:145: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:145: warning: excess elements in struct initializer
fwcutter_list.h:145: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[27]’)
fwcutter_list.h:145: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:145: warning: excess elements in struct initializer
fwcutter_list.h:145: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[27]’)
fwcutter_list.h:146: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:146: warning: excess elements in struct initializer
fwcutter_list.h:146: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[28]’)
fwcutter_list.h:146: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:146: warning: excess elements in struct initializer
fwcutter_list.h:146: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[28]’)
fwcutter_list.h:146: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:146: warning: excess elements in struct initializer
fwcutter_list.h:146: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[28]’)
fwcutter_list.h:147: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:147: warning: excess elements in struct initializer
fwcutter_list.h:147: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[29]’)
fwcutter_list.h:147: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:147: warning: excess elements in struct initializer
fwcutter_list.h:147: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[29]’)
fwcutter_list.h:147: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:147: warning: excess elements in struct initializer
fwcutter_list.h:147: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[29]’)
fwcutter_list.h:148: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:148: warning: excess elements in struct initializer
fwcutter_list.h:148: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[30]’)
fwcutter_list.h:148: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:148: warning: excess elements in struct initializer
fwcutter_list.h:148: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[30]’)
fwcutter_list.h:148: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:148: warning: excess elements in struct initializer
fwcutter_list.h:148: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[30]’)
fwcutter_list.h:149: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:149: warning: excess elements in struct initializer
fwcutter_list.h:149: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[31]’)
fwcutter_list.h:149: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:149: warning: excess elements in struct initializer
fwcutter_list.h:149: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[31]’)
fwcutter_list.h:149: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:149: warning: excess elements in struct initializer
fwcutter_list.h:149: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[31]’)
fwcutter_list.h:150: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:150: warning: excess elements in struct initializer
fwcutter_list.h:150: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[32]’)
fwcutter_list.h:150: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:150: warning: excess elements in struct initializer
fwcutter_list.h:150: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[32]’)
fwcutter_list.h:150: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:150: warning: excess elements in struct initializer
fwcutter_list.h:150: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[32]’)
fwcutter_list.h:151: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:151: warning: excess elements in struct initializer
fwcutter_list.h:151: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[33]’)
fwcutter_list.h:151: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:151: warning: excess elements in struct initializer
fwcutter_list.h:151: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[33]’)
fwcutter_list.h:151: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:151: warning: excess elements in struct initializer
fwcutter_list.h:151: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[33]’)
fwcutter_list.h:152: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:152: warning: excess elements in struct initializer
fwcutter_list.h:152: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[34]’)
fwcutter_list.h:152: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:152: warning: excess elements in struct initializer
fwcutter_list.h:152: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[34]’)
fwcutter_list.h:152: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:152: warning: excess elements in struct initializer
fwcutter_list.h:152: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[34]’)
fwcutter_list.h:153: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:153: warning: excess elements in struct initializer
fwcutter_list.h:153: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[35]’)
fwcutter_list.h:153: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:153: warning: excess elements in struct initializer
fwcutter_list.h:153: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[35]’)
fwcutter_list.h:153: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:153: warning: excess elements in struct initializer
fwcutter_list.h:153: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[35]’)
fwcutter_list.h:154: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:154: warning: excess elements in struct initializer
fwcutter_list.h:154: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[36]’)
fwcutter_list.h:154: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:154: warning: excess elements in struct initializer
fwcutter_list.h:154: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[36]’)
fwcutter_list.h:154: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:154: warning: excess elements in struct initializer
fwcutter_list.h:154: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[36]’)
fwcutter_list.h:155: error: unknown field ‘offset’ specified in initializer
fwcutter_list.h:155: warning: excess elements in struct initializer
fwcutter_list.h:155: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[37]’)
fwcutter_list.h:155: error: unknown field ‘type’ specified in initializer
fwcutter_list.h:155: warning: excess elements in struct initializer
fwcutter_list.h:155: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[37]’)
fwcutter_list.h:155: error: unknown field ‘length’ specified in initializer
fwcutter_list.h:155: warning: excess elements in struct initializer
fwcutter_list.h:155: warning: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[37]’)
fwcutter_list.h:156: error: initializer element is not constant
fwcutter_list.h:156: error: (near initialization for ‘_cb8d70972b885b1f8883b943c0261a3c[38].name’)
fwcutter_list.h:171: error: unknown field ‘flags’ specified in initializer
fwcutter_list.h:171: warning: initialization makes pointer from integer without a cast
fwcutter_list.h:181: error: unknown field ‘flags’ specified in initializer
fwcutter_list.h:181: warning: initialization makes pointer from integer without a cast
fwcutter_list.h:191: error: unknown field ‘flags’ specified in initializer
fwcutter_list.h:191: warning: initialization makes pointer from integer without a cast
fwcutter_list.h:200: error: unknown field ‘flags’ specified in initializer
fwcutter_list.h:200: warning: initialization makes pointer from integer without a cast
fwcutter_list.h:209: error: unknown field ‘flags’ specified in initializer
fwcutter_list.h:209: warning: initialization makes pointer from integer without a cast
fwcutter.c: In function ‘file_ok’:
fwcutter.c:65: error: ‘const struct file’ has no member named ‘flags’
fwcutter.c:65: error: invalid operands to binary &
fwcutter.c: At top level:
fwcutter.c:69: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘to_be16’
fwcutter.c:93: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘to_be32’
fwcutter.c:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘from_be32’
fwcutter.c: In function ‘print_ucode_version’:
fwcutter.c:129: error: ‘struct insn’ has no member named ‘opcode’
fwcutter.c:129: warning: comparison between pointer and integer
fwcutter.c:129: error: ‘struct insn’ has no member named ‘opcode’
fwcutter.c:129: warning: comparison between pointer and integer
fwcutter.c:132: error: ‘struct insn’ has no member named ‘op1’
fwcutter.c:132: error: invalid operands to binary &
fwcutter.c:132: error: invalid operands to binary <<
fwcutter.c:132: error: ‘struct insn’ has no member named ‘op2’
fwcutter.c:132: error: invalid operands to binary &
fwcutter.c:132: error: invalid operands to binary |
fwcutter.c:132: warning: assignment makes integer from pointer without a cast
fwcutter.c:138: error: ‘struct insn’ has no member named ‘op3’
fwcutter.c:140: warning: implicit declaration of function ‘printf’
fwcutter.c:140: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c: At top level:
fwcutter.c:156: error: expected ‘)’ before ‘in’
fwcutter.c:171: error: expected ‘)’ before ‘in’
fwcutter.c:186: error: expected ‘)’ before ‘in’
fwcutter.c:201: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
fwcutter.c:201: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
fwcutter.c: In function ‘analyse_ucode’:
fwcutter.c:203: error: ‘uint64_t’ undeclared (first use in this function)
fwcutter.c:203: error: (Each undeclared identifier is reported only once
fwcutter.c:203: error: for each function it appears in.)
fwcutter.c:203: error: ‘insns’ undeclared (first use in this function)
fwcutter.c:203: error: invalid operands to binary *
fwcutter.c:203: error: expected expression before ‘)’ token
fwcutter.c:203: error: invalid operands to binary *
fwcutter.c:203: warning: statement with no effect
fwcutter.c:205: error: ‘uint32_t’ undeclared (first use in this function)
fwcutter.c:205: warning: statement with no effect
fwcutter.c:205: error: expected ‘;’ before ‘i’
fwcutter.c:207: error: ‘i’ undeclared (first use in this function)
fwcutter.c:207: error: ‘len’ undeclared (first use in this function)
fwcutter.c:207: error: invalid operands to binary /
fwcutter.c:207: error: lvalue required as increment operand
fwcutter.c:210: warning: implicit declaration of function ‘disasm_ucode_1’
fwcutter.c:210: error: array subscript is not an integer
fwcutter.c:214: warning: implicit declaration of function ‘disasm_ucode_2’
fwcutter.c:214: error: array subscript is not an integer
fwcutter.c:218: warning: implicit declaration of function ‘disasm_ucode_3’
fwcutter.c:218: error: array subscript is not an integer
fwcutter.c: At top level:
fwcutter.c:225: error: expected ‘)’ before ‘*’ token
fwcutter.c: In function ‘swap_endianness_iv’:
fwcutter.c:238: error: ‘struct iv’ has no member named ‘reg’
fwcutter.c:238: warning: implicit declaration of function ‘bswap_16’
fwcutter.c:238: error: ‘struct iv’ has no member named ‘reg’
fwcutter.c:238: warning: statement with no effect
fwcutter.c:239: error: ‘struct iv’ has no member named ‘size’
fwcutter.c:239: error: ‘struct iv’ has no member named ‘size’
fwcutter.c:239: warning: statement with no effect
fwcutter.c:240: error: ‘struct iv’ has no member named ‘val’
fwcutter.c:240: warning: implicit declaration of function ‘bswap_32’
fwcutter.c:240: error: ‘struct iv’ has no member named ‘val’
fwcutter.c:240: warning: statement with no effect
fwcutter.c: At top level:
fwcutter.c:243: error: expected declaration specifiers or ‘...’ before ‘size_t’
fwcutter.c:244: error: expected declaration specifiers or ‘...’ before ‘size_t’
fwcutter.c:246: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
fwcutter.c: In function ‘build_ivs’:
fwcutter.c:250: error: ‘uint32_t’ undeclared (first use in this function)
fwcutter.c:250: warning: statement with no effect
fwcutter.c:250: error: expected ‘;’ before ‘i’
fwcutter.c:251: error: ‘size_t’ undeclared (first use in this function)
fwcutter.c:251: warning: statement with no effect
fwcutter.c:251: error: expected ‘;’ before ‘out_size’
fwcutter.c:254: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:255: warning: implicit declaration of function ‘exit’
fwcutter.c:255: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:258: warning: implicit declaration of function ‘malloc’
fwcutter.c:258: warning: incompatible implicit declaration of built-in function ‘malloc’
fwcutter.c:258: error: ‘in_size’ undeclared (first use in this function)
fwcutter.c:258: warning: passing argument 1 of ‘malloc’ makes integer from pointer without a cast
fwcutter.c:260: warning: implicit declaration of function ‘perror’
fwcutter.c:261: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:264: error: ‘i’ undeclared (first use in this function)
fwcutter.c:264: warning: division by zero
fwcutter.c:264: error: invalid operands to binary /
fwcutter.c:264: error: lvalue required as increment operand
fwcutter.c:264: warning: left-hand operand of comma expression has no effect
fwcutter.c:264: warning: value computed is not used
fwcutter.c:265: error: ‘flags’ undeclared (first use in this function)
fwcutter.c:265: error: invalid operands to binary &
fwcutter.c:268: error: ‘struct iv’ has no member named ‘reg’
fwcutter.c:268: warning: implicit declaration of function ‘to_be16’
fwcutter.c:268: error: invalid operands to binary &
fwcutter.c:269: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:270: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:272: error: ‘struct b43_iv’ has no member named ‘offset_size’
fwcutter.c:272: error: ‘struct iv’ has no member named ‘reg’
fwcutter.c:272: warning: statement with no effect
fwcutter.c:273: error: ‘struct iv’ has no member named ‘size’
fwcutter.c:273: warning: comparison between pointer and integer
fwcutter.c:274: error: ‘struct b43_iv’ has no member named ‘offset_size’
fwcutter.c:274: warning: statement with no effect
fwcutter.c:275: error: ‘struct b43_iv’ has no member named ‘data’
fwcutter.c:275: error: request for member ‘d32’ in something not a structure or union
fwcutter.c:275: error: ‘struct iv’ has no member named ‘val’
fwcutter.c:275: warning: statement with no effect
fwcutter.c:277: error: ‘out_size’ undeclared (first use in this function)
fwcutter.c:277: error: ‘be16_t’ undeclared (first use in this function)
fwcutter.c:277: error: ‘be32_t’ undeclared (first use in this function)
fwcutter.c:277: error: invalid operands to binary +
fwcutter.c:277: warning: statement with no effect
fwcutter.c:278: error: ‘uint8_t’ undeclared (first use in this function)
fwcutter.c:278: error: expected expression before ‘)’ token
fwcutter.c:278: error: invalid operands to binary *
fwcutter.c:279: error: ‘struct iv’ has no member named ‘size’
fwcutter.c:279: warning: comparison between pointer and integer
fwcutter.c:280: error: ‘struct iv’ has no member named ‘val’
fwcutter.c:280: warning: implicit declaration of function ‘to_be32’
fwcutter.c:280: error: invalid operands to binary &
fwcutter.c:281: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:282: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:284: error: ‘struct b43_iv’ has no member named ‘data’
fwcutter.c:284: error: request for member ‘d16’ in something not a structure or union
fwcutter.c:284: warning: implicit declaration of function ‘from_be32’
fwcutter.c:284: error: ‘struct iv’ has no member named ‘val’
fwcutter.c:284: warning: statement with no effect
fwcutter.c:286: error: invalid operands to binary +
fwcutter.c:286: warning: statement with no effect
fwcutter.c:287: error: expected expression before ‘)’ token
fwcutter.c:287: error: invalid operands to binary *
fwcutter.c:289: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:290: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:293: error: ‘struct fw_header’ has no member named ‘size’
fwcutter.c:293: warning: statement with no effect
fwcutter.c:294: error: ‘_out_size’ undeclared (first use in this function)
fwcutter.c:294: error: incompatible types in assignment
fwcutter.c:294: warning: statement with no effect
fwcutter.c: At top level:
fwcutter.c:297: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
fwcutter.c:297: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
fwcutter.c:298: error: expected declaration specifiers or ‘...’ before ‘uint32_t’
fwcutter.c: In function ‘write_file’:
fwcutter.c:300: error: ‘FILE’ undeclared (first use in this function)
fwcutter.c:300: error: ‘f’ undeclared (first use in this function)
fwcutter.c:300: error: invalid operands to binary *
fwcutter.c:300: warning: statement with no effect
fwcutter.c:305: error: ‘flags’ undeclared (first use in this function)
fwcutter.c:305: error: invalid operands to binary &
fwcutter.c:310: warning: implicit declaration of function ‘snprintf’
fwcutter.c:310: warning: incompatible implicit declaration of built-in function ‘snprintf’
fwcutter.c:313: warning: implicit declaration of function ‘fprintf’
fwcutter.c:313: warning: incompatible implicit declaration of built-in function ‘fprintf’
fwcutter.c:313: error: ‘stderr’ undeclared (first use in this function)
fwcutter.c:314: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:317: warning: implicit declaration of function ‘mkdir’
fwcutter.c:318: error: ‘errno’ undeclared (first use in this function)
fwcutter.c:318: error: ‘EEXIST’ undeclared (first use in this function)
fwcutter.c:320: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:326: warning: incompatible implicit declaration of built-in function ‘fprintf’
fwcutter.c:327: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:329: warning: implicit declaration of function ‘fopen’
fwcutter.c:329: warning: statement with no effect
fwcutter.c:332: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:334: warning: implicit declaration of function ‘fwrite’
fwcutter.c:334: warning: incompatible implicit declaration of built-in function ‘fwrite’
fwcutter.c:336: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:338: warning: incompatible implicit declaration of built-in function ‘fwrite’
fwcutter.c:338: error: ‘buf’ undeclared (first use in this function)
fwcutter.c:338: error: ‘len’ undeclared (first use in this function)
fwcutter.c:338: warning: passing argument 3 of ‘fwrite’ makes integer from pointer without a cast
fwcutter.c:338: warning: comparison between pointer and integer
fwcutter.c:340: warning: incompatible implicit declaration of built-in function ‘exit’
fwcutter.c:342: warning: implicit declaration of function ‘fclose’
fwcutter.c: At top level:
fwcutter.c:345: error: expected ‘)’ before ‘*’ token
fwcutter.c: In function ‘print_banner’:
fwcutter.c:415: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c: In function ‘print_file’:
fwcutter.c:423: error: ‘const struct file’ has no member named ‘flags’
fwcutter.c:423: error: invalid operands to binary &
fwcutter.c:424: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:426: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:428: warning: implicit declaration of function ‘strlen’
fwcutter.c:428: warning: incompatible implicit declaration of built-in function ‘strlen’
fwcutter.c:429: warning: implicit declaration of function ‘strncpy’
fwcutter.c:429: warning: incompatible implicit declaration of built-in function ‘strncpy’
fwcutter.c:431: warning: incompatible implicit declaration of built-in function ‘snprintf’
fwcutter.c:433: warning: implicit declaration of function ‘strcpy’
fwcutter.c:433: warning: incompatible implicit declaration of built-in function ‘strcpy’
fwcutter.c:435: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:436: warning: incompatible implicit declaration of built-in function ‘strlen’
fwcutter.c:437: warning: incompatible implicit declaration of built-in function ‘strlen’
fwcutter.c:440: warning: incompatible implicit declaration of built-in function ‘strlen’
fwcutter.c: In function ‘print_supported_files’:
fwcutter.c:452: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:466: error: ‘struct file’ has no member named ‘flags’
fwcutter.c:466: error: invalid operands to binary &
fwcutter.c:469: error: ‘struct file’ has no member named ‘flags’
fwcutter.c:469: error: invalid operands to binary &
fwcutter.c: At top level:
fwcutter.c:474: error: expected ‘)’ before ‘*’ token
fwcutter.c: In function ‘print_usage’:
fwcutter.c:515: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c: In function ‘do_cmp_arg’:
fwcutter.c:543: error: ‘size_t’ undeclared (first use in this function)
fwcutter.c:543: warning: statement with no effect
fwcutter.c:543: error: expected ‘;’ before ‘arg_len’
fwcutter.c:547: error: ‘arg_len’ undeclared (first use in this function)
fwcutter.c:547: warning: incompatible implicit declaration of built-in function ‘strlen’
fwcutter.c:547: warning: statement with no effect
fwcutter.c:548: error: ‘template_len’ undeclared (first use in this function)
fwcutter.c:548: warning: statement with no effect
fwcutter.c:555: warning: implicit declaration of function ‘memcmp’
fwcutter.c:556: error: invalid operands to binary +
fwcutter.c:556: warning: assignment from incompatible pointer type
fwcutter.c:564: warning: implicit declaration of function ‘strcmp’
fwcutter.c:569: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c: In function ‘parse_args’:
fwcutter.c:606: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:613: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:620: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:626: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:633: warning: passing argument 4 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:633: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c: In function ‘main’:
fwcutter.c:663: error: ‘FILE’ undeclared (first use in this function)
fwcutter.c:663: error: ‘fd’ undeclared (first use in this function)
fwcutter.c:663: error: invalid operands to binary *
fwcutter.c:663: warning: statement with no effect
fwcutter.c:681: warning: statement with no effect
fwcutter.c:683: warning: incompatible implicit declaration of built-in function ‘fprintf’
fwcutter.c:683: error: ‘stderr’ undeclared (first use in this function)
fwcutter.c:688: warning: implicit declaration of function ‘find_file’
fwcutter.c:688: warning: assignment makes pointer from integer without a cast
fwcutter.c:692: error: ‘const struct file’ has no member named ‘flags’
fwcutter.c:692: error: invalid operands to binary &
fwcutter.c:699: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:702: warning: implicit declaration of function ‘extract_or_identify’
fwcutter.c:702: error: ‘const struct file’ has no member named ‘flags’
make: *** [fwcutter.o] Error 1
owner@lilbeast:~/b43-fwcutter-011$ 

I used the same files I used the first time along with the same commands, why doesn't it work this time?

---

### Post by digisoft on 2008-04-27
I see what I did, I forgot build-essential, installing that now and I'll see what happens

---

### Post by kmyers1us on 2008-04-30
I have an HP L2000 SE with a BC8413. I had a tough time with Hardy Heron trying to get this working with WAP Personal. As I was about to give up and go back to Fiesty, something great happened!

I found this:
[http://blog.stevienova.com/2008/04/25/ubuntu-804-hardy-heron-linux-is-cool-linux-wireless-is-not-10-step-program/](http://blog.stevienova.com/2008/04/25/ubuntu-804-hardy-heron-linux-is-cool-linux-wireless-is-not-10-step-program/)
and did it to get wl_apsta.o installed properly.
Now it works great with b43-fwcutter.

Try this and see if it fixes it. 

-------
L2000 SE ATI Radeon Xpress 200M restricted drivers
-------

 After the wireless nighmare, I was able to get my ATI Radeon Xpress 200M to work in 3D with restricted drivers. In Hardy now suspend/hibernate works again with the ATI restricted drivers.

I am running compiz and get all the cool desktop affects.

---

