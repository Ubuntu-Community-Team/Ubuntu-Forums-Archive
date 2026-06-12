---
title: "installing Ubuntu to a thumb/pen drive"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-12-21
Is it possible to install to and run Ubuntu from a USB thumb/key drive ?  I am talking about actually running the O/S from the UBS drive and not just putting a copy of this Ubuntu ISO on a thumb drive.

And if so, is it possible to then run Ubuntu from this same USB thumb drive from **ANY** computer that I might choose to insert the thumb drive in before booting the computer, assuming that the computer/bios allows for booting from a USB device or would it be possible to only boot to and run Ubuntu successfully from this thumb drive on the computer whereon the installation of Ubuntu was performed ?

My research on this so far seems to indicate that this may be possible but the instructions that I have found so far seem to be somewhat convoluted, indicating that this may be more trouble than it might be worth.  Is my impression wrong ?

Thanks.

---

### Post by RedDevilMaestro on 2008-12-21
THIS is the same question I have.

I want to boot the Ubuntu OS direct from the USB Drive (Like how Windows boots from your hard drive).

---

### Post by infamous-online on 2008-12-21
Yes it can be done, however do note that usb flash drives are not anywhere near as fast as a traditional harddrive, so be patient. Also, i would suggest having at least an 8 gig flash drive, because the default installation requires 4 gigs, and that's without updates and such.

---

### Post by SportsGuy2 on 2008-12-21
Thats what I want to do, too, but i can only get the live cd version to work on my flash drive...

---

### Post by infamous-online on 2008-12-21
> **SportsGuy2 said:**
> Thats what I want to do, too, but i can only get the live cd version to work on my flash drive...

so you don't see the option to install ubuntu onto the system at all? how big is the flash drive?

---

### Post by carml on 2008-12-21
There are distro like Puppy and DSL which can be booted also by a USB drive,because they smaller than others distro.:popcorn:

---

### Post by wpshooter on 2008-12-21
> **carml said:**
> There are distro like Puppy and DSL which can be booted also by a USB drive,because they smaller than others distro.:popcorn:

I am not sure that you are understanding my questions.

I want to INSTALL Ubuntu on the USB thumb drive.  NOT just merely have a "Live CD version" on the USB drive that can be booted to and then ran as a "Live Session", i.e. I want the USB thumb drive to hold the installation of the O/S just as you would INSTALL it on an internal IDE or SATA hard drive.

Thanks.

---

### Post by logos34 on 2008-12-21
> **wpshooter said:**
> I am not sure that you are understanding my questions.

I want to INSTALL Ubuntu on the USB thumb drive.  NOT just merely have a "Live CD version" on the USB drive that can be booted to and then ran as a "Live Session", i.e. I want the USB thumb drive to hold the installation of the O/S just as you would INSTALL it on an internal IDE or SATA hard drive.

Thanks.

I believe this is what you're after:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

---

### Post by Pumalite on 2008-12-21
You shoud take a look at this too:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by wpshooter on 2008-12-21
> **Pumalite said:**
> You shoud take a look at this too:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

Thanks for the link.

I did not read every word of this but I still have the question that if I can manage to get Ubuntu installed on the thumb drive using one particular computer, can I then take that thumb drive to any other computer and SUCCESSFULLY run Ubuntu from other computers ?  I really don't see how this would be possible with the fact that the hardware on a computer(s) other than the one that the installation to the USB thumb drive was performed is/are NOT likely to be the same as the hardware that was on the installation computer.

Thanks.

---

### Post by Pumalite on 2008-12-21
If you install a 64 bit version, you cannot use it in a 32 bit computer. Sometimes one has to fix xserver. Beyond that I have had no problems with mine.

---

### Post by wpshooter on 2008-12-21
> **Pumalite said:**
> If you install a 64 bit version, you cannot use it in a 32 bit computer. Sometimes one has to fix xserver. Beyond that I have had no problems with mine.

If I install using a 32 bit computer that is using one type of chipset for the motherboard, video card, etc., etc., are you saying that if I take that USB thumb drive to another 32 bit computer that is using ANOTHER type of chipset for the motherboard, video card, etc., etc., that it will still work with **basically no problems** ?  I hope you are right, but I sort of find that hard to believe !!!

I would like to try this **IF** it will work but I do not have a 8gb or 16gb thumb drive and I would have to buy one to try this with and other than this, I really have no use for a thumb drive of this type.

Thanks.

---

### Post by SportsGuy2 on 2008-12-21
i did the install to the whole disk/flash drive, and it required the flash drive to be plugged in for the boot loader to work, so i couldn't even boot windows up... so i didn't like that.

somebody should figure out how to make a fully functional and portable ubutntu flash drive and make a good tutorial.

---

### Post by adult swim on 2008-12-21
you can install ubuntu on an external hard drive that you can take from computer to computer.  note, however, this is only possible if the computers you are planning to use are able to boot from a usb device.  also note that this is going to wipe everything on the external drive so back up the stuff you want to keep!

step 1
boot the ubuntu live cd and choose try ubuntu without installing

step 2 
when the desktop comes up, plug in your usb drive.  an icon for the drive will appear on the desktop.  IT IS VERY IMPORTANT to right click the drive icon and select UNMOUNT

step 3
double click on the install icon on the desktop.  set it up however you want until you get to the install step 4

step 4
on the prepare disk space screen, select manual.  
[IMG]http://farm4.static.flickr.com/3240/3126122859_4ca0da5957_o.png[/IMG]

step 5
this next part is very important.  your disk layout will be different than mine so be careful.  you want to select your external hard drive.  in this picture my computers hard drive is labeled /dev/sda and you can see the different partitions it is split up into ie /dev/sda1.  below all of that you can see /dev/sdb.  that is my external hard drive and where we want to install ubuntu.  double click the first partition, in my case it is /dev/sdb1 and see the next step below.
[IMG]http://farm4.static.flickr.com/3256/3126931894_bbc0fdbab5_o.png[/IMG]

step 6
a new dialog box will pop up.  select a ext3 as a filesystem (you can choose a different one if you want but in most cases ext3 is the best bet.
now for the mount point put in /   then click ok and click next on the screen that pops up
[IMG]http://farm4.static.flickr.com/3078/3126101691_7755d0e918_o.png[/IMG]

step 7
this step is important as well as it installs grub onto your external drive and not your hard drive.  click on the advanced button that you can see in the picture
[IMG]http://farm4.static.flickr.com/3088/3126983758_d75253cc74_b.jpg[/IMG]

step 8
this is where you choose to install grub to the external drive.  you want to select your external drive.  earlier when you chose where to install ubuntu to you installed it to the first partition of the drive which in my case was /dev/sdb1.  now when we install grub we want to choose the drive itself not a partition.  make sure that the install bootloader box is checked and on the dropdown menu choose the drive itself, in my case this will be /dev/sdb.  
[IMG]http://farm4.static.flickr.com/3201/3126101607_80d46b99b1_b.jpg[/IMG]

now click on ok and then install.  ubuntu will install to the external drive.  once this is done, to launch ubuntu off of the drive you will need to reboot the computer.  whenever the bios is coming up there will be a key you have to hit (its different on different computers) in order to change the boot order.  hit the key and then select to boot from usb.  make sure that your external drive is plugged in and boot it.  you should now be able to launch ubuntu.

---

### Post by SportsGuy2 on 2008-12-21
Thank you so much I am going to try this asap! :D

---

### Post by wpshooter on 2008-12-21
Thank you **Adult Swim** for the nice tutorial **BUT** this still does not answer my primary question as to whether the USB thumb/key/pen drive thus having Ubuntu installed in this manner can then be used to run Ubuntu on/from any computer that I might choose to (assuming that it can boot from a USB device) that has a completely different hardware configuration/setup from the computer that was used when installing the O/S to the USB drive/device.

I have found no one here that seems to want to directly answer this particular question.

My thought is what good is it going to do me to install Ubuntu (or any other version of Linux) on a portable USB device if I can not then be able to use it on a computer other than the one that was used to install the O/S to the USB device ?  This would seem to me to be just an exercise in futility or something done just to see if it would work on/from a USB device !!!

Thanks.

---

### Post by thomas228 on 2008-12-21
> **wpshooter said:**
> Thank you **Adult Swim** for the nice tutorial **BUT** this still does not answer my primary question as to whether the USB thumb/key/pen drive thus having Ubuntu installed in this manner can then be used to run Ubuntu on/from any computer that I might choose to (assuming that it can boot from a USB device) that has a completely different hardware configuration/setup from the computer that was used when installing the O/S to the USB drive/device.

I have found no one here that seems to want to directly answer this particular question.

My thought is what good is it going to do me to install Ubuntu (or any other version of Linux) on a portable USB device if I can not then be able to use it on a computer other than the one that was used to install the O/S to the USB device ?  This would seem to me to be just an exercise in futility or something done just to see if it would work on/from a USB device !!!

Thanks.

Hi wpshooter

I think you are more aware of how ubuntu works than you let on.

It should be obvious to even a newbie like me that if you install a system on to a thumb the best you could hope for is a very generic version.  A video card or wifi set of compiled drivers would be limited to computers that had that special hardware.

I have two laptops and 5 or 6 various desktops and  will be using a 16GB thumb with 8.04 installed on it.  I expect that as long as I use a  generic video and don't  mind that my wifi drivers will only work on the laptops I should have a operational OS.  I will be  able to install and update programs such as various utilities and for example Openoffice ver 3.

So in answer to your question concerning a thumb installation I would say both yes and no depending on what you want your system to do.

Just a few thoughts from an old retired EE

Tom

---

### Post by SportsGuy2 on 2008-12-21
> **wpshooter said:**
> Thank you **Adult Swim** for the nice tutorial **BUT** this still does not answer my primary question as to whether the USB thumb/key/pen drive thus having Ubuntu installed in this manner can then be used to run Ubuntu on/from any computer that I might choose to (assuming that it can boot from a USB device) that has a completely different hardware configuration/setup from the computer that was used when installing the O/S to the USB drive/device.

I have found no one here that seems to want to directly answer this particular question.

My thought is what good is it going to do me to install Ubuntu (or any other version of Linux) on a portable USB device if I can not then be able to use it on a computer other than the one that was used to install the O/S to the USB device ?  This would seem to me to be just an exercise in futility or something done just to see if it would work on/from a USB device !!!

Thanks.

This is EXACTLY what you want. It works perfectly. Believe me, it does work, the boot loader only comes on when you have the flash drive plugged in. It works like a charm :)

---

### Post by adult swim on 2008-12-22
> **wpshooter said:**
> Thank you **Adult Swim** for the nice tutorial **BUT** this still does not answer my primary question as to whether the USB thumb/key/pen drive thus having Ubuntu installed in this manner can then be used to run Ubuntu on/from any computer that I might choose to (assuming that it can boot from a USB device) that has a completely different hardware configuration/setup from the computer that was used when installing the O/S to the USB drive/device.

I have found no one here that seems to want to directly answer this particular question.

My thought is what good is it going to do me to install Ubuntu (or any other version of Linux) on a portable USB device if I can not then be able to use it on a computer other than the one that was used to install the O/S to the USB device ?  This would seem to me to be just an exercise in futility or something done just to see if it would work on/from a USB device !!!

Thanks.

ive got an install of 8.10 on an external drive and ive loaded it onto 3 different computers than the one i installed it on.  the computer that was used to install had intel 945gm.  ive used it on an ati radeon and an intel x3100 and they were both detected at startup.  i think since the new Xorg setup, things are hotplugged and not necessarily managed by a strict structure such as xorg.conf.  even if the hardware wasnt immediatley available, it wouldnt be a big deal to get it working.  the external drive would still boot and you could troubleshoot from there.

---

### Post by wpshooter on 2008-12-22
> **adult swim said:**
> ive got an install of 8.10 on an external drive and ive loaded it onto 3 different computers than the one i installed it on.  the computer that was used to install had intel 945gm.  ive used it on an ati radeon and an intel x3100 and they were both detected at startup.  i think since the new Xorg setup, things are hotplugged and not necessarily managed by a strict structure such as xorg.conf.  even if the hardware wasnt immediatley available, it wouldnt be a big deal to get it working.  the external drive would still boot and you could troubleshoot from there.

Thanks for the info.

I will give it a try as soon as I find me an 8gb thumb drive.

---

### Post by thomas228 on 2008-12-22
> **wpshooter said:**
> Thanks for the info.

I will give it a try as soon as I find me an 8gb thumb drive.

Hi again

Try ebay (search like 8gb flash or 16gb flash or 32gb flash)

I got 3- 16gb thumbs for between $12.51 and $18.00 with free shipping.

It can take a few weeks to receive them but at those prices I thought I could wait.

Hope that helps some

Tom

---

### Post by wpshooter on 2008-12-24
> **thomas228 said:**
> Hi again

Try ebay (search like 8gb flash or 16gb flash or 32gb flash)

I got 3- 16gb thumbs for between $12.51 and $18.00 with free shipping.

It can take a few weeks to receive them but at those prices I thought I could wait.

Hope that helps some

Tom

In doing some research on this I am finding references to certain drives being "**U3**" capable ?

Does a USB pen/thumb drive **_HAVE TO BE_** U3 capable in order to have a Ubuntu O/S installed and ran from it ?

Thanks.

---

### Post by wpshooter on 2008-12-24
> **wpshooter said:**
> In doing some research on this I am finding references to certain drives being "**U3**" capable ?

Does a USB pen/thumb drive **_HAVE TO BE_** U3 capable in order to have a Ubuntu O/S installed and ran from it ?

Thanks.

Hmmmmmmmmmmm, in doing a little further research on this, my "guess" is that one might NOT want the drive to be U3 capable, if you wanted to install & run Ubuntu from it.  Am I correct about this ?

Thanks.

---

### Post by SportsGuy2 on 2008-12-24
> **wpshooter said:**
> Hmmmmmmmmmmm, in doing a little further research on this, my "guess" is that one might NOT want the drive to be U3 capable, if you wanted to install & run Ubuntu from it.  Am I correct about this ?

Thanks.

lmao yes, u3 has nothing to do with this

and jw, not to be rude or anything at all, but how do you have so many posts and not be as knowledgeable? jw, please don't take offence

---

### Post by wpshooter on 2008-12-24
> **SportsGuy2 said:**
> lmao yes, u3 has nothing to do with this

and jw, not to be rude or anything at all, but how do you have so many posts and not be as knowledgeable? jw, please don't take offence

Thanks.

Number of posts just indicates that I know a lot of things but not everything.  No one can have knowledge in an area that they have never dealt with before.  One is never going to learn anything if they don't ask !!!

Thanks.

---

### Post by EowynCarter on 2008-12-25
I had that one right ;)

I'm worried about the 
"the following partitions tables will be changed"
sda
sdb

Even i after i told grub to install on the flash disk, so sda shoudn't be touched.
And an other trouble : the flash disk is sdb on my laptop, but on my desktop, more likley to be sdc, and grub will mess up right ? Any idea there ?

---

### Post by Pumalite on 2008-12-25
If you install Grub in your Flash you will have no problems.

---

### Post by EowynCarter on 2008-12-26
ok, an other problem.
Using the live cd, My hard drives don't show at all in xfce.
In ubuntu, they are monted as root, works fine with my windows hardrive, but total failure with the linux one, as i need write acces.
Security is nice, but it's annoying to be looked off your own stuff.

I don't feel like using command line everytime i want to acces my data.. I can't configure fstab either, as the point of installing on a usb thingy is to be able to switch from laptop to desktop.. 
Why no "mount as myself" option ?

---

### Post by thomas228 on 2008-12-26
> **EowynCarter said:**
> ok, an other problem.
Using the live cd, My hard drives don't show at all in xfce.
In ubuntu, they are monted as root, works fine with my windows hardrive, but total failure with the linux one, as i need write acces.
Security is nice, but it's annoying to be looked off your own stuff.

I don't feel like using command line everytime i want to acces my data.. I can't configure fstab either, as the point of installing on a usb thingy is to be able to switch from laptop to desktop.. 
Why no "mount as myself" option ?

Hi

My thumb works very nicely as an independent OS on computers that have the bios option for booting. ie it "mounts itself"

On my older systems (4 desktops) I am setting them up as windows/ubuntu dual boot.

This gives me a grub menu that I can change (add to) to cover my thumb for boot up.

Ubuntu is great and the thumb installation allows me to get around a lot of upgrade problems No hi-speed internet other than wifi at my local Hardy's which is 28 miles round trip from home.

I've ordered some 16GB thumbs with a higher rw speed and will be able to better maintain my various desktop Ubuntu OS's

I'm sure there are resolution to your "security terminal command" problems as well.

Good Ubuntu'ing  :popcorn:

Tom

---

### Post by thomas228 on 2008-12-26
> **EowynCarter said:**
> I had that one right ;)

I'm worried about the 
"the following partitions tables will be changed"
sda
sdb

Even i after i told grub to install on the flash disk, so sda shoudn't be touched.
And an other trouble : the flash disk is sdb on my laptop, but on my desktop, more likley to be sdc, and grub will mess up right ? Any idea there ?

Hi again

Read [http://ubuntuforums.org/showthread.php?t=1021772]("http://ubuntuforums.org/showthread.php?t=1021772") for hints on how to solve those problems.

Remember that the bios usb thumb boot will make it "hd0,X" ie the first disk. Once I got the hang of it thanks to the help of caljohnsmith and others.

Worked great for me

Good Ubuntu'ing  :popcorn:

Tom

---

