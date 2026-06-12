---
title: "After restore, system won't boot or recognize boot devices"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by mjstelly on 2009-08-01
I followed the directions to [backup a system]("http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup+restore") then restore it to another system. Well, I backed up just fine. I restored the file and totally hosed the target system. I followed instructions on [how to reset GRUB]("http://ubuntuforums.org/showthread.php?p=117829#poststop") in case I screwed things up. I now get: 

[B]Error 15: File not found.
Press any key to continue...
[/B]
To make matters worse, even though the BIOS settings has the cd drive set to position 1 in the boot priority, it won't boot from the cd. So, I can't even get to the desktop.

When I press a key, a list of boot kernels is displayed. I try to boot from any of them. It just returns me back to the previous screen.

I selected C for command-line, typed 
**grub> find /boot/grub/stage1**, 
I get 
**grub> root (hd0,0)**.

I type 
**grub> setup (hd0,0)**

Geeky goop prints to the screen, but finally says "install grub succeeds". Try typing **quit** but that does nothing. So I reboot, and nothing has changed. ](*,)

 I'm stumped on this one. All other directions I find assume that I can boot from the live cd, which I can't. Did I totally screw the pooch on this one? 

Learned bios supports usb boot device. I enabled it, saved and continued with Jaunty on a usbstick that I successfully tested on this machine first (acer laptop). Experienced same behavior as above although system noted usb device detected and loaded. 

So now the boot priority is 1) usb boot, 2) dvd drive, 3) hd0. I wondered if the system even attempted to boot from anything other than hd0. I removed hd0 from the boot priority list, rebooted, and received  the following message:

[B]Reboot and Select proper Boot Device
or Insert Boot Media in Selected Boot Device[/B]

Just as I suspected. Although the system knows about the dvd and usb drives, and the bios instructs it to boot from those devices first, it refuses to boot from anything but hd0. wtf?

I've hit the limit on my knowledge. I place the fate of this install in your capable hands.

---

### Post by wojox on 2009-08-01
Try C for command-line, type:

```
linux acpi=off
```

Press Enter.

---

### Post by mjstelly on 2009-08-01
> **wojox said:**
> Try C for command-line, type:

```
linux acpi=off
```Press Enter.

At the "grub>" prompt, I typed this command. It returned 

**Error 27: Unrecognized command**

:(

---

### Post by merlinus on 2009-08-01
> I selected C for command-line, typed 
**grub> find /boot/grub/stage1**, 
I get 
**grub> root (hd0,0)**.

I type 
**grub> setup (hd0,0)**Did you type

```
root (hd0,0)
```before typing

```
setup (hd0)
```

---

### Post by mjstelly on 2009-08-01
> **merlinus said:**
> Did you type

```
root (hd0,0)
```before typing

```
setup (hd0)
```

OK, what am I missing? :confused:
I typed the above commands from the grub prompt, then

**linux acpi=off** (still unrecognized command)
**reboot**. 

Got the same result: **Error 15: File not found.**

---

### Post by merlinus on 2009-08-01
Can you boot from the live cd? Restore option should get you to a command line (not >grub).

If so, post results of

```
sudo fdisk -l
```

---

### Post by mjstelly on 2009-08-01
> **merlinus said:**
> Can you boot from the live cd? Restore option should get you to a command line (not >grub).

If so, post results of

```
sudo fdisk -l
```

Well, no. I can't. I mentioned that in the original post. The system won't let me boot from either a cd or a flash drive.

---

### Post by presence1960 on 2009-08-01
using that command line prompt run the command ```
sudo fdisk -l
```
you won't be able to copy the info but write it down and then post it back here. You are getting error 15 because you probably installed GRUB to the wrong place. I know setup(hd0,0) is incorrect because that installed GRUB to a partition not the MBR.

That should work from the command prompt. I just rebooted my machine and went into recovery mode and dropped to a command-line shell. I ran sudo fdisk -l and it worked for me. Post back the output you receive from that command and we can tell you the proper commands to run to install GRUB.

---

### Post by presence1960 on 2009-08-01
> **mjstelly said:**
> At the "grub>" prompt, I typed this command. It returned 

**Error 27: Unrecognized command**

:(

That's because that command can't be run from grub> you need to exit grub> to run that command

---

### Post by presence1960 on 2009-08-01
I remember very early in my Ubuntu days I tried this and it jacked my system up too. Of course I knew less about Ubuntu then than I do now. I had to take my hard disk out of my machine and put it in my daughter's rig. I then used dban to clear the hard disk. Put it back in my machine and reinstalled ubuntu. I have not used that method to back up/restore since then. There are other options to create an image that can be used to restore, such as clonezilla, partimage or [ping]("http://ping.windowsdream.com/") (partimage is not ghost).

---

### Post by mjstelly on 2009-08-01
[IMG]http://picasaweb.google.com/lh/photo/_Pfjgiroyx4F9fpfOOZLSw?authkey=Gv1sRgCLfKvu3v_e3vFA&feat=directlink[/IMG]
Here's a pic of my monitor. command doesn't work in the way you directed.

Guess the pic didn't load. figures. At any rate, none of the commands i've tried from GRUB work, and I can't load linux from the usb or cdrom.

---

### Post by presence1960 on 2009-08-01
> **mjstelly said:**
> [IMG]http://picasaweb.google.com/lh/photo/_Pfjgiroyx4F9fpfOOZLSw?authkey=Gv1sRgCLfKvu3v_e3vFA&feat=directlink[/IMG]
Here's a pic of my monitor. command doesn't work in the way you directed.

Guess the pic didn't load. figures. At any rate, none of the commands i've tried from GRUB work, and I can't load linux from the usb or cdrom.

don't run sudo fdisk -l from GRUB, select C, as soon as the command prompt appears run ```
sudo fdisk -l 
``` No more no less. forget grub momentarily.

---

### Post by mjstelly on 2009-08-01
> **presence1960 said:**
> don't run sudo fdisk -l from GRUB, select C, as soon as the command prompt appears run ```
sudo fdisk -l 
``` No more no less. forget grub momentarily.

I'm going to try a different approach. I attached the drive as a secondary on my functioning system. I want to format it, then clone the working drive image to it. 

How do I do that?

Thanks for your patience and for helping me to clean up my mess. :oops:

---

### Post by presence1960 on 2009-08-01
> **mjstelly said:**
> I'm going to try a different approach. I attached the drive as a secondary on my functioning system. I want to format it, then clone the working drive image to it. 

How do I do that?

Thanks for your patience and for helping me to clean up my mess. :oops:

I would not use that same method. I would use partimage, clonezilla or ping. Don't play with fire and get burned twice.

---

### Post by mjstelly on 2009-08-01
> **presence1960 said:**
> I would not use that same method. I would use partimage, clonezilla or ping. Don't play with fire and get burned twice.

No, I learn pretty quick. Just gonna read up on the those apps you mentioned.

Thanks again.

---

### Post by mjstelly on 2009-08-02
I have to say, you folks are pretty awesome! You stuck around until I worked through to a solution. Qualities like that are all too rare these days! That's what makes this community rawk! 

The solution that worked for me? [Clonezilla]("http://www.clonezilla.org/"). 

Here are the steps I took in case someone else finds themselves in the same unfortunate and frustrating circumstances. 

Requirements: Another functioning hard drive or use a second working computer.
1a) Add a bootable hard drive as the master or
1b) Place offending drive in a second system as a slave. Note: I have the hard drive jumpers set to Cable Select, then configured the master/slave settings in the bios.
2) Boot the system.
3) Download Clonezilla.
4) Follow directions on the site for installing it to a bootable source - cd, flashdrive, or harddrive.
5) Clone the functioning drive.

That's it! I now have two identical, ***functioning ***drives. In fact, I'm adding this comment from the once-broken drive. Hooray for Ubuntu!

---

### Post by presence1960 on 2009-08-02
Glad you got it working! Enjoy Ubuntu.

---

