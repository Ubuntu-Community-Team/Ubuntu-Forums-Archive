---
title: "Need help!!!"
date: 2008-10-22
forum: General Help
---

### Post by LidanJericho on 2008-10-22
When i start up the computer it's automatic goes to ubuntu....

but i want to go to windows xp....
so im afraid that ubuntu deleted xp...
what i need to do?

---

### Post by Elfy on 2008-10-22
We can check - in ubuntu open a terminal from the accessories menu, paste this command

```
sudo fdisk -l
```

it will ask for password, use yours - it will not show but it is there.

Paste the output back here and we can check - assusming that it's there and you haven't deleted it then we can make win the default.


Please do not use titles like that - this is a support forum and eveyone is needing help ;)

---

### Post by Circus-Killer on 2008-10-22
firstly, when starting a new thread, you should make the title of the thread a bit more descriptive than "Need help!!!". perhaps something like "problem with dual boot" or "cannot start windows xp", etc.

now onto the problem. well, when you go through the ubuntu install, it gives the option to create a dual boot setup or to just remove windows completely. if you had selected dual boot, it should have automatically setup the boot loader (grub) to give you an option of which os you wish to start.

so, by my guess, it can be possible that you did completely wipe out XP, but i'm not too sure. i would wait for more responses that should be able to give you directions on how to find out whether or not xp has been whiped.

---

### Post by LidanJericho on 2008-10-22
> **forestpixie said:**
> We can check - in ubuntu open a terminal from the accessories menu, paste this command

```
sudo fdisk -l
```

it will ask for password, use yours - it will not show but it is there.

Paste the output back here and we can check - assusming that it's there and you haven't deleted it then we can make win the default.


Please do not use titles like that - this is a support forum and eveyone is needing help ;)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb98b805

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

this what it's typing...
i think it's just deleted the windows xplike circus-killer said...
so my other question is how i install windows xp?

---

### Post by Flyingjester on 2008-10-22
yup, it's gone, do you have the disk?

---

### Post by LidanJericho on 2008-10-22
> **Flyingjester said:**
> yup, it's gone, do you have the disk?

of course... 
im doing the trick with the F11 and install right from the disk but it's still going to ubuntu ;\

---

### Post by Flyingjester on 2008-10-22
i'm confused, do you have the windows disk in the tray?

---

### Post by LidanJericho on 2008-10-22
yup..

---

### Post by Flyingjester on 2008-10-22
and it's still booting right into ubuntu? are you sure you have the boot order correct in bios, and have a bootable windows copy? (I am assuming you haven't reinstalled windows already)

---

### Post by No-Neck on 2008-10-22
What trick with F11?

If your computer is not booting the Windows installation when you have the CD-ROM in your drive, you will need to enter the BIOS when your PC first switches on, probably by pressing Delete.

Be careful what you do here, you'll need to find Boot Order, or Boot Priority and change it to boot from CD/DVD first.

---

### Post by LidanJericho on 2008-10-22
> **No-Neck said:**
> What trick with F11?

If your computer is not booting the Windows installation when you have the CD-ROM in your drive, you will need to enter the BIOS when your PC first switches on, probably by pressing Delete.

Be careful what you do here, you'll need to find Boot Order, or Boot Priority and change it to boot from CD/DVD first.

That's what i did... and still it's going to ubuntu!O_o

---

### Post by No-Neck on 2008-10-22
If the BIOS is correctly set up then there are only 2 possibilities:

1) CD drive is faulty, improperly configured or improperly connected

2) CD-Rom is not bootable.

So, if you're sure your CD drive is working correctly and you set the boot order up (does it hang before it boots Ubuntu and/or mention boot from CD/DVD?) then check your Windows CD.

---

### Post by LidanJericho on 2008-10-22
The CD is ok... i installed from it the windows befor a month or something... 
but now it's types something with Media Boot/ Choose media boot ...

---

### Post by No-Neck on 2008-10-22
Nothing in terms of booting from different devices will have changed since you installed Ubuntu, it is impossible. At that point your computer doesn't even know Ubuntu exists, for all it knows your hard drive may contain no OS at all. 

Perhaps it is possible your motherboard requires you to press a button during boot to choose different boot media, but if you've set up your BIOS to boot from CD first it should do that automatically.

You'll have to remember exactly how you managed to install Windows a month ago.

---

### Post by TyTiger on 2008-10-22
As not all computers start up the same, the most common BIOS options ive come across in my experence are:
ESC, F1, F2, F10 F12, Delete and Del(num pad)

these can also be the option to boot from an alternative medium, depending on the computer. Try some of them out.

Oh also note, a handy trick is to press them repeatedly untill you get somwhere, its not allways easy to press it in the small time gap the computer wants it to be pressed so this sometiems helps.

---

### Post by Elfy on 2008-10-22
> but now it's types something with Media Boot/ Choose media boot ...that would be it then I suspect - choose cdrom

---

