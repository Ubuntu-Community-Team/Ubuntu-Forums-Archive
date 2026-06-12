---
title: "New Hard Disk Error  ( partition table is bad )"
date: 2011-09-16
forum: Hardware
---

### Post by CheAmr on 2011-09-16
I just bought a new hard disk ( western digital 750GB ) 
and when I opened partition magic 8 on windows 7 it tells me "partition table is bad " then the partition magic stops 

I tried formatting it through ubuntu but it failed with this error 
```

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error

```


I don't know what to do , windows cannot read or view the hard disk and same things with ubuntu .. please help 

Thanks in Advance

---

### Post by nickleboyblue on 2011-09-16
Input/output error: sounds to me like the drive's physical connections may be a little loose, or the motherboard doesn't recognize the hard drive (which does happen from time to time).  Check with your motherboard's documentation to check that angle, and make sure that all of the cables are securely connected.

Also, though I have never experienced this myself, while building computers, it is best to do so with a grounding wrist strap so you don't fry your hardware.  Though this is a remote possibility, it IS a possibility.  Also, try turning on your computer with the case open and see if you can hear the hd making any startup sounds.  If it's solid state, this will obviously not happen, but if it's a traditional hard drive, it will probably make some noise.  If it does not, you may have a faulty drive.

---

### Post by CheAmr on 2011-09-19
> **nickleboyblue said:**
> Input/output error: sounds to me like the drive's physical connections may be a little loose, or the motherboard doesn't recognize the hard drive (which does happen from time to time).  Check with your motherboard's documentation to check that angle, and make sure that all of the cables are securely connected.

Also, though I have never experienced this myself, while building computers, it is best to do so with a grounding wrist strap so you don't fry your hardware.  Though this is a remote possibility, it IS a possibility.  Also, try turning on your computer with the case open and see if you can hear the hd making any startup sounds.  If it's solid state, this will obviously not happen, but if it's a traditional hard drive, it will probably make some noise.  If it does not, you may have a faulty drive.

your right , I even tried to 0 fill it and it gave me ETA 406 hours ! :s lol 

I just replaced it with another one 

thank you :)

---

