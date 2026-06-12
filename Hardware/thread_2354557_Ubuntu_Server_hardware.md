---
title: "Ubuntu Server hardware"
date: 2017-03-03
forum: Hardware
---

### Post by Dridhas on 2017-03-03
Hello all,

i hope everybody is doing well.

i have come across a dilemma on which hardware to use for a home-cloud server (owncloud/nextcloud) using ubuntu server CLI.

the hardware that ive been looking into:
- Lenovo IdeaCentre Q150 / Dell Optiplex FX160
- Stick computer
- Raspberri Pi

im looking for something like a small/tiny factor in order to have it out of sight and not that noisy (fan).

can you please provide me an input on which would be better to use?

Thanks!

---

### Post by DuckHook on 2017-03-04
That is a wide range of HW that you are considering, and the answer will depend on your needs:

[LIST=1]
[*]What throughput are you looking for?
[*]Is reliability/uptime important?
[*]Will your usage be CPU-intensive (example: running vitual machines)?
[*]What services do you want in the cloud?
[/LIST]

---

### Post by Dridhas on 2017-03-04
basically, i will have this to run either owncloud or nextcloud for the family.

nothing fancy.

---

### Post by howefield on 2017-03-04
> **Dridhas said:**
> basically, i will have this to run either owncloud or nextcloud for the family.

I use a Raspberry Pi for an owncloud setup, it is the model B so quite a way from the latest iteration but works very well.

I do disable most owncloud "apps" as I don't need much more than the basic file syncing and I have an external disk attached mainly for robustness not trusting the SD card to hold up for too long although a good card these days is probably good enough.

So there you go, a vote for the pi, with the caveat that if you want to do more than run owncloud/nextcloud with it then you probably want one of the other options. Build in a little future proofing :)

---

### Post by Dridhas on 2017-03-04
thanks for the input. im gonna go ahead and get me a pi 3.

then, ill have to learn how to configure the external hard drive for the data folder.

---

### Post by DuckHook on 2017-03-04
You might find this interesting: [https://nextcloud.com/box/](https://nextcloud.com/box/)

---

### Post by howefield on 2017-03-05
> **Dridhas said:**
> thanks for the input. im gonna go ahead and get me a pi 3.

then, ill have to learn how to configure the external hard drive for the data folder.

That should be easy enough.. along the lines of creating the mount point, get the UUID of the disk, edit and add the disk to the fstab file, then mount it.

```
sudo mkdir /media/Data
ls -al /dev/disk/by-uuid
sudo nano /ect/fstab
UUID=010bd8f2-e522-4508-af04-cfc9d00c56ea	/media/Data	ext4	defaults	0	0 
sudo mount -a 
```

You have a choice of putting the owncloud /data folder there or using it as extra mounted storage, ie, a local disk.

---

