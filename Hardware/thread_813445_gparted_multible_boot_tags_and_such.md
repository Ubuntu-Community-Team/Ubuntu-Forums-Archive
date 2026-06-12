---
title: "gparted multible boot tags and such"
date: 2008-05-30
forum: Hardware
---

### Post by templa edhel on 2008-05-30
so i have 2 hard drives, a 60gig and a 20gig (roughly).when i installed i had windows and ubuntu on the 60 gig and the 20 gig ext2. now i would like to move the windows partition to the 20 gig and have the 60gig all for ubuntu. I deleted the 20gig then copyed the windows partition to it using gparted. but now im at the point where i need to add boot flags and gparted appers only to allow one. also i heard that if i have 2 windows systems(i dont want to delete the other one yet) then it will crash when i boot one. what do i do now?:confused:

---

### Post by abhiroopb on 2008-05-30
Ah I'm really confused! Could you take a screenshot of gparted and point out what exactly you want to do (diagrams are always helpful!)

---

### Post by templa edhel on 2008-05-31
[IMG]http://i269.photobucket.com/albums/jj54/templaedhel/Screenshot.png[/IMG]
i need to add another boot tag but it wont let me. once i do that and can successfully boot the copyed partiton of windows i can delete the old one and inlarge my ubuntu partiton

---

### Post by abhiroopb on 2008-05-31
SO let me clarify, you have an ubuntu partition (ext2) of 45gb, you have to copies of Windows. I'm not 100% sure but I believe that inherently you can have only ONE boot flag. What is it that you are exactly trying to do? If you want to boot into you're windows partition you can add it to the GRUB (grand unified boot laoder) so that when you start the computer you will be able to hit esc, get into grub and start windows. Is this what you are trying to do? If so do the following in a terminal:

```

sudo gedit /boot/grub/menu.lst

```

In gedit scroll to the bottom and something like the following should be there (if not read on and you can add it):

```

title   Windows 95/98/NT/2000
root   (hd0,0)
makeactive
chainloader   +1

```

Since you are trying to add the windows partition (/dev/sda3) to the boot loader you need to edit root (hd0,0). I assume that the windows is on the FIRST partition of the SECOND hard drive, so the root (hd0,0) will need to be root (hd1,0).

So at the end of the grub file you should add this:

```

title   Windows 95/98/NT/2000
root   (hd0,0)
makeactive
chainloader   +1

```

This suggestion is adding Windows to you're grub so you can start it. I don't see how you can have more than one boot flag. Not really sure about this, but look at it this way if you have more than one boot flag which one will it load when you boot?

NB: I'm still not totally sure what it is you are intending to do. Sorry I don't know if its you or me, either way hopefully someone else can take a quick scan of this thread as well.

---

### Post by templa edhel on 2008-05-31
it didn't work and i think i know why. If you look in the upper right corner dev/sda is 91.76gb(and its the only disk you can choose) which appears to mean its seen as one hd. before it appeared as 2 because it had been partitioned. so i have one extended partition with the old windows and ubuntu on it(and swap) then on the SAME disk i have to copy of windows and the windows restore tool(the 4 gig fat32 partition). so what do I add to menu.lst now? sorry im being so bothersome.

---

### Post by abhiroopb on 2008-05-31
I was quite sure it was one HD, as gparted shows each HD as a separate section (as in you can't view two HDs in one window like that).

change root hd(1,0) to root hd(0,2)

so it looks like this:
title   Windows 95/98/NT/2000
root   (hd0,2)
makeactive
chainloader   +1

I am assuming that because the windows partition is /dev/sda3 it is the THIRD partition

I'd advise you to restructure this if possible. You have basically the same setup as me (one ubuntu and one windows). there is no need to put the ubuntu in an extneded partition. And you can have upto four partitions before there is a need to have an extended partition.

---

