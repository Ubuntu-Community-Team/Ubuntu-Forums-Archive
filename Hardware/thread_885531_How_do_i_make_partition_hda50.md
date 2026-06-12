---
title: "How do i make partition hda50"
date: 2008-08-10
forum: Hardware
---

### Post by Dozerman on 2008-08-10
I wonder if someone can help with this,
I'm trying to install xubuntu onto a hardmodded xbox (with the Cromwell bootloader and a 500gb hdd). When i try to install i get an error "cannot mount special device /dev/hda50" I think its looking for the original xbox drive to install on, which i dont have (its run xebian for the last 6 months), is it possible to partition a drive with a specified device number, IE i need to make four partitions hda50, hda51, hda55 and hda56 what is the best way to go about doing this.

Thanx in advance

Dozer

---

### Post by RedPandaFox on 2008-08-11
Is this a new drive you are installing or was this the one you has the other OS on while in the xbox?

---

### Post by Dozerman on 2008-08-11
> **RedPandaFox said:**
> Is this a new drive you are installing or was this the one you has the other OS on while in the xbox?

It is a brand new unformatted and unpartitioned 500gb Maxtor drive. The old xbox drive died. I also have a western digital 500gb drive that has Xebian installed.


Edit: I found a command that might do what i want :- MAKEDEV, but i dont know how to use it.

Thanx

Dozer

---

### Post by sayad on 2008-08-11
If it is an unformatted brandnew hdd , the you should and should afcourse format it and theen go for using it.
Then afcourse for your MAKEDEV , MAKEDEV is a program that will create the devices in /dev used to interface with drivers in the kernel. 

Note that programs giving the error ``ENOENT: No such file or directory'' normally means that the device file is missing, whereas ``ENODEV: No such device'' normally means the kernel does not have the driver configured or loaded.

---

### Post by RedPandaFox on 2008-08-11
Has the previous HDD lost everything? unfortunetley from my experience with modding Xbox's there is some file needed for the HDD to recognise the MoBo, without that file the HDD wont work in the system, Kinda like Microsoft saying to us all "HAHAHA Suckers! Think you can outsmart me!?!" But leaving it still relatively easy to mod, you just need the file. Something to do with the BIOS I believe.
Do a bit of research.
I haven't switched my HDD yet as my networking to PC wouldn't work as it should, so I cant backup the file. 
I was attempting the mod a while ago, so I forget exact how-to, but I'm living quite happily with soft mod I have installed

---

### Post by Dozerman on 2008-08-12
> **RedPandaFox said:**
> Has the previous HDD lost everything? unfortunetley from my experience with modding Xbox's there is some file needed for the HDD to recognise the MoBo, without that file the HDD wont work in the system, Kinda like Microsoft saying to us all "HAHAHA Suckers! Think you can outsmart me!?!" But leaving it still relatively easy to mod, you just need the file. Something to do with the BIOS I believe.
Do a bit of research.
I haven't switched my HDD yet as my networking to PC wouldn't work as it should, so I cant backup the file. 
I was attempting the mod a while ago, so I forget exact how-to, but I'm living quite happily with soft mod I have installed

Thanx for your help, I flashed cromwell to the bios and it now runs xebian without any problems. I'd like to try xubuntu on the new drive. I can see the drive when i run gparted from xubuntu live cd, but when i try to install it, the installer seems to be looking for device hda50, cant find it and fails (hda50 is a partition on an original xbox drive). Also the whole of the drive is formatted as swap. It seems as tho the installer is looking for an original xbox drive's partitions, but, i dont know how to recreate them on a new drive.

---

### Post by RedPandaFox on 2008-08-12
I think I also remember reading somewhere that the BIOS will only recognise to a certain size HDD, but there is a way around it. My sisters partner has a 300gb HDD I think on his. His is Hard modded, mine is soft modded.

[http://www.copying-xbox-games.com/tutorials.php?tutorialid=00000032](http://www.copying-xbox-games.com/tutorials.php?tutorialid=00000032)

Now I THINK this is the site I used while trying to upgrade my HDD, but it does say you need a perfect copy of the original HDD.

Maybe a little more searching will bring up more help? :)

---

