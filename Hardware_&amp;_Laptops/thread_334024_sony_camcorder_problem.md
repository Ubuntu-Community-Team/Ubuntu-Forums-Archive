---
title: "sony camcorder problem"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by glederfein on 2007-01-08
Hi all!
I am trying to connect my Sony DCR-TRV140E camcorder to my computer so I can capture some of the data on it. It is supposed to be very compatible with Linux, however when using a USB firewire but Ubuntu doesn't seem to detect anything. I tried capturing through Kino but I get an error message at the bottom saying: "raw1394 kernel module not loaded or failure to read/write /dev/raw1394!". 
I tried ```
sudo /sbin/modprobe raw1394
sudo /sbin/modprobe dv1394
sudo mknod /dev/video1394 c 172 0
``` then ```
sudo dvgrab
``` but all I get is: "Error: no camera exists".

Please help me detect my camcorder...

---

### Post by meng on 2007-01-08
Have you tried:
gksu kino
(or else change the permissions on raw1394 so that your user has access)?

---

### Post by glederfein on 2007-01-08
> **meng said:**
> Have you tried:
gksu kino
(or else change the permissions on raw1394 so that your user has access)?
When trying "gksu kino" I get the same warning message in kino and no ability to capture. :(

---

### Post by meng on 2007-01-08
I would assume, then, that:
ls /dev/raw1394
returns nothing when your camera is connected and switched on.

---

### Post by glederfein on 2007-01-08
> **meng said:**
> I would assume, then, that:
ls /dev/raw1394
returns nothing when your camera is connected and switched on.Actually I get the file listed after doing "sudo /sbin/modprobe raw1394" again (I restarted the computer)...

---

### Post by meng on 2007-01-08
Then the hardware is not being detected. You mentioned "USB firewire", do you mean USB or firewire? Because they're quite separate!

---

### Post by glederfein on 2007-01-08
> **meng said:**
> Then the hardware is not being detected. You mentioned "USB firewire", do you mean USB or firewire? Because they're quite separate!
I think it is a USB. The only thing is that on one end it is small (perhaps 4-pin) and the other end is a normal USB.

---

### Post by hal10000 on 2007-01-08
> I would assume, then, that:
ls /dev/raw1394
returns nothing when your camera is connected and switched on

If so, you can create a device, on my sytem it is:
```

sudo mknod /dev/raw1394 c 171 0
sudo mknod /dev/video1394 c 171 1

```

---

### Post by meng on 2007-01-08
> **glederfein said:**
> I think it is a USB. The only thing is that on one end it is small (perhaps 4-pin) and the other end is a normal USB.
I think this is referred to as an A-to-B USB connection. It is NOT firewire, so you should google for USB connections with that camcorder. AFAIK, the 1394 ports only apply to firewire devices.

---

### Post by glederfein on 2007-01-08
> **meng said:**
> I think this is referred to as an A-to-B USB connection. It is NOT firewire, so you should google for USB connections with that camcorder. AFAIK, the 1394 ports only apply to firewire devices.
I can't seem to find the appropriate USB driver. The only I could find (barely) is for Windows. Is there no support for camcorder USB connections in Linux? Must I get firewire in order to capture my camcorder?

---

### Post by hal10000 on 2007-01-08
I googled for your camera and all I found was that this model is NOT compatible with linux.

The only (possibly) positive answer is here: [http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/9deacb9f52ce56ec/1d25ad5978044c21?lnk=gst&q=DCR-TRV&rnum=1#1d25ad5978044c21]("http://groups.google.com/group/comp.os.linux.hardware/browse_thread/thread/9deacb9f52ce56ec/1d25ad5978044c21?lnk=gst&q=DCR-TRV&rnum=1#1d25ad5978044c21")

You may try to modprobe the mentioned modules ([COLOR="Red"]sudo modprobe sd_mod sr_mod usb-storage scsi_mod usb-ohci usbcore[/COLOR])
and mount the camera's storage (presumably as a scsi or usb device).

---

### Post by hal10000 on 2007-01-08
You may also install the usbview package, which is a graphical tool to view your usb media (if your camera is plugged in).
Also, the lshw package may be useful to get info's about connected hardware; it's a command line tool which lists a lot of information about your hardware.

---

### Post by glederfein on 2007-01-08
When trying to modprobe the modules suggested all went fine except for "usb-ohci" which was not found. After installing the USB Viewer I found it detected the camcorder as "snd-usb-audio" and gave me all kinds of information on it. After all this still Kino won't allow me to capture anything and dvgrab says "no camera exists". :(

---

### Post by hal10000 on 2007-01-08
If you have an intel or via chipset on your MB, then the ohci driver may not be used, I assume that the usb_uhci module is used instead.
But the fact that it detects your camera as "snd-usb-audio" is very strange, something is still going wrong.
Plug in th camera and post the output of:
sudo lsusb -v (or sudo usbview), only the relevant parts
maybe the output of sudo lshw and lspci can help too (only the usb specific parts)

---

### Post by meng on 2007-01-08
> **glederfein said:**
> When trying to modprobe the modules suggested all went fine except for "usb-ohci" which was not found. After installing the USB Viewer I found it detected the camcorder as "snd-usb-audio" and gave me all kinds of information on it. After all this still Kino won't allow me to capture anything and dvgrab says "no camera exists". :(
I think kino and dvgrab expect a firewire input. That said, I'm no expert. Is this a brand-new camcorder? i.e. do you have the opportunity to return it to the store because it doesn't suit your needs?

When I purchased my camcorder (Panasonic), the very first thing I did was check that it worked with Linux. If it hadn't, I would have returned it to the store the very next day.

---

### Post by budgie9 on 2007-01-08
Here is a page that may answer some of your questions. The answers on this page are for your Sony camera.
[http://www.css.ap.sony.com/consumer/template/KBCategory.aspx](http://www.css.ap.sony.com/consumer/template/KBCategory.aspx)

It does state that not all Sony cameras can be used for streaming video via the USB port. My newer model camera only allows one to transfer files from the memory stick to the computer over the USB port. Video transfer is only via the Firewire port. I am unable to use my camera as a  webcam as such.
Perhaps you are getting a little confused with the terminology.

---

### Post by glederfein on 2007-01-09
I'm having trouble copying the sudo lsusb -v output since it's too long in the terminal and USB Viewer won't let me copy.
Here's the output of sudo lshw (usb part):
```

 *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef40-ef5f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: QuickCam Express
                   vendor: Logitech, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=spca5xx maxpower=100mA speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             resources: ioport:efa0-efaf irq:6
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef80-ef9f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb
                      description: Audio device
                      vendor: Sony Corp.
                      physical id: 1
                      bus info: usb@2:2.1
                      version: 0.00
                      capabilities: usb-1.00 audio-control
                      configuration: driver=snd-usb-audio maxpower=300mA speed=12.0MB/s

```
The camcorder isn't that new and I don't believe it is possible to return it right now.
I also tried downloading the driver from [here]("http://www.css.ap.sony.com/consumer/template/DDDownload.aspx") and installing it trough Wine but I'm getting errors during installation... ](*,)

---

### Post by JohnCub on 2007-11-15
This is likely a day late and a dollar short but in case anyone else ends up here via google as I did sony provides no linux drivers at all for any of their camcorders (according to the support chat I just had with Charles_)

They suggested  I capture the video using the video/audio out into a capture device.  Since I have no capture device and my camcorder is aging I offered that I'd be more inclined to buy a camcorder that is supported.  I asked if they made a linux compatible model and the answer was no.  He asked if there was anything else he could help with.

I asked if he knew of a manufacturer that did support linux.

No luck.

---

### Post by scorp123 on 2007-11-24
> **glederfein said:**
>  I am trying to connect my Sony DCR-TRV140E camcorder to my computer so I can capture some of the data on it. It is supposed to be very compatible with Linux  I know this is almost 1 year too late .... Just in case anyone is still reading this thread: This camera is _very easy_ to get working with Linux provided that you use the **IEEE-1394 "mini DV" Firewire connector** which is hidden underneath a plastic cover on the camera's front right corner ... It's in front of the handle, or if you look into the camera's lense: it's to the lower left of the lense, right there on the corner where the handle begins. It's not really obvious if you don't know where to look. Just gently push the cover aside (e.g. with your finger nail)and underneath it you will find several connectors; one of which is the **DV OUT port** of the camera.

So obviously you need a Firewire cable and a system that has this type of connector, either built-in or via an expansion card. Apple (duh! :) ... they were the first to have this type of connector on their computers as far as I know), Sony, Fujitsu-Siemens, Toshiba, Dell and HP laptops usually have a DV connector these days so from the hardware point of view it shouldn't be a problem.

However, and that's also non-obvious if you don't know it: On Linux you need to load the right kernel modules (= "device drivers") manually (nope, they don't get loaded automatically!)  or else the camera will never ever be recognized. So to avoid having to do this over and over again I'd put these lines into **/etc/modules** .... for example mine looks like this: ```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
[COLOR="Blue"]ieee1394
ohci1394
raw1394
video1394
[/COLOR]
``` Also ... I'd put the user account you want to use this with into the "video" group (you might otherwise run into permission problems with the device): **System > Administration > Users and Groups** .... Then make sure your user account really is a member of the "video" group.

Once everything is setup: reboot. Just to make sure all the devices get re-initialised properly with the right permissions.

Now when you plugin your camera check the output of the "dmesg" shell command: You should see messages like this in your console (this is from my HP laptop):```
 [ 2037.128000] ieee1394: raw1394: /dev/raw1394 device initialized
[ 2065.464000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[080046010225bef8]
[ 2065.468000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 2066.204000] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
[ 2071.100000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
``` If you get messages like this you can be pretty sure that your camera is now known to your system.

[U]Now as for applications and how to get your stuff off your camera and into your computer: 
[/U]I found **kino** to be very easy for this job. It's like a VCR. You can remote control your camera with "kino" and rewind or fast-forward to the location you want to start to copy from. Both "kino" and your camera will display the content of your tape (cool!). Once you got that far just hit the record button and "kino" will copy the tape in your camera to your Linux system.

_As for DVD's and such:_ 
Please note that the format of the movie data that is written to your Linux system's harddisk is **"Raw DV"** (uncompressed!! **Uses *LOTS* of disk space!** Make sure you got tons of free disk space to spare or else you will run into troubles!)  ... On one hand that "Raw DV" format is OK because it has a high resolution and excellent sound definition. Basically whatever you recorded will be displayed at the maximum quality your camera is capable of (provided you setup your camera to use 16-bit sound and "Normal Play" recording mode ... picture and sound quality suffer greately if you e.g. use 12-bit sound and "Long Play"!). So having a good quality helps a great deal, especially if you want to cut your stuff or add special effects, sub-titles, and so on.

On the other hand all this "Raw DV" stuff that got transferred to your harddisk is not cool because that format is not compatible to any of the modern formats you'd need to create e.g. XVID, DIVX, MP4 or DVD movies. So you'd need to convert your material first into those formats. And because all those formats require lots of compression and calculation you better have a fast dual-core system and plenty of free disk space! Converting e.g. 60 min. of "Raw DV" material into MPEG-2 so it can be used by program such as "k3b" to create a Video-DVD takes lots and lots of time. You'd need to be patient there. I for example do such conversion jobs during the night so I don't have to bother about how long it takes.

I hope this posting was useful ...

---

### Post by scorp123 on 2007-11-24
> **JohnCub said:**
>  They suggested  I capture the video using the video/audio out into a capture device. Since I have no capture device... All you need is a **IEEE-1394 Firewire** connector and Linux and ***EVERY*** camera with a **"DV OUT"** port will happily talk to each other ... there's your "capture device". IEEE-1394 is a hardware-standard and all you need is an OS that supports it. You don't need any special "camera driver" ... well, at least not to get your video taped material into a movie editor on Linux.

> **JohnCub said:**
>  I asked if they made a linux compatible model and the answer was no. Standard phrase by those underpaid undertrained uninformed support folks. They have their lists and if it says on the list "OS requirement: Windows" then that's the answer you will *always* get, regardless of what the hardware is really capable of.

Fact is: So far I had no troubles whatsoever to copy movie material from video cameras to my Linux systems via the DV cable ... "DV" is a hardware standard so all devices with a DV port also talk the same protocol and will therefore work with Linux too (at least this was my experience so far ...).

Hope this posting helped ....

---

### Post by sr20ve on 2007-12-11
> **scorp123 said:**
> All you need is a **IEEE-1394 Firewire** connector and Linux and ***EVERY*** camera with a **"DV OUT"** port will happily talk to each other ... there's your "capture device". IEEE-1394 is a hardware-standard and all you need is an OS that supports it. You don't need any special "camera driver" ... well, at least not to get your video taped material into a movie editor on Linux.

 Standard phrase by those underpaid undertrained uninformed support folks. They have their lists and if it says on the list "OS requirement: Windows" then that's the answer you will *always* get, regardless of what the hardware is really capable of.

Fact is: So far I had no troubles whatsoever to copy movie material from video cameras to my Linux systems via the DV cable ... "DV" is a hardware standard so all devices with a DV port also talk the same protocol and will therefore work with Linux too (at least this was my experience so far ...).

Hope this posting helped ....

Maybe you can help me with my problem then. I have a sony handycam I am trying to capture from using Kino. First I had an issue with the raw1394 module, so I added those modules to /etc/modules, now that's no longer a problem. Now it just seems like it is not detecting the camera when it's plugged in and turned on. The camera is set to the right mode. dmesg doesn't indicate that it's turning on. It's a brand new firewire cable, although, I don't have anything else to test it with. Any ideas?

---

### Post by scorp123 on 2007-12-12
Do you get any messages in "dmesg" at all? The camera has to be in "playback" mode, but other than that it's pretty much straightforward. The only thing that comes to my mind here is that maybe your firewire chipset doesn't get recognised? Do you have it listed e.g. in "lspci"?  When I do that here I get e.g. this: ```
# lspci

08:03.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
``` ... What do you get? Does your system list any firewire controller?

---

### Post by sr20ve on 2007-12-12
> **scorp123 said:**
> Do you get any messages in "dmesg" at all? The camera has to be in "playback" mode, but other than that it's pretty much straightforward. The only thing that comes to my mind here is that maybe your firewire chipset doesn't get recognised? Do you have it listed e.g. in "lspci"?  When I do that here I get e.g. this: ```
# lspci

08:03.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
``` ... What do you get? Does your system list any firewire controller?

Yes, I do get
> [ 2037.128000] ieee1394: raw1394: /dev/raw1394 device initialized
in dmesg.

And yes, it does show up in lspci, and the camera is in playback mode.

---

### Post by scorp123 on 2007-12-12
Another thing worth to check ... What are the permissions on those firewire-related device files? Is your normal user account member of those groups (in my case: "video" and "disk", because /dev/raw1394 and /dev/video1394/0 belong to those groups)?

If your normal user doesn't have the right permissions (ie. you're not member of the right groups) then "kino" won't be able to talk to the camera.

---

### Post by sr20ve on 2007-12-12
> **scorp123 said:**
> Another thing worth to check ... What are the permissions on those firewire-related device files? Is your normal user account member of those groups (in my case: "video" and "disk", because /dev/raw1394 and /dev/video1394/0 belong to those groups)?

If your normal user doesn't have the right permissions (ie. you're not member of the right groups) then "kino" won't be able to talk to the camera.

I'm running Kino as root, so it shouldn't be a permission issue. If I don't run Kino as root, then I do get permission errors because I haven't added my account to either of those groups.

---

### Post by scorp123 on 2007-12-12
> **sr20ve said:**
> I'm running Kino as root Not a wise thing to do! Running GUI stuff as "root" is rather risky, lots of things never supposed to have any significant powers all of a sudden enjoy the unlimited + unrestricted powers of the "root" account ... that's not good. It's very easy to hose your system like that. It would be better if you worked under your normal account and fixed the permission problems ... But OK, it's your system. I just hope you know what you do. :)

I'd recommend you check your camera on a friend's system (e.g. with the help of the Ubuntu Live CD in case they're not Linux users so you don't have to touch their harddisk in any way) and try a different camera on your system. 

I know out of experience that any camcorder with a DV-out port should work tip top, e.g. I once had a friend's Panasonic camcorder here and I had no trouble downloading the movie on its tape via "kino"; on another occasion my father dropped by and he happened to have his JVC camcorder with him, so I tried that one too ... worked tip top. Same for some other Sony camcorders I was able to get my hands on.

Did you ever test your camera on Windows or MacOS? Does it work there? Just to be sure your camera's DV port isn't dead for some odd reason ...

---

### Post by sr20ve on 2007-12-12
> **scorp123 said:**
> Not a wise thing to do! Running GUI stuff as "root" is rather risky, lots of things never supposed to have any significant powers all of a sudden enjoy the unlimited + unrestricted powers of the "root" account ... that's not good. It's very easy to hose your system like that. It would be better if you worked under your normal account and fixed the permission problems ... But OK, it's your system. I just hope you know what you do. :)

I'd recommend you check your camera on a friend's system (e.g. with the help of the Ubuntu Live CD in case they're not Linux users so you don't have to touch their harddisk in any way) and try a different camera on your system. 

I know out of experience that any camcorder with a DV-out port should work tip top, e.g. I once had a friend's Panasonic camcorder here and I had no trouble downloading the movie on its tape via "kino"; on another occasion my father dropped by and he happened to have his JVC camcorder with him, so I tried that one too ... worked tip top. Same for some other Sony camcorders I was able to get my hands on.

Did you ever test your camera on Windows or MacOS? Does it work there? Just to be sure your camera's DV port isn't dead for some odd reason ...

Thanks for the advice. I know running Kino as root is not the best idea, but I wanted to get this working right, then go back and fix the permission issues so it can be ran as a normal user.

I've never had problems capturing video in Windows using Sony Vegas, so it's not the camera. I'm wondering about the cable though. I'm going to have to find a way to test this cable on another computer.

I'm trying to get this to work on my laptop with a 4 pin to 4 pin firewire cable. I don't have anything else that will use a 4-4 firewire cable. What I can do, to make sure I'm doing everything right, is try to set this all up on my desktop using my 4-6 pin cable and see if I run into issues.

Meanwhile, I'm going to have to find a way to test this 4-4 pin cable. Maybe I'll just go buy another cable, then return it if it doesn't fix the issue.

---

### Post by sr20ve on 2007-12-27
Just to update my situation, it turns out I did indeed have a bad cable.

---

### Post by scorp123 on 2007-12-27
> **sr20ve said:**
> Just to update my situation, it turns out I did indeed have a bad cable. So everything works now? Cool :)

---

### Post by steveyeager on 2008-02-16
I have been following this post and would like to see if anyone can help me activate my firewire.

If I boot my pc to linux with my expresscard firewire card inserted, it works.  I can run kino (as myself and do not need sudo) and it captures.  However, if I start up my computer without the firewire card inserted, it will not work.  I ran the commands:

sudo /sbin/modprobe raw1394
sudo /sbin/modprobe dv1394
sudo mknod /dev/video1394 c 172 0

and I can find all these files afterwards.  However, starting kino (as myself and with sudo) says: WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!

ls -l /dev/*1394

crw-rw-rw- 1 root disk 171, 0 2008-02-16 08:59 /dev/raw1394
crw-r--r-- 1 root root 172, 0 2008-02-16 11:11 /dev/video1394

so, what is wrong?

---

### Post by scorp123 on 2008-02-16
See one of my earlier postings again. You have to make sure that your user is a member of the groups the devices get assigned to.

Also: You may want to compare the output of "lsmod", e.g. once when you reboot with the card already inserted and once when you reboot when you inserted the card afterwards ... Just to check if there is a difference --and that's probably the case here-- in which order the modules got loaded.

My suggestion would be to leave the Firewire card in your laptop ... unless you need the card slot for something else? Most modern laptops these days have all the stuff such as Bluetooth, WLAN, LAN, etc. "on-board", so if there is not really a reason to remove the card I'd just leave it inserted.

---

### Post by Rebelli0us on 2008-06-07
same prob here, I'm trying to capture & burn DVDs from Sony camcorder DCR-HC26 via firewire cable. Kino says:

The IEEE 1394 subsystem is not responding.The raw1394 module must be loaded, and you must have read & write access to /dev/raw1394

What does that mean?




BTW Firefox 3.0 amd/or these forums are not working so good, I could barely post this....

---

### Post by scorp123 on 2008-06-08
> **Rebelli0us said:**
> Kino says:

The IEEE 1394 subsystem is not responding.The raw1394 module must be loaded, and you must have read & write access to /dev/raw1394

What does that mean? How about reading posting #19? I put it there for a reason, you know :)

---

### Post by Rebelli0us on 2008-06-09
> **scorp123 said:**
> How about reading posting #19? I put it there for a reason, you know :)

Thank you, I read your post. I'm a newbie and don't know how to "load the right kernel modules", I'll have to work on that :) Isn't there an easier way? I'm trying not edit system files manually if I don't understand what I'm doing.

---

### Post by Corvair on 2008-06-10
I have a Sony DCR-TR7000 camcorder and I could not get it to capture
video. I use an IEEE 1394 connection.

This thread has helped me to get it working.

Thank you very much.

---

### Post by scorp123 on 2008-06-12
> **Rebelli0us said:**
>  I'm a newbie and don't know how to "load the right kernel modules" Well, then simply tell me where you get stuck, e.g. at which step? Other than that I was under the impression that I pretty much explained it all in all the necessary details :)

But if you still run into troubles then please tell me where exactly and I can try and help out.

> **Rebelli0us said:**
>  Isn't there an easier way?  Hmmm .. Editing a few lines in a config file and in return having each and every digital video camera on this planet ever produced by any manufacturor and any brand work 100% with your Linux system (for as long as both have the necessary "DV" interface) ....? Uhhhhm, sorry no. :)

> **Rebelli0us said:**
>  I'm trying not edit system files manually if I don't understand what I'm doing.  Good. But then again I was under the impression that I gave detailed explanations why the files needed to be modified and what those modifications are good for?

---

### Post by scorp123 on 2008-06-12
> **Corvair said:**
> I have a Sony DCR-TR7000 camcorder and I could not get it to capture video. This thread has helped me to get it working. Thank you very much. You're welcome :)

---

