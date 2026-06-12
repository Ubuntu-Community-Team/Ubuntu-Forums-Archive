---
title: "Hard drive inaccessable - Previously a dual boot"
date: 2008-11-19
forum: Hardware
---

### Post by Clawz114 on 2008-11-19
Hi guys.

About a year and a half ago (i know ive left it a long time) My computer was running XP and Ubuntu at the same time on the same hard drive. It took me a little while to figure out what to do with the partitions or whatever but i did it in the end.

This was all working nicely until one day i decided to be a stupid $%£&.

I didn't use the Ubuntu side of things hardly ever so i decided i didn't want it anymore and i couldn't figure out how to uninstall just the Ubuntu part so... in a very very stupid move my me... i opened windows explorer and selected the Ubuntu files and pressed delete.

For some reason i thought this would just get rid of it, obviously it isn't that simple.

Ever since then, i cant get into the hard drive. It wont even load XP. It turns on and gives me an error message if that hard drive is plugged in. (to be honest i cant remember what error number it was as it was so long ago... and i don't have a PC right now so i cant check)

Ive tried plugging it in while a different hard drive is running XP. It spins up but XP cant detect it.
Ive tried it as a secondary hard drive with an XP hard drive as the master... still wont boot (different error message)
Ive tried putting it in an external hard drive enclosure and plugging it in via usb. When i do this, the drive spins up like it should but nothing happens on the computer and XP cant see it or has no knowledge of it even existing.

I don't care if the hard drive is unusable, i don't actually want it... what i do want, is the data which is still on there (Saved on the XP side)

Any suggestions?

Im a bit of a noob with hard drive partitions and ubuntu so, simple answers please :|

I have had a little bit of a try with the program "Spinrite" but i couldnt get that to work :confused:

Thanks in advance

---

### Post by caljohnsmith on 2008-11-19
So did you have Ubuntu installed inside of Windows (a Wubi install)? Or did Ubuntu have its own dedicated partition, and you used Grub on start up to boot either OS? Sounds like you had a Wubi install though. Do you have a Ubuntu Live CD? If not, that would help to troubleshoot your problems. Actually any Live CD will do. If you can download and boot a Live CD, how about opening a terminal (Applications > Accessories > Terminal if it is Ubuntu), and post the output of:
```
sudo fdisk -lu
```
While your HDD is connected. We can work from there if you want.

---

### Post by Clawz114 on 2008-11-19
Ubuntu was on its own partition.

> Grub on start up to boot

That reminds me a bit about the error.

The error was something along the lines of

Grub error (error number which i cant remember)

---

### Post by dwanders on 2008-11-19
It sounds like you need to restore your Windows Boot loader. You should be able to do this with the Windows XP Disk - if I can locate the steps I will post them. 

I am kind puzzled at how you deleted the Ubuntu from Windows, unless you were using the Disk Administrator and deleted the Ubuntu Partition?

---

### Post by Clawz114 on 2008-11-19
> It sounds like you need to restore your Windows Boot loader. You should be able to do this with the Windows XP Disk - if I can locate the steps I will post them.

I am kind puzzled at how you deleted the Ubuntu from Windows, unless you were using the Disk Administrator and deleted the Ubuntu Partition? 

Thankyou

Im remembering more and more about this now.

I was using a program or something that let me read and access the linux files from XP as i wanted to be able to get to stuff i had been using in ubuntu.

Cant remember what it was called.

---

### Post by dwanders on 2008-11-19
Step by step 

1. Put XP Disc in drive

2. Startup PC

3. Let the PC run into the CD

4. Choose the Recovery Console

5. Type your admin username

6. Type your admin password

7. Type Fixmbr

8. Type exit

9. Eject Disc

10. Load windows !

11. Enjoy !

---

### Post by dwanders on 2008-11-19
Of course the really amazing thing is that you are removing your Linux install rather than your Windows install? Thats just plain crazy :lolflag:

---

### Post by Clawz114 on 2008-11-19
...ok

Is it possible to do this through my laptop.

I can put the hard drive in a usb enclosure, and then change the boot order so the laptop drive isnt even on there, and put CD ahead of the external drive?

Will that have the same effect?

Its just i dont have a working computer atm as my motherboard has bent cpu socket pins (£200 down the drain :()

---

### Post by caljohnsmith on 2008-11-19
> **Clawz114 said:**
> ...ok

Is it possible to do this through my laptop.

I can put the hard drive in a usb enclosure, and then change the boot order so the laptop drive isnt even on there, and put CD ahead of the external drive?

Will that have the same effect?

Its just i dont have a working computer atm as my motherboard has bent cpu socket pins (£200 down the drain :()
Yes, the main thing is to boot the Live CD while also having your Win XP HDD hooked up. With the problems you are describing though, it may well be that Ubuntu won't be able to see your XP HDD, but hopefully that won't be the case. Give it a shot and let me know how it goes.

---

### Post by Clawz114 on 2008-11-19
> actually any live cd will do. If you can download and boot a live cd, how about opening a terminal (applications > accessories > terminal if it is ubuntu), and post the output of:
Code:

Sudo fdisk -lu

while your hdd is connected. We can work from there if you want. 

[size="5"]or[/size]

> 
1. Put xp disc in drive

2. Startup pc

3. Let the pc run into the cd

4. Choose the recovery console

5. Type your admin username

6. Type your admin password

7. Type fixmbr

8. Type exit

9. Eject disc

10. Load windows !

11. Enjoy ! 

---

### Post by Coder543 on 2008-11-19
If you want to get rid of ubuntu (a very strange idea...) then follow the second one, The other one is just asking for more details so that the issue can be further diagnosed. (Perhaps you need to ask some questions so that we can help you see why ubuntu is *so* much better than windows? Believe me, Ubuntu is on the level of Mac OS 10.5; It is that good! [plus it has wine so it can run windows apps really well])

---

### Post by Clawz114 on 2008-11-19
^^^ lol ^^^

Can i play games on ubuntu... such as Battlefield 2, Command and Conquer 3? Latest games coming out at present? Get software for my Sony High definition Camcorder?
Photoshop?
Ultramon? (does ubuntu have dual screen support?)
Kaspersky anti-virus?

If i can get all of them then i would most likely consider giving it another go.

-------------------------------------------------------------

Bit of a strange question but...

For the windows CD method.

Can i use a windows CD that is not the original disc that was used when i installed windows. For example, someone else's disc. I cant find my XP disc at present (typical)

I only wanna grab the files then nuke the entire hdd.

---

### Post by dwanders on 2008-11-19
I think you need the XP Disk (A Linux live CD will not be able to restore your Windows MBR with Fixmbr - you need a Windows OS CD to do that). 

And I too believe it should work if your Laptop boots off the CD, and the primary harddrive it sees is your broken disk - if you boot off the CD and it sees your laptop first instead, when you run fixmbr it will go right to the Laptop HDD. You need to have the broken disk show up as C: to Windows.  

you could run it like:

fixmbr \Device\Harddrive0 (or antoher dirve)
    if you know what the \Device\nameis

---

### Post by dwanders on 2008-11-19
Wont need Kaspersky, and many of those can be run through Wine or Crossover Office for $30. 

GIMP instead of Photoshop
I have heard it does Dual Monitor - but never had need to do so

Yes, you can use any disk, but you will still need to know the Administrator & Password of the original install. 

Ubuntu and Linux in general have many killer games also all free.

---

### Post by dwanders on 2008-11-19
I have taken the path of using Game Consoles for Games, and I leave my computer for computing and find that I really can do anything I need to in Linux. 

You do need to be careful when purchasing new gadgets - make sure they work with Linux prior to the purchase rather than after. Then again, for my kids they love the Linux Games, and ther are many of them for Ubuntu try out [http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by Clawz114 on 2008-11-19
This is gonna sound like i wasted your time.


But i just plugged in the hard drive in the external USB enclosure, and it worked :|

I tried just plugging it in over 10 times, taking it out, plugging it back in, removing the hard drive reinsterting it into the enclosure, didnt work... and now all of a sudden it works :S

Thanks for the help anyway guys. Much appreciated :KS

---

### Post by dwanders on 2008-11-19
Is it working you can boot off it? Or is it working you can read the data off it with your laptop?

If all you were trying to do was access the data - you could have gotten ) there much sooner =)! 

No problemo here though - Still think you should give Ubuntu another try and check out some of those open source games. Happy computing:-P

---

### Post by Clawz114 on 2008-11-19
Its working as in, working as an external mass storage device. Havnt tried booting off it, but i dont need to.

I did try just using it as a mass storage device but it didnt work the 10 + times i tried it over the past few months.

Thanks anyway!

---

