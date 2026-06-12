---
title: "Dual Booting Ubuntu 9.04 with Ubuntu 8.04.x"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by EmyrB on 2009-05-14
Hi All,

To cut a long story short (and prevent me from ranting) I need to be able to have 2 versions of Ubuntu on 1 PC. Why? Well My Sony Ericsson W800i is no longer recognised by Ubuntu (8.10 at least saw it as a 3G mobile device, 9.04 just doesn't do anything) and the last version of Ubuntu that worked flawlessly with the phone was 8.04. I have a post in the forums as to how to get Ubuntu to recognise the phone, but alas no one has so far been able to help.

Anyway, to get round the problem (8.10) I installed Windows XP so I could get at my photo's and transfer music. I then hit upon the idea of a virtual machine, so with 8.10 I installed VirtualBox and installed 8.04. This worked until I upgraded to 9.04. I don't rteally want to boot into Windows all the time, so I came up with the bright idea of tripple booting with Windows XP, Ubuntu 9.04 and Ubuntu 8.04.x.

I kinda know how it works, I won't need to create a swap as I have the one created with 9.04. Not too worried about having my /home mounted (on a separate partition) as long as I can mount my photo's drive (currently on ext4, so will have to reformat to ext3 and alter fstab on 9.04 to expect ext3). I just don't know how grub will behave. I take it that grub on 9.04 is newer than 8.04.x and if so, will this cause an issue with the installer for 8.04.x when it comes to installing the bootloader to sda?

Any help with either dual booting Ubuntu with Ubuntu or how to get 9.04 to recognise my W800i will greatfully be recieved.

Cheers

EmyrB

---

### Post by TyTiger on 2009-05-14
Ive often considered this myself, i currently run only 8.04.2 on my desktop because the newer version didn't quite work right, either the sound was buggy or the graphics was very slow.
the grub version shouldn't be an issue, yes it may update your grub but it will (should) keep your currently installed OS's and their respective Grub listings in tact and just put the 9.04 at the top of the list. 

As for the Ext4, I believe that it comes with th newer versions of Ubuntu and may or may not be readable by the earlier versions, (i could be wrong I've not tried it) so leave it as ext4 first to see what happens. 

9.04 might need its own root partition but you can indeed set your 8.04.x partition to be mounted under your /home directory of 9.04 though I'm not 100% sure how you would have it mount the /home/name from he 9.04 as the home/name on the 8.04.x
just that you can mount the entire partition as your home directory. (or whatever you choose)

Hope that helps some.

---

### Post by EmyrB on 2009-05-14
Thanks for the reply TyTiger. My 9.04 install has its own root partition and I will set 8.04.x to have its own root partition as well, its just grub that I feel is a stumbling block.

Cheers

EmyrB

---

### Post by EmyrB on 2009-05-15
I have one more question regarding formatting an existing ext4 drive back to ext3. If i do this, will it change the drive's UUID for 9.04? Also, will the drive have the same UUID for 8.04.x as 9.04?

Cheers

EmyrB

---

