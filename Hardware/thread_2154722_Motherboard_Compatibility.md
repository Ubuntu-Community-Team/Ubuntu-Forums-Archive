---
title: "Motherboard Compatibility"
date: 2013-06-15
forum: Hardware
---

### Post by GUZZLR on 2013-06-15
Hello All,
I've not built a computer with the intent of running Linux.  This computer will probably have two drives for separate operating systems (Linux & Windows 7).  Is there a compatibility list out there, or does anybody have suggestions or success stories for the Mobo they are using.  I suppose I tend to lean towards ASUS and AMD on a microATX.
Also, I need to stay away from the new BIOS setup...cant remember the name...EUVI maybe.  
Thoughts
Thanks for the help

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by GUZZLR on 2013-06-15
Thanks, are you running windows 7 64bit in your other drive?

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by oldfred on 2013-06-15
If not using Windows 8 pre-installed UEFI works for most systems. 

But how you boot install media for both Windows & Ubuntu is how it will install. So if you want BIOS be sure to turn on BIOS/CSM/Legacy in UEFI/BIOS and boot installer in BIOS mode.

But all very new hardware may have some issues and require some work arounds with Linux as vendors do not really support Linux and the developers have to learn what they did differently with a new system and update drivers or even kernel.

---

### Post by GUZZLR on 2013-06-15
```
But how you boot install media for both Windows & Ubuntu is how it  will install. So if you want BIOS be sure to turn on BIOS/CSM/Legacy in  UEFI/BIOS and boot installer in BIOS mode.

```

Now that I think about it, I suppose I need not even worry about the newer UEFI as Linux will be on a completely seperate drive, and windows on my other.  For example, I am currently running Linux on an exteranl drive now, with Win7 Pro on my internal C: drive on a laptop,  I changed the Bios around to boot from the external first.  So, I just turn on the exteranl (on/off switch on the case) and it boots into Linux.  If I want Windows, I turn off the external, and it boots to windows. 
When I installe Linux (over and over again due to NVidia issues which is another story), I completely remove the internal drive so there is no way it could get mess with the windows O/S; plus, I purposely do not run grub update after the install and reinstall of the original interanal drive.  I think this way, the two O/S are completely away from themselves.
So, If I have two drives on the new project desktop computer, when I install Linux, I'll simply unhook my Windows drive, and load Linux on the second drive.  So again, I dont think whch BIOS would matter, since grub and MBR never mix...
Thoughts welcome!
Thanks

---

### Post by oldfred on 2013-06-15
The only issue is that UEFI and BIOS write hardware system info differently for operating system to use. So if not installed in the same mode you have to go into BIOS or UEFI and change to correct mode to boot. It is not critical which mode you use, just that they must be the same.

---

