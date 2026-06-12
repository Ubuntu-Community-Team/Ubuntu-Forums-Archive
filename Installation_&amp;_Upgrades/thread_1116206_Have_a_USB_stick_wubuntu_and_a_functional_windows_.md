---
title: "Have a USB stick w/ubuntu and a functional windows partition"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by tamas305 on 2009-04-04
I was planning to put both ubuntu and a functional windows partition on one 8gb USB stick. Using gParted I made a 2gb fat32 portion as the first partition (I've heard that windows only recognizes the first one) and a 5gb ext3 section for ubuntu. The rest being swap. This may seem like a stupid question but I'm kind of confused how to correctly use the manual install of ubuntu to install it into the ext3 section, when I do it I get an error message. =( please help

---

### Post by tamas305 on 2009-04-04
In case anyone cares I figured out how to do this =) 

its too lengthy to type here so e-mail me for it at [email]tamas305@gmail.com[/email] if you want to know

---

### Post by tamas305 on 2009-04-15
I decided I did not want people spamming me so here is how I did it. 

Note: I highly recommend you back up your data before you begin this tutorial because anything could happen. This is collage of what I put together from various other forums and it worked for me. I also advise (if possible) for you to unplug any hard drives attached to the system as a safety precaution. For this tutorial you will need:

  - Ubuntu Live CD
  - gParted Live CD
  - SuperGrub CD (download it but you may not need it)

*websites are constantly updating so any link I post now may be outdated in a week so just google them if you cannot find them. Now lets get our hands dirty...

***_Installation_***

Once you have used gParted to make all of the partitions that you needed. All you need is ext3 for Ubuntu and a fat32 for windows. 

Note: windows only recognises the first partition of a USB drive, make sure the fat32 is first. (When I say first I mean name wise not by how the gParted GUI displays it. i.e. /dev/sdb1). Remember to write down somewhere the partition number of the ext3 partition, this will become mighty useful later.

Insert the Live CD and click on full install. Go though all the menus until you get to the partitioner. Now here is the tricky part. Select manual install (guided overwrites all of your partitions including the fat32). Then from the next page select the partition from your USB drive you want to install Ubuntu to. (it will be an ext3 partition)

Note: make sure that install to correct directory or Ubuntu might overwrite something important. So, if possible, unplug your internal hard drive just in case.

Now set that ext3 partition as the "/" drive. (Ubuntu will install all of its files here, the "root"). Continue through the installer and install Ubuntu. Once done you will have correct the GRUB problem. 
[B][I][U]
GRUB problems: Error 22 especially.[/U][/I][/B]

Try to run your computer without the USB drive that has Ubuntu on it plugged in, what happens? Most likely you got an error.

The problem is that you installed GRUB's files onto the USB drives while you installed it into the Master Boot Record (MBR). So what happening is that GRUB tries to run and it cannot find its files because they are on your USB drive which is not plugged in.

Boot up the live CD and go into the demo mode. Open up a terminal (Applications --> Accessories --> Terminal). 

This is going to involve some MS-DOS like features, so pull your pants up and lets get going.

Into the terminal type:
```

sudo grub
```

This gets you the GRUB shell

```
find /boot/grub/stage1
```

This returns the location of GRUB's files. Note: whatever was returned for the find command you have to use it in the next line, you should still be in the grub>. 
```

root (hd?,?)
```

Use whatever find returned again, for example if find returned (hd0,1) then root (hd0,1) would be what you enter.

Now you have to make sure that GRUB is on the USB drive not on the MBR.

```
setup (hd?)
```

Replace ? with whatever drive you want to install GRUB on. Most likely your USB drive so use whatever number that find returned, for example if it returned (hd3, 15) then you would type setup (hd3).

To exit the GRUB shell type

```
quit
```

If it still does not work than I suggest using SuperGrub Live to delete GRUB completely from everything and then redo this entire tutorial. Cross your fingers that does not happen. Hopefully if everything works out correctly than you should be able to boot successful to Ubuntu when the USB is plugged in and to whatever OS you normally use.

Good luck,

-tamas

---

### Post by azzline on 2009-04-17
Hi! I was interested in installing Ubuntu into my 16gb USB and actually using the full space. However,  using the tool given by 8.10 to make live usb does not allows me to do so, it says everything is ready however the USB will not boot. I was able to install in a 8gb but I need more space because I need to virtualize xp inside ubuntu and install Visual Studio. This is because my laptop died and I need to use the desktop pcs they have at school, but do not want to be recompiling and moving folders. I know it sounds kind of stupid to do all of this but I really need VS. Wondering if you could give me some advise in how to, if you may please.

Beforehand, thank you for reading this anyone.

---

### Post by tamas305 on 2009-04-17
The live usb tool inside Ubuntu is not a full install. It only makes a live USB, which is basically exactly like the CD except on a USB drive. To get persistent memory (saving files on the USB) you need a full install like in the posts above

-tamas

---

### Post by kdroxx on 2009-04-25
What if I want to install ONLY Ubuntu ??
Just format the drive as ext3 and follow guided installation, right ??

---

### Post by DavidFourer on 2009-04-26
I want to make a full-install on a USB stick, no Windows or anything fancy though.  Just a usable portable drive that I can tweek and save permanent files.  I run Ubuntu on a notebook and unplugging the hard drive is not practical.  I'm not a hi-tech user here.  Can this be done safely?  I understood everything up to here:
> The problem is that you installed GRUB's files onto the USB drives while you installed it into the Master Boot Record (MBR).
Perhaps I should wait for someone to make these and sell them, Or try to get someone at the local LUG to make one for me.

Two reasons for doing this.
The obvious--to take my ubuntu on the road, with bookmarks and email and such.
Also, I tried the Jaunty live CD and had problems, so I'm holding off on upgrading my regular computer.  Maybe problem with Intel integrated graphics--http://ubuntuforums.org/showthread.php?p=7104256#poststop (Dell Inspiron 6000).  So I thought I would try to get Jaunty working on the USB, if that makes sense.

---

