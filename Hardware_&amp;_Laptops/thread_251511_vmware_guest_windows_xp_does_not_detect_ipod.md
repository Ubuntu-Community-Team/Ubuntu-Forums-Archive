---
title: "vmware guest windows xp does not detect ipod"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by robinsingh on 2006-09-05
Hi 
I have a dual boot Dell inpiron 9400
1) first OS is Ubuntu 606 Dapper Drake with Vmware SErver 1.0 (with Windows XP Pro as a guest OS) . 
2) The second OS in this dual boot  setup is Win XP Home.

Problem:
When running the first OS, (Ubuntu) , When I plugin my Apple Ipod , only Ubuntu detects it instantaneously. I want my Windows XP Pro to detect it as well. 
Essentially, I have a bunch of windows softwares that I want to install from iPod into windows XP pro guest OS. 

Having said that, if I insert any CD/DVD into my DVD R-W drive, 
both Ubuntu and WinxP detect it. 
I know I can burn my software from iPod on DVDs and then use it in my guest Windows XP but that will be my last option. 

I am pretty sure, there must be some easy way to force WinXP Pro. to detect the iPod at least as a external USB drive. 
by changing some vmware (or ubuntu) settings. 

On a separate note, my second dual boot OS Win XP home (when running) can easily detect iPod as soon as I plug it in. 
Seems like I need to change some vmWAre setting to force my guest OS (win XP Pro) to detect my USB device (iPod).

Any help would be appreciated, 
robin.

---

### Post by x64Jimbo on 2006-09-05
Under the VM menu, there is a "removable devices" sub-menu that will allow you to pass USB devices through into the guest OS. Give that a shot.

---

### Post by robinsingh on 2006-09-09
Thanks for your tip. 
I tried this. Added a usb controller device from VM guest settings. Then turned on the USB device (ipod) from VM submenu as suggested by you.  Windows XP immediately detected my iPod but gave a message 
"a Hi-speed Usb device is plugged in into Non_hiSpeed USB port" .. tries to confiure, then gives an error "there's been a problem configuring your new hardware, it might not work correctly"
And the device manager shows a yellow exclamation beside the  usb controller device. And that renders my ipod not usable in Windows . Back to Square one. :-(
Any Suggestions. 
Thanks in advance. 
robin

---

### Post by x64Jimbo on 2006-09-10
Hmmmm... Apparently there is not a need to use vmware for ipods now since Ubuntu supports them natively
[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

---

### Post by hampton275 on 2006-09-11
TBH, 
    After having a lot of "known" issues with gtkpod and 5th gen ipod I would rather use vmware/iTunes. I have done a lot of checking and to get full functionality out of the Ipod Video, I will need at best 3 programs(see below). If all of these worked fine that would be ok, but Linux is just having too much of a tough time with this and since I have vmware for work anyway, it would be the easiest way.
     Anyone have a solution on the detection issue for the Ipod in vmware? Any help would be great!!!

This is what I have found in these forums on syncing, however gtkpod for me is spewing permission rights, so that's a no go. Have beat that issue to death. ;)
*Audio File Syncing (MP3,AAC,Audiobook)
    --> gtkpod
*Album Artwork Syncing
    --> gtkpod (cvs version)
*Photo Syncing
    --> GPixPod or similar program
*Podcast Subscribing/Syncing
    --> iPodder / Amarok or a simalar program (to subscribe to the Podcast) and gtkpod (to sync to iPod)
*Calendar Syncing
    --> any calendar program that can "Save As" iCal files (ex. Kontact, Ximian Evolution)
*Contact Syncing
    --> any contact program that can "Save As" vCard files (ex. Kontact, Ximian Evolution)
*Video Syncing
    --> gtkpod (cvs version)

---

### Post by SirKillalot on 2006-09-14
vmware doesnt support the ipod yet, i read that a hundred times in the vmware forums.
regards

---

### Post by komputes on 2008-06-11
I have used the following instructions to get VMware server 1.0.6 installed on Hardy.

[http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

The USB throughput seems to be broken.

I have absolutely no USB devices on my server running VMware Server 1.0.6.

Luckily, I am also running 1.0.3, where all the devices (including my iPod) are able to be passed through to to the Guest OS. Is anyone able to use VMware server 1.0.6 and throughput the USB controller + devices into an XP guest OS?

---

