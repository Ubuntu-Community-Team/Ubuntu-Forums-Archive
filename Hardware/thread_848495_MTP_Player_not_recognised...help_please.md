---
title: "MTP Player not recognised...help please"
date: 2008-07-03
forum: Hardware
---

### Post by valmorel on 2008-07-03
I have an MTP format portable MP3 player (Samsung YPU3J), and am using Ubuntu Hardy. I have downloaded and installed mtpfs, which I understand should allow the player to be seen just like a USB stick, but for some reason, Ubuntu fails to recognise it. It is recognised by both Amarok and Gnomad. I would be very grateful if someone could give me simple instructions to make it automount, if this is indeed possible........thanks D.

---

### Post by valmorel on 2008-07-03
Bump..............please. I have done a ton of forum searching on this, but mostly its related to earlier versions, which seem different, or remains unsolved. Any ideas?????

---

### Post by ElSlunko on 2008-07-03
Do you have libmtp installed?

---

### Post by valmorel on 2008-07-04
> **ElSlunko said:**
> Do you have libmtp installed?
Yes. It shows up in Synaptic as installed

---

### Post by ProbablyX on 2008-07-04
You can't mount MTP units. They have to be used via gnomad or amarok.

On some players there's an option to change modes between MTP and "drive". If your player can do "drive" then it should mount as a USB memory

---

### Post by valmorel on 2008-07-04
> **ProbablyX said:**
> You can't mount MTP units. They have to be used via gnomad or amarok.

On some players there's an option to change modes between MTP and "drive". If your player can do "drive" then it should mount as a USB memory

Ok thanks. The information I have is wrong then, as I was led to believe MTP players could be mounted like drives in 8.04. I use Gnomad and Amarok to manage it now, but for something like a firmware update, it would need to be seen as a drive.

---

### Post by wpiter on 2008-08-22
MTP's can be mounted like external drives...

I had problems with my Zen X-fi under gnomad, however mtpfs did the trick...

Automount however is -as far as I know- still not possible.

Install libmtp, mtptools and mtpfs

then make a mount point

```
$ sudo mkdir /media/MyZen
$ sudo chmod 775 /media/MyZen
```

Connect your player to the usb port and mount the *******

```
$ sudo mtpfs -o allow_other /media/MyZen
```

your device is now lister in /media/MyZen. Change 'MyZen' for any other other name you'd like.

unmount once your done uploading music and other stuff

```
$ sudo umount /media/MyZen
```

Now you can deconnect your player.

If you have now succes make sure your kernel supports usb
```
$ lsusb
```
should give an output like this
```
Bus 007 Device 005: ID 041e:4162 Creative Technology, Ltd
Bus 007 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd
Bus 007 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

My Zen X-fi is listed here as Creative Technology (the manufacturer)

---

### Post by valmorel on 2008-08-22
Wpiter............. thanks for taking the time. In the end, I got fed up with the whole MTP thing, and foud a hack, on 'anythingbutipod' I think it was which explained how to convert the YPU3 to standard USB drive format. Worked like a charm, so now it auto mounts, and can be seen by just about any prog including the fabulous Gpodder podcast management utility.
Oh the joy of freedom.....................

---

### Post by wpiter on 2008-08-25
That's another way of dealing with it... You changed the firmware with an asian version didn't you? That's indeed another option.

---

### Post by valmorel on 2008-08-26
> **wpiter said:**
> That's another way of dealing with it... You changed the firmware with an asian version didn't you? That's indeed another option.

Not sure which country the firmware was intended for, either Asia or maybe Russia. I lose some sorting functionality, but overall for my purposes it is a much better soln.

---

