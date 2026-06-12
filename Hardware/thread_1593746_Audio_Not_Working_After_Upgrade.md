---
title: "Audio Not Working After Upgrade"
date: 2010-10-11
forum: Hardware
---

### Post by MikeyDL on 2010-10-11
Hi,

Just upgraded to 10.10 but my audio no longer works.  I did an lshw -c sound output and here is my hardware specs for the laptop I'm on:

  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:f4700000-

Also sound preferences does show an output item for "Internal Audio Analog Stereo".

Any ideas?

Thanks!

---

### Post by MikeyDL on 2010-10-12
Well update here...

I had done an update from my system with 10.04 and the sound went out.  Decided to download a fresh copy and build on a startup usb stick to test if a new rebuild would fix the problem.  Unfortunately, even with a stick boot there is no sound.

Under preferences in the hardware tab there are a variety of setting you can choose from to test the speakers such as analog stereo, digital duplex stereo, etc..  Tried them all and wasn't able to get any sound for my card.

Any tips on how to roll back the drivers to 10.04 or do I need to do a rebuild to 10.04 for this system?

---

### Post by MikeyDL on 2010-10-12
Well...more info.

Did the update on my netbook as well.  Love the new interface layout.  However, same problem with no sound.  A device shows in sound preferences but no sound output for test.  

The device on this netbook is an Intel N10/ICH 7 Family High Definition Audio Controller (rev 02).  

I'm hoping that this is a big enough problem that it will be addressed with a fix.

On a positive not my network which is spotty with both onboard and a usb stick D-Link device seems to be allot more stable.

Really hope there is a solution for this... :(

---

### Post by 98cwitr on 2010-10-12
fresh install of 10.10...im in the same boat, my digital audio isn't working either. I changed it to digital duplex which usually works and nothing is coming out.

> 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)


---

### Post by MikeyDL on 2010-10-12
Well fixed my netbook at least.  

Googling found that there was a user setting under System - Administration - Users and Groups.

When you edit your logon you need to go to the User Privileges tab and check "use audio devices."  That fixed the netbook at least.

For my main acer laptop no luck yet.  A dmidecode command shows the followign for the audio device:"

Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
        Type: Sound
        Status: Disabled
        Description: HD-Audio

So guess it's a driver issue and disabled for now.  Put in a bug report on it and have 13 on the same issue so hoping it gets fixed for my device.

---

### Post by 98cwitr on 2010-10-12
yep, just fixed mine too

```
sudo alsamixer
```

and pressed 'm'...damn thing was muted :?

---

