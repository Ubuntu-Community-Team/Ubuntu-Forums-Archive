---
title: "Possible to use Hi-MD Minidisc player/recorders w/ linux?"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by hollywoodb on 2006-04-03
I'm looking into getting a sony Hi-MD Minidisc player/recorder as an alternative to limited storage mp3 players.  If you haven't checked them out, do it.

Anyways, I have a few questions:

1) Has anyone successfully used linux to store music to a minidisc player of any sort, the old standard or Hi-MD?  Success or failure stories?

2) The Sony Hi-MD devices can supposedly store files of any type, so I wonder if the device itself would be recognized as USB mass storage? Anyone can comment on this?

3) If it isn't possible to use the device natively in linux, I do have WinXP available via vmware for the few rare things I can't do with wine.  Has anyone used USB devices with WinXP via vmware and could comment on compatibility and such?  The Sony players come with software that lets you store music to a disc @ 100x speed (so they claim).  If this software would work well in vmware that is a viable option for me as well.  I've never actually tried to use a USB device with WinXP via vmware and I don't have one handy to test with.

4) It doesn't seem that the Sony Hi-MD devices have ogg support.  I rip every CD I buy to ogg format to have the tracks handy for listening.  How is ogg->mp3 conversion quality-wise if that's my only option for getting those tracks onto the device. I have no idea if the Sony software supports converting unsupported formats or if I have to do it manually.

---

### Post by djroadrash on 2006-04-21
hi i got a md player and hate it. it is lovely if you use windows and dont mind the sony antipiracy software that gets installed with the program, it only will let u record to minidisc the same song 3 times and then you cant. crap, any way i tried to conect the md to ubuntu and it did not work natively, so if there is a solution (doubtful since the files are proprietary of sony, they are not even mp3) i dont know it. md's would be nice if they recorded mp3, but as it is they only work on windows, maybe with wine you could use it on ubuntu, i dont know. im trying to see if i can change the software in the minidisc to a linux player, dont know if it is posible.
dont support sony, they suck
my humble opinion

---

### Post by marvinthesad on 2006-05-11
Hi.

2.) I have one sitting here and got it to be recognized as a usb mass storage device (without partition table, so mount /dev/sda /mnt/test -t vfat). So storage works fine.

Playing the proprietary format is fine, but as far as I know, you would need windows software to transfer your musi into to this proprietary format. ](*,) 

3.) And I have actually used USB devices with Win2k (who wants WinXP anyway), this works quite well, so if the sony software just uses the usual usb-storage facility, which I would guess, bringing it to work under Win2k should be very likely. (I don't have the software handy :( )

4.) ogg - mp3 conversion in general is very lossy of course, but if you use the minidisc player as jogging gadget, you would mind too much the quality, I guess. As I don't have the software, I guess, you would have to convert manually. google for a script...

cheers


just found more info: [http://en.wikipedia.org/wiki/Minidisk](http://en.wikipedia.org/wiki/Minidisk), have a look at the links there. It seems to me an improbable task to get a linux software writing onto the sony.

I wish there was a flash/HD recorder with the same capabilities as the sonys. (line-in, mic in, choose several compression bitrates, very nice)...

---

