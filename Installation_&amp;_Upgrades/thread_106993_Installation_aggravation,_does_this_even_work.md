---
title: "Installation aggravation, does this even work?"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by dcsleeper on 2005-12-22
The PC: Compaq Celeron 400, matrox agp 4mb, 196 mb ram, 10 gb hd

I've burned SEVEN coasters here. some Optimum, some Fuji media, some with Nero, some with ISOBurner. I get to the about the same place in the install and it fails to read from the cd. It is AFTER: detection, loading other stuff, network, partitioning, host name, etc. Libss10.0.9.07 or something like that is the filename that is the start of having trouble reading. Just to be clear it is about 6% into actually copying the files to the drive. I have tried 3 different cd rom drives in this pc. I have tried burning speeds from 48x to 1x. I have perused these forums for the last two days.

I'd say the image is bad, but I downloaded it twice from two different sites.

As much as I hate MS, this is why people are NOT running to Linux as quickly as some of you out there might think that they should.

I'm frustrated, and I'm tired of screwing around with this distro.

More info: I loaded NT 4.0 from CD on this machine two days ago. No CD read issues at all. I just burned a Puppy Knopix image to the Optimum media at the 48x speed and it booted up just fine. Seems the problem is with the Ubuntu image doesn't it?

Don't even suggest I order a disc.

---

### Post by kairu0 on 2005-12-22
Did you check the MD5SUM of any of the ISOs that you downloaded? If it passes the test then chances are Ubuntu has a problem with your particular hardware configuration.

You can check the MD5SUM against the MD5SUMS files on virtuall any Ubuntu mirror. It's located in the same directory as the ISO images.

And here is a Windows tool for the task (it's freeware):

[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)

---

### Post by dcsleeper on 2005-12-22
yup. MD5 hash is fine.

A hardware problem reading files off of 3 different cd rom drives, unpacking them and writing them to a drive it has already written to?

Seems mighty unlikely. 

More than thumbing my nose at this thing, I'd like to know what the problem is.

---

### Post by dcstar on 2005-12-22
[QUOTE=dcsleeper]The PC: Compaq Celeron 400, matrox agp 4mb, 196 mb ram, 10 gb hd

I've burned SEVEN coasters here. some Optimum, some Fuji media, some with Nero, some with ISOBurner. I get to the about the same place in the install and it fails to read from the cd. It is AFTER: detection, loading other stuff, network, partitioning, host name, etc. Libss10.0.9.07 or something like that is the filename that is the start of having trouble reading. Just to be clear it is about 6% into actually copying the files to the drive. I have tried 3 different cd rom drives in this pc. I have tried burning speeds from 48x to 1x. I have perused these forums for the last two days.
......[/QUOTE]
Is the CD drive a Master on it's own IDE channel, or a Slave on the HD channel?

---

### Post by az on 2005-12-22
[QUOTE=dcsleeper]
As much as I hate MS, this is why people are NOT running to Linux as quickly as some of you out there might think that they should.[/QUOTE]

Actually, that is why Windows comes preinstalled.


[QUOTE=dcsleeper]I'm frustrated, and I'm tired of screwing around with this distro.
[/QUOTE]

No one is pointing a gun to your head.  

1.  Is your motherboard set to overclock the CPU?

2.  Is your CPU overheating?

3.  Did you run memtest for at least a few minutes?

I will have more questions for you, if you need.

---

### Post by dcsleeper on 2005-12-22
The CD is cable select on the secondary channel. The hard drive is cable selecyt on the primary channel. I don't usually use CS but on Compaqs it works better than master/slave.

no CPU overclocking or overheating. In fact this model just has a big sink, no fan. and it's not even warm.

Did not do a mem test but I have been using this PC for months with win98, and now recently with nt 4. I have experience with nt barfing the installation almost immediately with bad memory. Don't suspect it here.

---

### Post by kairu0 on 2005-12-22
Are you certain that the hard drive doesn't have bad sectors?

Is the hard drive the model that came with the computer?

---

### Post by dcsleeper on 2005-12-22
No to both, but it is definitely a cd read error, not a write error. I can hear the cd re-calibrating to track 0. Don't know if that is what you call it, but I think you are familiar with what I mean.

---

### Post by dcsleeper on 2005-12-22
Just updated firmware on the burner. Burned the GNoppix live cd and booted that just fine. I will burn a new UBUNTU tommorow and try that. Thanks for the help and I will keep advised..

---

### Post by scole on 2005-12-22
If it dosent work just order some ubuntu cds their free, if that dosent work replace the cd drive if possible and format the hdd. Then use a partion boot disk aka boot it works great to make a seperate partion of the size u want for ubuntu. (if u plan to multiboot) then delete that partion you made for ubuntu in the ubuntu partion program. select the free space and allow ubuntu to automaticly set up the space.

---

