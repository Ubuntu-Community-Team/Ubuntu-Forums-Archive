---
title: "MBR messed up"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by dummyhead3 on 2009-10-05
Hey, I want to reinstall ubuntu on my laptop which dual boots a messed-up ubuntu and Windows. 
I was going to install ubuntu when some error messages started popping up. So, I decided to delete my old, disfunctional ubuntu partiton and create a new ext3 one.
Unfourtunatley, the installer kept bugging. I believe this is because instead of shutting down Windows, I put it into hibernation mode.  
Now, I can't boot into Windows because I deleted the old linux partition on witch grub was installed, therefor grub gives me error 15. How can I remove grub, or reinstall linux?

Also i tried to perform fdisk with a FreeDOS liveCD, but it says that fdisk doesn't exist.

THUG LYFE! :guitar:

---

### Post by doomsword2001 on 2009-10-05
i had this prob 1 year ago too.
i think that if u enter the installation disk, you won't get erro15, because cd will boot first, then install ubuntu and grub will be installed as well.
if u enter cd and get error15 i think that means first boot device is the hard disk and u have to make 1st the cd rom.

---

### Post by dummyhead3 on 2009-10-05
> i think that if u enter the installation disk, you won't get erro15, because cd will boot first, then install ubuntu and grub will be installed as well.

Yes, but the problem is, ubuntu (8.04) won't install! The install hangs on 3rd step.

---

### Post by doomsword2001 on 2009-10-06
if i am right grub deletes windows MBR but u can restore it with windows cd or [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828). i think you are able to install grub with a live cd on the windows partition aswell.

---

### Post by presence1960 on 2009-10-06
you can restore windows to MBR by following the instructions for your windows version [here]("http://ubuntuforums.org/showthread.php?t=1014708"). You should then be able to boot right into windows. Get windows squared away then reinstall Ubuntu. GRUB will overwrite windows on MBR during the Ubuntu install and you will be good to go.

---

