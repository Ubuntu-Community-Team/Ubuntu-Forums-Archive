---
title: "Android Nexus 5 pictures absent in Thunar"
date: 2015-12-02
forum: Hardware
---

### Post by dez93_2000 on 2015-12-02
When I connect my Nexus 5 to either my laptop or desktop (both xubuntu 15.10) either in MTP or PTP, the DCIM folder is empty, except for the .thumbnails folder (it's not a hidden files problem) which has the thumbnails. Astro (android file manager) shows the pics in the DCIM folder & android photo apps show them also. The phone is mounted, says it has root permissions, and isn't present in /media. I think this may be new to 15.10; I'm using Thunar 1.6.10.

Any thoughts? Thanks!

---

### Post by furtom on 2015-12-02
> **dez93_2000 said:**
> The phone is mounted, says it has root permissions, and isn't present in /media. 

I'm not quite understanding here. Where is the phone mounted?

Let's first check the obvious. Whereever it is, cd into it and check the output of "ls" 

If you don't know what I mean, post back with the full path to your DCIM folder in ubuntu.

---

### Post by dez93_2000 on 2015-12-02
> Where is the phone mounted?

mtp://[usb:002,004]/Internal storage/DCIM/

> cd into it and check the output of "ls"

bash: cd: mtp://[usb:002,004]/: No such file or directory  :(

So yeah, odd. If I right click on it in thunar it gives me an "unmount" option suggesting it's already mounted (and since I can see the folders and their contents, that seems reasonable), but it's not in /media.
Thanks for your help/time!

---

### Post by furtom on 2015-12-03
> **dez93_2000 said:**
> mtp://[usb:002,004]/Internal storage/DCIM/



bash: cd: mtp://[usb:002,004]/: No such file or directory  :(

So yeah, odd. If I right click on it in thunar it gives me an "unmount" option suggesting it's already mounted (and since I can see the folders and their contents, that seems reasonable), but it's not in /media.
Thanks for your help/time!

Make sure you don't have that extra colon in the command. It's just:

```
cd mtp://[usb:002,004]/Internal storage/DCIM/
```

---

### Post by dez93_2000 on 2015-12-03
ah, I didn't in the command, that's just how the failure message prints out.

---

### Post by furtom on 2015-12-03
OK. good! When I have a chance, I'll go home and mount my phone and see what I can gleen from it... Hopefully someone else will chime in. :)

---

### Post by dez93_2000 on 2015-12-05
Hey Tom, did you have a chance to plug 'er in and see if the pics apppeared? Cheers!

---

### Post by furtom on 2015-12-07
I'm sorry, my friend, I haven't. Busy weekend. I'll try first chance I get.

---

### Post by efflandt on 2015-12-07
I figured out where a USB connected Android phone (S3 in my case) mounts in 14.04 at least. When I hovered over the phone in nautilus it said mtp://[usb:002,007]/ (which you cannot cd to because it is a network URL not a mount point). But I did find where it mounted in my home directory (the 2nd store_... is my microSD card) even though it is mounted as mtp and not ptp:```
efflandt@XPS-8100-1404:~$ ls .gvfs
gphoto2 mount on usb%3A002,007

efflandt@XPS-8100-1404:~$ ls .gvfs/gphoto2\ mount\ on\ usb%3A002\,007/
store_00010001  store_00020002

efflandt@XPS-8100-1404:~$ ls .gvfs/gphoto2\ mount\ on\ usb%3A002\,007/store_00010001
2014-04-29-14-16-07.jpg  ChatON                     files              Melrose Park.txt  Playlists          Sounds
2014-08-04-14-33-51.jpg  data                       Fill_and_Sign_PDF  mobi_drm          Podcasts           storage
airdroid                 DCIM                       FortyTwoSDK        Mom-mobile.txt    QrDroid            telenav70
Alarms                   debug_logs                 gameloft           Movies            Ringtones          TF2 SPREADSHEET.txt
Android                  DE-Exchange-owa-error.png  gamepad            Music             samsungapps        wdh_update
Application              documents                  INDI               Nearby            ShareShot          ZCV-04-2.txt
beam                     Download                   iPad.txt           Notifications     ShareViaWiFi
burstlyImageCache        Elgin T-1.txt              log.txt            Pictures          SheadSpreet_files
```I guess I should move those files that I put in the internal /.

---

### Post by dez93_2000 on 2015-12-12
interesting, thanks efflandt. No joy at my end: nothing in gvfs.
Weirdly, music is also an empty folder whether I mount as mtp or ptp. I can't for the life of me understand whose changed what in android 6 or (x)ubuntu 15.10 but it seems insane that such basic functionality isn't working. BOO!

---

### Post by dez93_2000 on 2015-12-17
Ended up using SSHdroid to connect via wifi network, per a suggestion from a chap on Reddit. Not an ideal situation though - leaving this open in case anyone knows any more.

Additional info@ I upgraded to 6.0.1; DCIM still empty but Music now showing only the folders I've recently added through SSHdroid, and not all folders, despite there being loads more in the same folder. Goodness knows how some must be 'flagged' as different...Possibly by transferring them through MTP before they're flagged as mtp, whereas going through SSHdroid adds no flag?

---

