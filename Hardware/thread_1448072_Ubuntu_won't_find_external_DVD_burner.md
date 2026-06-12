---
title: "Ubuntu won't find external DVD burner"
date: 2010-04-06
forum: Hardware
---

### Post by H3R3T1K on 2010-04-06
Hi everybody,

this is my first post here. I decided to give the Netbook remix a try yesterday and I must say I'm impressed. I have no Linux experience at all. My netbook is a Asus EEE 1005HA. I plugged my external DVD burner in in order to install the drivers for my printer (HP LaserJet P1005). Ubuntu doesn't give me any notification that I have plugged in the device. What can I do about this?

---

### Post by Lundi020 on 2011-01-07
Hi,

I'm having the same problem with connecting external DVD drive to my netbook wich runs on ubuntu netbook edition. I have posted my query on this forum and haven't received any response either. Not sure if the community will do anything about it :( but thought to jooin to your post so people can see that there are more of us with this issue! cheers

---

### Post by coffeecat on 2011-01-07
@Lundi020, the OP hasn't logged in for two months so we may or may not hear from them again. Let's do a bit of investigating of your problem.

Plug the DVD drive in and switch it on. Don't bother with putting a disc in it. Now open a terminal and do each of the following three commands:

```
lsusb
dmesg | tail
ls /dev/sr*
```Post the output. When you post it  click on the # icon in the message toolbar and paste the output between the two [code] tags.

---

### Post by musket85 on 2011-07-16
BUMP: I've got the same problem and can post that output. Hopefully Coffeecat you can still help me.


```

ben@obeseChild:~$ lsusb
Bus 005 Device 002: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 002: ID 13d3:5702 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ben@obeseChild:~$ dmesg | tail
[ 1052.253440] sr 7:0:0:0: Attached scsi generic sg1 type 5
[ 1325.948201] Skipping EDID probe due to cached edid
[ 1710.563586] usb 1-3: USB disconnect, address 7
[ 1841.821112] usb 1-3: new high speed USB device using ehci_hcd and address 8
[ 1841.954986] usb-storage 1-3:1.0: Quirks match for vid 05e3 pid 0701: 520
[ 1841.955120] scsi8 : usb-storage 1-3:1.0
[ 1843.011798] scsi 8:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462D HS02 PQ: 0 ANSI: 0
[ 1843.273637] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 1843.274174] sr 8:0:0:0: Attached scsi CD-ROM sr0
[ 1843.274638] sr 8:0:0:0: Attached scsi generic sg1 type 5
ben@obeseChild:~$ ls /dev/sr*
/dev/sr0

```

Help? I have an external dvd-rom/cdrw drive, second one I've tried to no avail. Drive spins up but not sign of

---

### Post by coffeecat on 2011-07-16
@musket85, two points. Your external DVD device has this enclosure:

> **musket85 said:**
> 
Bus 001 Device 008: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter


It's the enclosure that's the problem, not the optical drive it encloses. At least it's the problem in certain Ubuntu releases, notably 10.10/Maverick. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

It's a bit long but there are some workarounds in there. Read my post at #9 where I did some investigating in different Ubuntu releases. It's a bit out of date with regard to Natty/11.04 now, because I posted that when Natty was still pre-alpha, and Natty was released over two months ago. Tbh, I haven't kept up-to-date with how this device is working in Natty atm.

Which leads to... Which version of Ubuntu are you using? Your personal details say 8.04, but that's obsolete now.

---

### Post by musket85 on 2011-07-16
I'm using Maverick 10.10... should update my description really.

I'll let you know how I get on with the workarounds in that link. 

Cheers for the very speedy response.

---

### Post by musket85 on 2011-07-16
Okay- I can get the drive to mount via 

```

udisks --mount /dev/sr0

```

I can then get it to recognise the disk in vlc (I'm starting with a video dvd for testing) 

Putting /dev/sr0 in the disc location in vlc begins to work and then flakes out putting this message to the terminal

[CODE]

libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
[\CODE]

Somehow libdvdcss2 had become deselected.... 
[CODE]
sudo /usr/share/doc/libdvdread4/install-css.sh
[\CODE]

I suppose this means I'll have to mount the disc each time... yawn. Next I need to try burning a cd & listening to an audio cd.

Cheers Coffeecat, you are a legend. Although I might need more help with the cd's in a moment. I'll let you know.

---

### Post by musket85 on 2011-07-16
Urgh, fail on all CD counts. Should I just upgrade to 11.04?

OR if that's a bad idea, what would you recommend for burning/playing cd's?



My old comp worked perfectly under standard ubuntu, I'm useless with unr/unity COMPLETELY paralysed.

---

### Post by coffeecat on 2011-07-17
> **musket85 said:**
> Urgh, fail on all CD counts. Should I just upgrade to 11.04?

I just tried a quick test in Natty with a video DVD, audio CD and data CD in my ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter device. The data CD and audio CD both automounted and I was able to play the audio CD in Banshee. The DVD didn't automount - as in Maverick - but opening VLC and Media -> Open Disc worked just fine. So... you will still have a minor issue with video DVDs but not with audio or data CDs.

> **musket85 said:**
> I'm useless with unr/unity COMPLETELY paralysed.

Unity in 11.04 is not the same as the old UNR interface. It is transformed, 1000% better than Unity in 10.10. Give it a try. Many people didn't like it at first but have come to prefer it. There are two links in my sig which will help you find your way round it.

---

### Post by busibus on 2011-07-17
Hi!

I've got the same problem but with all external things if i do the output it comes:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
german@german-laptop:~$ dmesg | tail
[   58.082715] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 6 (level, low) -> IRQ 6
[   58.082752] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   59.008032] intel8x0_measure_ac97_clock: measured 55324 usecs (2665 samples)
[   59.008035] intel8x0: clocking to 48000
[   59.245606] ppdev: user-space parallel port driver
[   68.064027] eth1: no IPv6 routers present
[   69.640101] lib80211_crypt: registered algorithm 'CCMP'
[   71.378321] Intel AES-NI instructions are not detected.
[   71.399246] padlock_aes: VIA PadLock not detected.
[  479.186185] ipw2200: Firmware error detected.  Restarting.
german@german-laptop:~$ ls /dev/sr*
ls: no se puede acceder a /dev/sr*: No existe el fichero o el directorio

A couple of weeks ago everything was fine so i don't know if the problem became when i upgrade to 11.04 

If someone can help me i will be really happy!

---

### Post by movieman on 2011-07-17
I've been having a similar problem with my new i5 server. I installed the OS using the USB DVD drive and that worked OK, but now if I put a disk in the drive the OS can't see it. What appears to happen is that it tries to mount the drive and then /dev/sr0 disappears.

---

### Post by musket85 on 2011-07-30
I did eventually upgrade to 11.04 an the automount kicked in like a good OS should. Seemed to be 10.10 specific. 

And unity in 11.04 is a lot better (autohide ftw), would still prefer the top left ubuntu button to be a menu.. I know they are aiming for touchscreens but at least give us the option of dropdown or fullscreen. 

Cheers coffeecat

---

### Post by HiFlight on 2011-08-01
I have a similar problem with 10.10...my USB CD drive shows up in "Computer" until I load a disk, then after some blinking on the drive, the icon disappears from "Computer".   

Doesn't matter whether it is a data or audio CD.   I have tried several different drives with the same result.  

I hope someone can provide some guidance here, as this is the only major issue I have since installing 10.10 over 10.04.

---

### Post by coffeecat on 2011-08-02
> **HiFlight said:**
> I hope someone can provide some guidance here, as this is the only major issue I have since installing 10.10 over 10.04.

Did you look at the output of lsusb on your system? Did you get a line similar to what musket85 saw?

```
Bus 001 Device 008: [COLOR="Red"]ID 05e3:0701 Genesys Logic, Inc.[/COLOR] USB 2.0 IDE Adapter
```

I've reddened the important bit. If you get the same then have a look at the thread I link to in post #5. There are some workarounds there.

---

### Post by HiFlight on 2011-08-02
> **coffeecat said:**
> Did you look at the output of lsusb on your system? Did you get a line similar to what musket85 saw?

```
Bus 001 Device 008: [COLOR=Red]ID 05e3:0701 Genesys Logic, Inc.[/COLOR] USB 2.0 IDE Adapter
```I've reddened the important bit. If you get the same then have a look at the thread I link to in post #5. There are some workarounds there.

Please excuse my ignorance, but how do I check the output of lsusb?   I am not real familiar with the use of terminal, but can follow instructions pretty well. 

Thanks...

---

### Post by HiFlight on 2011-08-02
> **HiFlight said:**
> Please excuse my ignorance, but how do I check the output of lsusb?   I am not real familiar with the use of terminal, but can follow instructions pretty well. 

Thanks...

This is what I got as the result of attempting a mount via terminal:

ron@ron-desktop:~$ udisks --mount /dev/sr0
Mount failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ron@ron-desktop:~$ 

And here is an excerpt from Nautilus Prefs:   


[ATTACH]199103[/ATTACH]

---

### Post by coffeecat on 2011-08-02
> **HiFlight said:**
> Please excuse my ignorance, but how do I check the output of lsusb?   I am not real familiar with the use of terminal, but can follow instructions pretty well. 


Open a terminal. Then type:

```
lsusb
```

Then press enter. If you want to post the output, highlight the output with the mouse, right-click and choose "copy". Then you'll be able to paste it into your post.

---

### Post by HiFlight on 2011-08-02
> **coffeecat said:**
> Open a terminal. Then type:

```
lsusb
```Then press enter. If you want to post the output, highlight the output with the mouse, right-click and choose "copy". Then you'll be able to paste it into your post.

Here are the results of that command:  

ron@ron-desktop:~$ lsusb
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ron@ron-desktop:~$ 

I'm not sure what that tells me about the non-functioning of my usb cd player.   It does show as a drive in the "computer" dropdown until I put a cd in, then it disappears very shortly thereafter without opening.

---

### Post by coffeecat on 2011-08-02
> **HiFlight said:**
> Here are the results of that command:  

ron@ron-desktop:~$ lsusb
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: [COLOR="Red"]ID 05e3:0701 Genesys Logic, Inc.[/COLOR] USB 2.0 IDE Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ron@ron-desktop:~$ 

I'm not sure what that tells me about the non-functioning of my usb cd player.

It tells you that you have the affected optical drive enclosure. Did you read through this thread? Have another look at my post #5 and the link I posted in it.

---

### Post by HiFlight on 2011-08-02
> **coffeecat said:**
> It tells you that you have the affected optical drive enclosure. Did you read through this thread? Have another look at my post #5 and the link I posted in it.


I have looked through that post and tried the various suggested terminal commands and this is the response: 

ron@ron-desktop:~$ udisks --mount /dev/sr0
Mount failed: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ron@ron-desktop:~$ 

The command: ..../sr1 resulted in file not found.   I do not have an internal cd or dvd drive on this computer.   

Are there any other workarounds that you might suggest?  This is getting pretty annoying, I am beginning to wish I had stayed with 10.04!  

I do very much appreciate the help!

Ron

---

### Post by coffeecat on 2011-08-03
> **HiFlight said:**
> Are there any other workarounds that you might suggest?  This is getting pretty annoying, I am beginning to wish I had stayed with 10.04!  

I sympathise. This is one of those issues that affects only a tiny minority of users but which is mightily inconvenient if it does affect you. And I very much doubt this will ever get fixed in Maverick.

First thing - silly question, but it has to be asked. You did have a CD or DVD in the drive when you ran the udisks command?

I don't know of any workarounds other than those posted in the thread I linked to. But since this device is (mostly) working in Natty/11.04 for others, it might be worth trying Natty on your machine to see if that helps. You don't have to upgrade - yet. Download the Natty ISO and create a bootable live USB. Boot up the live USB, choose "try Ubuntu" to get to the live desktop and see how the device works with your setup.

The other thing that might be worth trying is a later kernel. Tbh, I don't know whether this is a kernel or udev issue, but I suspect the kernel is involved. You can install a newer version of the kernel from a ppa. If you need help, post back and I can see what I can suggest.

Last thing I'd recommend is to try to avoid purchasing any hardware with Genesys stuff in it. Virtually impossible advice, I know, because how would you know what you were getting? All I can say is that Genesys is not on my Christmas card list. I have another Genesys device (SD card reader) that plays up in Linux. If it was one device, I would suspect a bug in the Linux driver. With two different ones by the same manufacturer I'm beginning to think of shoddy hardware, and a well-known line from Oscar Wilde.

---

### Post by victor1234 on 2011-08-03
I'm having issues with my new dvd-burner.It's an external LG GE20, and  I'm able to see the disk that's in the tray, but it won't play the DVD. I  have the codecs installed, but it still gives me the error 	Code: 	Could not read from resource I'm not sure what the issue is, and I'm trying to install Windows XP  als. Please give me any suggestion

---

### Post by HiFlight on 2011-08-03
> **coffeecat said:**
> I sympathise. This is one of those issues that affects only a tiny minority of users but which is mightily inconvenient if it does affect you. And I very much doubt this will ever get fixed in Maverick.

First thing - silly question, but it has to be asked. You did have a CD or DVD in the drive when you ran the udisks command?

I don't know of any workarounds other than those posted in the thread I linked to. But since this device is (mostly) working in Natty/11.04 for others, it might be worth trying Natty on your machine to see if that helps. You don't have to upgrade - yet. Download the Natty ISO and create a bootable live USB. Boot up the live USB, choose "try Ubuntu" to get to the live desktop and see how the device works with your setup.

The other thing that might be worth trying is a later kernel. Tbh, I don't know whether this is a kernel or udev issue, but I suspect the kernel is involved. You can install a newer version of the kernel from a ppa. If you need help, post back and I can see what I can suggest.

Last thing I'd recommend is to try to avoid purchasing any hardware with Genesys stuff in it. Virtually impossible advice, I know, because how would you know what you were getting? All I can say is that Genesys is not on my Christmas card list. I have another Genesys device (SD card reader) that plays up in Linux. If it was one device, I would suspect a bug in the Linux driver. With two different ones by the same manufacturer I'm beginning to think of shoddy hardware, and a well-known line from Oscar Wilde.

Thanks much for the info.   I did burn a live CD for 11.04 and ran it.   Everything looked good, but is it possible to remove the disk  while running live in order to try the audio cd?   I have only the one usb cd drive..

I think I will try the network update first so I don't lose all my contacts, etc and if that doesn't work, will try the clean install.   

Thanks!  Look forward to your answer on removing the live disk while running live.  

Ron

---

### Post by HiFlight on 2011-08-03
> **HiFlight said:**
> Thanks much for the info.   I did burn a live CD for 11.04 and ran it.   Everything looked good, but is it possible to remove the disk  while running live in order to try the audio cd?   I have only the one usb cd drive..

I think I will try the network update first so I don't lose all my contacts, etc and if that doesn't work, will try the clean install.   

Thanks!  Look forward to your answer on removing the live disk while running live.  

Ron

Well, I found an old Memorex USB CD/DVD burner that I had used with another computer.  I ran the live 11.04 disk on it and tried the problem Teac USB cd player with an audio CD and it worked fine.  I then removed the live CD, rebooted back to 10.10  and tried the Memorex with an audio CD, which also worked just fine.  

It appears that the problem with 10.10 and the Teac CD player and is likely to be unsurmountable.   I just need to decide whether to keep 10.10 and use the Memorex or upgrade to 11.04.     

Thanks for all your help, Coffeecat!   At least I now know where the problem lies, and it appears to be a 10.10 issue.

---

### Post by coffeecat on 2011-08-03
@HiFlight, good luck if you do decide to upgrade to 11.04. One FYI, for the future. You can "burn" an Ubuntu ISO to a USB flash pendrive using startup disk creator which is what I was implying you could do. Sorry that I wasn't clear enough. But you got around the problem with your Memorex CD drive which was useful in that it showed that some USB optical drives work OK in Maverick. Clearly it's your Teac player that has the problem Genesys chipset. That Genesys chipset has found its way into a lot of different branded devices, unfortunately.

---

### Post by HiFlight on 2011-08-03
> **coffeecat said:**
> @HiFlight, good luck if you do decide to upgrade to 11.04. One FYI, for the future. You can "burn" an Ubuntu ISO to a USB flash pendrive using startup disk creator which is what I was implying you could do. Sorry that I wasn't clear enough. But you got around the problem with your Memorex CD drive which was useful in that it showed that some USB optical drives work OK in Maverick. Clearly it's your Teac player that has the problem Genesys chipset. That Genesys chipset has found its way into a lot of different branded devices, unfortunately.

I upgraded to 11.04 via network update.  All went smoothly, all my data is intact and the Teac CD player now works fine!   

Overall, I find little to not like so far with Natty.   

Again, Coffeecat, thanks much for all the assistance!

---

### Post by coffeecat on 2011-08-03
You're welcome. Enjoy Natty. You may find the two links in my sig useful for finding your way around the Unity interface.

Good luck!

---

### Post by HiFlight on 2011-08-03
> **coffeecat said:**
> You're welcome. Enjoy Natty. You may find the two links in my sig useful for finding your way around the Unity interface.

Good luck!


The only thing that I want to do is autohide the launcher and the top panel.  The top panel used to autohide I think, but now it doesn't.   

Also, I see that Firefox 5 doesn't have a home icon in the top toolbar any longer.  I did find a little add-on that opens a new tab with my homepage, which is just about as convenient as the icon.  

It seems that my install went very well and everything seems to be working just fine.  

Thanks again...I will use the links in your sig for sure!

---

### Post by rjmac on 2011-10-06
I am on 11.04 and I have an external drive which is not being recognised.  The DVD drive is labeled as a Optic USB DVD/RW the windows drives label it as SunplusIT USB2 SATA Device. 

When I type lsusb
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I see nothing on the system to indicate the device is attached but the device does light up when connected. I can not access the device nor is any disk in the device shown.

Is there anything I can do to get it working?

---

### Post by american.swan on 2012-05-21
My lsusb looks like the following.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fd:0842 Initio Corporation 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
**Bus 001 Device 004: ID 04e8:342a Samsung Electronics Co., Ltd **
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 007: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 001 Device 042: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 046: ID 0fca:8004 Research In Motion, Ltd. Blackberry Handheld
**Bus 001 Device 044: ID 04e8:5f05 Samsung Electronics Co., Ltd **

I have an "internal" SuperMulti drive that seems to burn just fine but the external one does not.  This drive is a Samsung SE-S084C.  It burns Double Layer RW disks.  AND YES, it connects to the computer TWICE.  Does anyone have any idea how to get this to burn?  My computer recognizes it as a CDROM drive maybe because I added it to my fstab, but burning software doesn't recognize it as such.  Supposedly it's /dev/sr1 my internal burner is /dev/sr0 it seems.

Any suggestions would be appreciated.

---

