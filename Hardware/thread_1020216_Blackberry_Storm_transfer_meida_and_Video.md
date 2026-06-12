---
title: "Blackberry Storm transfer meida and Video"
date: 2008-12-23
forum: Hardware
---

### Post by amdefeo on 2008-12-23
So I got my storm the other day, and I was a concerned about syncing it up with Ubuntu. Im running 8.10 Intrepid Ibex the beta version. When I plugged it in initially i got nothing, I played with some of the setting on the device and now it works perfectly, music and videos transfer with no problem. Here are the setting. Options>Memory>Mass Storage Support Change to ON> then, Auto enable Mass Storage Mode When Connected change to YES 

Im not sure if this has any other effects on the device, it seem to be running OK.

Enjoy

---

### Post by mariner09 on 2008-12-24
If you ever want to tether with the barry project, you'll want to make sure to disable or at least set the device to prompt you for the option.  The tethering function won't work when the device is connected as storage.

---

### Post by travisn000 on 2008-12-27
I just got my first Blackberry... Merry Christmas to me!

I was curious if syncing with the Storm works with the barry project (..in ubuntu or elsewhere)?  I'm usually a PCLinuxOS user, but barry hasn't made it into their repositories..  I'm posting from a mandriva install that I thought might let me use barry, but barry-backup and the bidentify command don't seem to see my blackberry storm..  If ubuntu works with the Storm I might have to consider a switch to Kubuntu! :D

FWIW, your tip to enable mass storage mode does work!  Thanks.

---

### Post by mariner09 on 2008-12-27
The storm is pretty new and I don't think the barry developers have gotten a hold of one yet.

The 1st key is to see what the device shows up as as far as an address.  lsusb should show something.

gmane has a barry mailing list.  I found that backup and mounting media worked with the Bold, but tethering was an issue.  I worked with a developer to test various libbarry patches until we got it working.

Does btool -l show it?  You may have to run as root.

---

### Post by travisn000 on 2008-12-28
Hi Mariner.. thanks for the tips.

..it seems to be working this morning!:confused:  

I did a reboot yesterday as I was having issues with acidrip crashing..  something was eating up nearly all 4GB of my ram.  Anyway, seems to be working this morning; I just ran the backup and sync without a hitch, next I might give tethering a try..

For reference, lsusb gives the following:
```
Bus 001 Device 003: ID 0fca:8004 Research In Motion, Ltd.
```

btool -l returns (ID numbers removed):
```
Blackberry devices found:
Device ID: <xxxxxxx>. PIN: <xxxxxx>, Description: RIM BlackBerry Device

```


Thanks again!

---

### Post by travisn000 on 2008-12-28
I just found this link regarding tethering with ubuntu:

[http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux](http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux)

..They are using **Barry** and **XmBlackberry** to get tethering to work; I haven't tried it, but I figured it might help someone.

---

### Post by mojorising on 2008-12-29
This looks a little promising. My company just replaced my ancient Blackberry with a new Curve. I'm going to continue Googling and see what comes up (when I first plugged my phone to my laptop, the Blackberry locked up and went all weird so I'm going to check on a few things before trying that again). 

Please take a look at this online petition to get Blackberry to support Linux. Hopefully we'll eventually get something from them on this that will make the process of connecting Blackberrys to Linux a little easier. 

[http://www.petitiononline.com/bb1d1234/petition.html](http://www.petitiononline.com/bb1d1234/petition.html)


Mike

---

### Post by mariner09 on 2009-01-02
You no longer need XmBlackBerry with the latest releases of Barry.

---

### Post by kidux on 2009-02-11
> **amdefeo said:**
> So I got my storm the other day, and I was a concerned about syncing it up with Ubuntu. Im running 8.10 Intrepid Ibex the beta version. When I plugged it in initially i got nothing, I played with some of the setting on the device and now it works perfectly, music and videos transfer with no problem. Here are the setting. Options>Memory>Mass Storage Support Change to ON> then, Auto enable Mass Storage Mode When Connected change to YES 

Im not sure if this has any other effects on the device, it seem to be running OK.

Enjoy

Thanks so much! I was able to get my Storm to mount now and transfer music. :guitar:

---

