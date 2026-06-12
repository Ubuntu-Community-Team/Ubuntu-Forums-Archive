---
title: "Can't Use / Detect / mount USB MP3 player"
date: 2009-03-16
forum: Hardware
---

### Post by omisaza on 2009-03-16
Hello, I want use a MP3 player,  gigabeat (nana)  p5s   512 MB from  TOSHIBA , basically I want to dump files on it (folder), same way as it works under winblows,  i've search around for days, try several solutions but nothing yet,  I've tested on Ubuntu 8.04,  8.10 , PConLinux 07 with the same results,  running lsusb shows the device but fdisk doesn't get it,  now I'm pretty sure is a bug, anyway here is what I have, just in case! thank You

device:  gigabeat (nana)  p5s   512 MB , TOSHIBA

DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
kernel:  uname -r   2.6.24-19-generic

DISTRIB_DESCRIPTION="Ubuntu 8.10"
kernel:  uname -r   2.6.27-11-generic

lsusb

Bus 005 Device 004: ID 0930:000f Toshiba Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 056e:0029 Elecom Co., Ltd 
Bus 001 Device 001: ID 0000:0000 


sudo fdisk -lu

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    71633834    35816886    7  HPFS/NTFS
/dev/sda2        71633835   155348549    41857357+  83  Linux
/dev/sda3       155348550   156296384      473917+   5  Extended
/dev/sda5       155348613   156296384      473886   82  Linux swap / Solaris


dmesg | grep -i USB

[16795.541524] usb 5-3: new high speed USB device using ehci_hcd and address 4
[16795.674789] usb 5-3: configuration #1 chosen from 1 choice
[17042.356872] usb 5-3: USB disconnect, address 4

---

### Post by nloewen on 2009-03-31
I have the same problem with my sansa e260 in Jaunty beta. A solution or workaround would be greatly appreciated.

---

### Post by BennBuntu on 2009-06-08
I got my gigabeat F-60 working by editing the vendor in

/usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi

from 2352 to 0930 to match output from lsusb. For the sandisk, maybe something similar, I saw some people had removed it all together to get it going.

See this bug report [https://bugs.launchpad.net/ubuntu/+bug/345916]("https://bugs.launchpad.net/ubuntu/+bug/345916")

---

### Post by radi0j0hn on 2009-06-11
I appreciate your solution, but can someone present this in a step by step fashion so those of us who can do SOME things with terminal but are noobs can fix this?  Where do we get the numbers to match, etc.

My gigabeat 40 is invisible to Ubuntu as well!

---

### Post by briguy47 on 2009-06-11
> **radi0j0hn said:**
> I appreciate your solution, but can someone present this in a step by step fashion so those of us who can do SOME things with terminal but are noobs can fix this?  Where do we get the numbers to match, etc.

My gigabeat 40 is invisible to Ubuntu as well!


I don't know if this solution will work for the problem, but here is a step by step on how to do it.  :D 

1. Launch your terminal of choice.

2. Change to the directory holding 20-libgphoto2.fdi with:

```
 **cd  /usr/share/hal/fdi/preprobe/10osvendor/**
```3. Backup the file we are about to edit with:  

        **```
sudo cp 20-libgphoto2.fdi 20-libgphoto2.fdi.bak 
```**
4. Open 20-libgphoto2.fdi in GEdit with:  

```
**sudo gedit 20-libgphoto2.fdi**
```


5. Replace the number 2352 with 0390, for the Toshiba Gigabeat line of players by:
       
[B]Hit Ctrl + H and type 2352 into the "Search For" box and 0930 in the "Replace With" box.  
       Click the "Replace All" button.
[/B] 

7. Save the file with **Ctrl + S**.  Then reboot your system to apply the changes.  If this method works, your device should be good to go. 


I hope that is what you were looking for.  If you have any questions, just let me know.  :)


Non-Critical Note: This will replace the vendor_id for EVERY model of the Toshiba Gigabeat.  I can't see the harm in doing so, but if you would feel more comfortable only replacing the id that applies to your model, just search for the entry that contains your model. 

i.e. if you have a Gigabeat P10 then you would search for and change only the 2352 in this entry:

 <match key="usb.vendor_id" int="**2352**">
    <match key="usb.product_id" int="17">
     <merge key="info.category" type="string">portable_audio_player</merge>
     <append key="info.capabilities" type="strlist">portable_audio_player</append>
     <merge key="portable_audio_player.access_method" type="string">user</merge>
     <merge key="portable_audio_player.type" type="string">mtp</merge>
     <append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
     <merge key="camera.libgphoto2.name" type="string">**Toshiba Gigabeat P10**</merge>
     <merge key="camera.libgphoto2.support" type="bool">true</merge>
    </match>

---

