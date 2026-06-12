---
title: "My installation problem"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by kenailes on 2006-02-17
Trying to install on a desktop for my kids. Ubuntu on my laptop works fine except for the reboot issue that has been addressed elsewhere.  Here is what happeninng on the desktop:

It gets most of the way thru and then throws an error about not being able to copy all the apps over from the CD saying maybe the issue is due to disk space--not possible, it is a 100 G HD and the HD is clean...

So i have reburned the cd three times now, the last time burning at speed 1x--i can't go any slower.  the last time thru, when it said it couldn't copy the programs over, i figured i would try skipping to the next step in the install, but when it goes to reboot for the first time, i get the blue screen that says it is configuring ubuntu, but never goes any further.

i am sure it is something simple, but i am clueless. any suggestions?

---

### Post by uopjohnson on 2006-02-17
have you checked the md5 sum on your downloaded iso files to make sure your download isn't corrupted?  Are you reformatting your hard drive each time?  and are you setting up the partitions manually or automatically?

---

### Post by nixclusive on 2006-02-17
I had the same error about running out of free space when i tried the /var partition to be of only 100 mb

---

### Post by kenailes on 2006-02-17
i will admit i didn't check the md5. i just downloaded the whole thing again.  I guess i need to check it. I am also using the auto partition because I just am not terribly confident in my paritioning skills...any suggestions?

also how do i check the md5?

---

### Post by byen on 2006-02-17
Hey there,
Three things you might want to look for:
1.Make sure you check the md5sum after download (here is a [program]("http://www.nullriver.com/index/products/winmd5sum"))
2.Using lower speed levels helps (I see you are already doing that)
3.If the above two do not work, try using a CD of a different make. It seemed to help some people (cd-make qulaity I guess)

If all the above do not work: That would mean
You need to try an install with the ACPI-off feature
You can try and install taking out all the usb devices on your system

And if all the above do not work... we are always here.
Goodluck!

---

### Post by kenailes on 2006-02-19
okay, i am stumped. i checked the md5, everything is accurate, burned at 1x with a brand new cd from a brand new spindle, same trouble.  I can, however, install just the base system, trouble is I don't know what to do after that in order to stuff installed.  Anyone have any idea why the install keeps bombing?  i know this is a pc capable of having linux installed, because it used to have FC4 on it.  I would rather have ubuntu on it since I am running ubuntu on this laptop.  tough enough learning the ins and outs of one distro, let alone 2...

---

### Post by renzokuken on 2006-02-19
if you have a permanent internet connection (preferably ethernet based) you could try installing just the server (basic components) and then installing the ubuntu-desktop package from the repos via apt-get to bring it up to full Ubuntu spec.

i had several issues when installing Breezy and this solved it.

on the first CD boot screen type "server" and press enter (its says at the bottom so you'll know which one.

let it install through.

when finished you'll be left with a black login terminal screen

simply type

# sudo apt-get install ubuntu-desktop gdm

and wait.........only works with a working net connection though (obviously)

took about an hour for me to do on a 512mb DSL connection

---

