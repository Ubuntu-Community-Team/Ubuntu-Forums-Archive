---
title: "Acer Aspire One BIOS Update"
date: 2009-08-19
forum: Hardware
---

### Post by Keith Wapshott on 2009-08-19
Hi,
 
I have an Acer Aspire One netbook with Ubuntu netbook remix as the OS
 
The problem I have is that my battery will not charge, Acers response to this is that I need a BIOS update which rectifies this problem
 
The problem I have is that the BIOS updates that are available only seem to be for windows os
 
My Acer Aspire One originally had linpus as its OS
 
I am not sure how to proceed from here, I need a BIOS update but I can not find any for linux/ubuntu on the Acer website.
 
Any help or guidance will be gratefully received.
 
Regards,
 
Keith

---

### Post by coldReactive on 2009-08-19
You'll have to install windows onto your aspire one to do a BIOS update. It is *_**extremely**_* unrecommended for you to use WINE to perform a BIOS Update.

Honestly, I can't see why computer companies dropped support for flashing a new BIOS from a floppy disk.

---

### Post by warreno on 2009-08-20
With the Aspire One, there is no floppy at all; you'd have to use a USB floppy drive to flash the BIOS. The drive would probably cost at least twice what the netbook did. That said, USB thumb drive support would be a nice addition.

There might be a workaround to this problem, though: Discharge the battery completely, if you haven't, Keith. Run it flat into the ground. I mean every time the system goes into suspend, hit the power button again to force every last erg of juice out of the battery until *nothing happens at all*. Then try charging it again.

I don't think there's a LiveCD of Windows XP out there, so using that to flash your BIOS may not be possible either.

I have an Aspire One myself, FWIW, but this issue hasn't come up for me … *yet*.

---

### Post by coldReactive on 2009-08-20
> **warreno said:**
> The drive would probably cost at least twice what the netbook did.

Netbooks are a little over 200 USD around here (alone, I don't like getting them with network plans). You can't expect a USB floppy drive to get even over 20 USD (I paid 15 USD for mine.)

---

### Post by Keith Wapshott on 2009-08-20
The battery is as flat as a pancake
 
It just will not charge
 
Acer issued a BIOS upgrade that supposedly address this problem, the only problem is that it is in windows format only.
 
And that is a real PITA, they supply this netbook with a Linux OS as well so why do they only provide a windows based BIOS update?

---

### Post by warreno on 2009-08-20
> **coldReactive said:**
> Netbooks are a little over 200 USD around here (alone, I don't like getting them with network plans). You can't expect a USB floppy drive to get even over 20 USD (I paid 15 USD for mine.)

Wow, you got a bargain on the drive, but not on the netbook. Still, good to know.

---

### Post by warreno on 2009-08-20
<snip>
That was a reply to my suggestion about forcing the battery to discharge totally.

**Keith**, I just Googled [this page]("http://4zzblawg.wordpress.com/2008/11/02/aspire-one-how-to-flash-bios/") that seems to talk about your very problem and seems to present a fix, albeit a sort of bass-ackward workaround kind of fix. But it seems to be targeted specifically at Linux users.

Hope this helps; do let us know.

---

### Post by warreno on 2009-08-20
Oh yeah. The term I Googled was "acer aspire one bios update linux". The URL I posted was the second hit.

I'm not trying to be an *** here; just posting this because it really is amazing how Google can do things the *right* way so often. Which almost makes up for all the times it gets it dead *wrong*.

---

### Post by bapoumba on 2009-08-20
Two posts removed. Please keep it civil, thanks.

---

### Post by Keith Wapshott on 2009-08-20
> **warreno said:**
> <snip>
That was a reply to my suggestion about forcing the battery to discharge totally.
 
**Keith**, I just Googled [this page]("http://4zzblawg.wordpress.com/2008/11/02/aspire-one-how-to-flash-bios/") that seems to talk about your very problem and seems to present a fix, albeit a sort of bass-ackward workaround kind of fix. But it seems to be targeted specifically at Linux users.
 
Hope this helps; do let us know.
 
 
Didn't work :(

---

### Post by warreno on 2009-08-20
> **Keith Wapshott said:**
> Didn't work :(

Aw heck. What did/did not happen?

---

### Post by kixome on 2009-08-20
had the same problem, disconnected andreconected the battery and it began charging

---

### Post by kixome on 2009-08-20
there is an xp live cd, though I don't know if it loads all dlls and such, dont know if it would work but I do have it (its called super pe) if you need a copy then msg me

---

### Post by Aearenda on 2009-08-20
The Linux BIOS upgrade method shown [here]("http://macles.blogspot.com/2008/07/flashing-bios.html") has always worked for me.

---

### Post by warreno on 2009-08-20
> **Aearenda said:**
> The Linux BIOS upgrade method shown [here]("http://macles.blogspot.com/2008/07/flashing-bios.html") has always worked for me.

Huh, that seems a lot like the other one I found, though a bit less slangy and from-the-hip. *Nice*.

**Keith**, any luck with this other method?

---

### Post by Keith Wapshott on 2009-08-20
> **Aearenda said:**
> The Linux BIOS upgrade method shown [here]("http://macles.blogspot.com/2008/07/flashing-bios.html") has always worked for me.
 
Yup that did the trick, have flashed my BIOS
 
But.....
 
Despite what Acer said it has not fixed my problem, the battery still wont charge :(
 
Well I guess it means another call to Acer

---

### Post by Keith Wapshott on 2009-08-20
Just want to say thanks to everyone for there help, it is very much appreciated.

---

### Post by warreno on 2009-08-20
> **Keith Wapshott said:**
> Despite what Acer said it has not fixed my problem, the battery still wont charge :(

Ah. Flat battery. I did wonder about that. The idea that a computer's BIOS might somehow affect how the LiIon batteries worked seemed a little off. Along the lines of, "Oh, your car's tires are flat? Well, check to see if there's gas in the tank…"

Oh well, at least if you actually *do* need to upgrade the BIOS someday, you know how. Thanks for the pointer, **Aearenda**. I'm sure I'll need it too eventually. In fact maybe I should make a FreeDOS boot image now and avoid the rush…

---

### Post by Keith Wapshott on 2009-08-20
Yes I did wonder about that myself.
 
They say there was some problem with a BOOS setting that was stopping the battery from charging up and the update was supposed to fix this.

---

### Post by Keith Wapshott on 2009-08-20
Update......
 
Just checked my netbook and it has worked!
 
The battery is now charging!

---

### Post by warreno on 2009-08-20
A'ight, that is officially spooky. Still, excellent news.

---

### Post by Keith Wapshott on 2009-08-20
> **warreno said:**
> A'ight, that is officially spooky. Still, excellent news.
 
Yup!
 
I am now a very happy chappy :)

---

### Post by sepharoth213 on 2010-01-31
I came across this looking for some fix for the unsupported bios crap, I just have to say that the Aspire One has an emergency bios recovery thing,
[http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html)
if you have this kind anyway. I've had to use this twice now, Windows broke my bios a couple times (but only during dual boot with Ubuntu...hmmm).

---

### Post by Thaddeus Morgan on 2010-03-05
First thing I did with my new Acer Aspire One AO532H was to wipe the drive and install UNR 9.10.  It feels good never to accept a EULA.  In order to upgrade the BIOS from 1.02 to 1.18, I did the following:

[LIST=1]
[*]Download BIOS update files from Acer website.
[*]Make note of the contents of the batch file used to update the BIOS.
[*]Download the latest version of FreeDOS.
[*]Install unetbookin (sudo aptitude install unetbookin).
[*]Use unetbookin to create a USB start up disk for FreeDOS.
[*]Copy the BIOS update files onto the USB start up disk.
[*]Boot the AO532H from the USB disk.
[*]Run the command found in the batch BIOS update file, modified to use absolute paths instead of relative paths.
[/LIST]

This update procedure left my UNR 9.10 installation intact and successfully updated the BIOS using only free software.

---

### Post by Vagabond112 on 2011-11-21
I've just updated my Acer notebook (Ubuntu 11.10, AMDx64) bios using unetbootin freedos bootable flash drive, prepared in advance (Kingston traveler, 2GB fat32 filesystem).

There are no instructions on Acer's website on bios updating in Linux OS for my notebook model, and Linux is not officially supported on my model. The update bios archive has only DOS, WIN32 and WIN64 stuff.

After making bootable pen drive, I manually copied the necessary files from the update bios archive. Only bios.bat and contents of DOS folder containing an image and firmware utility were copied to pen drive root.

After test boot, I dir a:\ and dir b:\ in order to check whether freedos system could see anything on my pendrive. It sees its own files at a:\ and the copied bios.batch and update bios files at b:\.
 
I just needed then to edit the bios.batch file manually, as suggested by Thaddeus Morgan, indicating the absolute paths to the utility and image files, adding "b:\" to dos commands contained in the batch file. Thus, the freedos system will know where to take the utility programs and where to take the new bios image.

This exercise reminded me cool old days, before mices and GUIs appearance...

Be very careful before taking a decision to update bios on you own risk using non standard methods. You should absolutely understand what you're doing and what are possible consequences...

---

