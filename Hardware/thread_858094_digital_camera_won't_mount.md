---
title: "digital camera won't mount"
date: 2008-07-13
forum: Hardware
---

### Post by aaronp on 2008-07-13
All,

I have a Canon powershot digital camera which has always auto-mounted as soon as it is plugged into USB under both Gnome and KDE 3.5.
Doing the same thing under KDE4 produces nothing. I used lsusb and the device is appearing in the list but running ```
sg_scan -i
``` only shows me my two hard drives and my DVD-RAM writer.

If I change to a KDE 3.5 session and plug in the camera it auto-mounts and asks me what I want to do with th photos like normal but in KDE4 it doesn't even create an entry in Dolphin.

Any ideas?

thanks
Aaron

---

### Post by matt$2 on 2008-07-13
Now kde4 may have a deficit / bug, or you're not finding it.

Look in /media

That's where they appear these days.

---

### Post by aaronp on 2008-07-14
Thanks but /media is the first place I looked and it isn't there.

Aaron

---

### Post by dirtylobster on 2008-08-17
I have the same problem.

---

### Post by ronocdh on 2008-11-01
I'm having this problem, too. Photo imports (Canon PowerShot A590IS) worked just fine under both GNOME and KDE 3.5, but now that I've migrated to KDE4.1, no luck! I can't get the camera to mount in F-Spot or DigiKam.

I've tried reinstalling all the camera-reading packages available in the repos, to no avail. Still get "Could not lock device" or something similar about the camera not being there, even though DigiKam can correctly autodetect its model number.

---

### Post by richardjones on 2008-11-15
I'm also getting this problem with KDE 4 under Intrepid.

lsusb finds the device:

```
Bus 008 Device 005: ID 04a9:3110 Canon, Inc.
```

there's no errors in syslog:

```
Nov 16 08:53:54 shiny kernel: [ 1629.436023] usb 8-2: new high speed USB device using ehci_hcd and address 5
Nov 16 08:53:54 shiny kernel: [ 1629.589156] usb 8-2: configuration #1 chosen from 1 choice
```

Digikam scan finds it "Canon EOS 400D (PTP mode)" and allows me to grab images from it.

But my preferred method of accessing photos is a straight USB mount, and I can't seem to do that.

---

### Post by TerenceWhite on 2008-11-15
I have the same symptoms on my Intrepid upgrade. My Canon A720IS autodetected on plugin and opened Digicam, which I could then download from. Now plugging in does not autostart Digicam.

lsusb shows
Bus 005 Device 005: ID 04a9:315d Canon, Inc.

Starting Digicam manually allows me to connect to the camera and dl photos.

I've had Hardy on here prior to the upgrade, and the process was working as described in the OP.

---

### Post by Mze on 2008-11-15
Install [f-spot]("http://f-spot.org/Distributors") from the repository and see if it will allow you to transfer images.

Keep your camera in the "Picture Preview" setting when you connect it to your PC.

All the best.

---

### Post by noelvh on 2008-11-16
Hi All,
This is my first time posting to the Ubuntu forums.

I have been using Kubuntu for the last 2 years and moved to the new Kubuntu 8.10, and have the same issue with my Canon PS 710.

I did see there were a number of issues with Kamera and other users. This is a big draw back for me as I use my laptop to do all my photo imports.

I just found a work around to pull the photos off the camera, and that is to use Picasa 3. At first it dose not seem to be working. It see the camera but when you click import it just sets there. Well I left it and took the dog out, and when I came back my son was looking at the photos in Picasa. I finished the import and they are all there.

I installed from the deb from the Picasa web site.

Noel Vh

---

### Post by Bogart on 2009-02-24
I have this same problem with KDE 4.2, I was wondering if it got solved for any of you. It seems to be related to KDE4 and Canon cameras, since we all have Canon cameras and they work in Gnome/KDE3.

---

### Post by nebi on 2009-03-03
Same problem here with kubuntu 8.10. So now i will use f-spot to get my images of my canon camera.

---

### Post by oygle on 2009-03-12
Same problem here, the only way I can get DigiKam to import from my Canon A460 , is to run DigiKam from the terminal.

BUT, I can't see it under /media , and a mount command doesn't show it. I like to check that all pics have been downloaded correctly, by running a file compare, but as it's not 'mounted', it won't show anywhere.

When will this bug be fixed ?

Oygle

---

### Post by stafio on 2009-03-13
Same problem here using a Canon EOS Rebel XS on Ubuntu Intrepid/KDE 4.1. Digikam will autodetect it as a USB PTP Class Camera, but I can't get it to work under "Configure Kamera" in the KDE System Settings.

---

### Post by stafio on 2009-03-13
I found a solution for this. First, you need to install gphotofs through either synaptic or using apt-get. Create a directory in your home folder called "camera".
Mount using the command```
gphotofs ~/camera
```
Unmount using```
fusermount -u ~/camera
```

Reference: [http://forums.debian.net/viewtopic.php?p=208732&sid=45853f911dea9e49fed3f022fcdca097#208897]("http://forums.debian.net/viewtopic.php?p=208732&sid=45853f911dea9e49fed3f022fcdca097#208897")

---

### Post by oygle on 2009-03-16
I installed gphotofs and followed your instructions. Now when I turn the camera on and do the mount with gphotofs, the 'mount' command shows

> gphotofs on ~/camera type fuse.gphotofs (rw,nosuid,nodev,user=*****)


but I cannot browse via Nautilus, and an 'ls' on ~/camera returns 'input/output error'

If it is mounted as a file system, how do I read/access the pics ?

Oygle

---

### Post by baroing on 2009-03-21
Well, at least I'm not alone?  

I'm getting the same problem trying to mount a Canon 400D on my new Kubuntu 8.10 install...it worked fine on 7.04, Konqueror could automount it...tried configuring it in the camera settings, but no love...

---

### Post by Ishimaru Chiaki on 2009-03-22
I see your issue is similar to mine, but on my side, it's under Ubuntu 8.04 with Gnome, and my digicam is a Finepix s1000fd.  I posted about it yesterday.

EDIT on 3:23 a.m UTC-5 DST : Thanks a lot for the hint, I could import my pics using Picasa !

I'll go mark my topic as solved.

---

### Post by stafio on 2009-03-22
> If it is mounted as a file system, how do I read/access the pics ?

In my case, that was all that was necessary. The mount command returns

```
gphotofs on /home/myname/camera type fuse.gphotofs (rw,nosuid,nodev,user=myname)

```

Doing an ls on ~/camera returns 'store_00020001', the directory that exists in the camera.

Update: Doing the same thing on Hardy results in an input/output error for me. It's using Intrepid that it works for me.

---

### Post by liviubero on 2009-04-03
I have a Canon EOS 1000D and I can browse pictures in Konqueror just by going to camera://
Otherwise the camera is not automatically mounted. This is probably because of the ptp-Transfer Protocol the camera is using and not the usb - Protocol.

---

### Post by LyonTamer on 2009-05-02
Same problem here with an Insignia NS-DSC7P09. Worked fine on 8.01, would automount as a media drive, but after batteries died in the camera during an upload, computer no longer automounts. lsusb shows it, but that's as far as I can get. Am installing f-spot to see what happens...

---

### Post by LyonTamer on 2009-05-02
No it did not help, the camera is still not detected.

---

### Post by bricedebrignaisplage on 2009-12-07
Previous post was in may, now december. I just installed Karmic & KDE4 (I was previously running Hardy & KDE3.5). My camera (Canon IXUS 80 IS) was mounted as a directory when I plugged it in Hardy. Now with Karmic it does not appear. I can access it with digikam and gphotofs, but I prefer to have it as a mass storage device...

I also checked under Sid and it's the same problem. I'll post the problem on the KDE forum too.

---

### Post by bricedebrignaisplage on 2009-12-07
Since it seems to be a KDE problem, see the following post:
[http://forum.kde.org/viewtopic.php?f=19&t=84364](http://forum.kde.org/viewtopic.php?f=19&t=84364)

---

### Post by modvavet on 2010-02-09
Actually, have had the same issue today under Xubuntu, I got it mounted w/ gphotofs and am importing w/ F-spot, but it's still a pain in the buttocks :P  Fujifilm FinePix J38, here.

---

### Post by no2498 on 2010-02-09
all cams seem to come up as a card reader
unmount the cam,turn off the computer, do what ever you need to do
take out the card. restart plug the card in
hope this helps
its in the usb some how
i cant pin point it yet

---

### Post by Eagle-Owl on 2010-03-31
Hi All, 

Same issue here , Canon EOS 450D and kubuntu karmic. 
Didn't have a problem with Kubuntu hardy, but since I upgraded to karmic i could not mount my camera anymore. 
This is getting ridiculous and it's bothering me since I do a lot of photography and want to get the pictures.

---

### Post by WamBamBoozle on 2010-03-31
I have this problem with my cannon camera too. It won't usb mount on karmic or any of the previous ubuntu releases either. My solution: don't do that. Get a card reader (mine cost $10 at Target). It's faster and bypasses all the weirdness of Cannon supplying or not supplying a compatible or not compatible USB driver.

---

### Post by manvvip on 2012-03-29
Same problem with 12.10

I have searched the forums and still no answer

Cannot be mounted as it has always been able to.

(canon ixus 100)

Can see it via Digikam. But not through Dolphin.

---

