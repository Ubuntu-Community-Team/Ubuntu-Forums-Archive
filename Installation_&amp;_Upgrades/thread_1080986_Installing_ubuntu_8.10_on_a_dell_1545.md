---
title: "Installing ubuntu 8.10 on a dell 1545"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by annexwill on 2009-02-26
I am running a dell inspiron 1545 with an intel core2 duo @2ghz and 4gb of ram. I am fairly illiterate and inexperienced with computers, but I am a quick learner. I HATE!!! microsoft and especially windows. I used to have a mac and like the os but cant afford the hardware etc. I downloaded the 64bit ubuntu 8.10 iso from the ubuntu site, burned it to a disk and booted it, only to get to the screen with the option to install ubuntu and then it freezes... I have been searching for info on my particular case for 4 days now and am getting quite frustrated. I HATE windows and would really like to start running ubuntu or some similar linux based distro. Any help would be greatly appreciated.

will.

---

### Post by insulinaddict on 2009-02-28
I also have a 1545, installed fine other than wireless card detection. Think your problem is that you're trying to install 64bit, its only a 32bit processor.

---

### Post by b3rnd on 2009-03-23
Hello insulinaddict,

does the hardware (touchpad, nic, wlan, ...) work correctly with the inspiron 1545 under ubuntu?

Does it need any "hand work" or is everything recognized during installation?

---

### Post by crf on 2009-04-02
Hi, I just got a New Inspiron 15 (also called a dell Inspiron 1545 I think), core2 duo T6400.

I installed Ubuntu 8.10 64 bit from a DVD in Linux magazine, Ubuntu Special. It works well. I think all the hardware works, including wireless. Everything also worked while running it as a live-cd. 

Before installing, I used the windows Vista disk management tool to make enough room for linux. The Inspiron came with 3 partitions already: the main ntfs vista partition, a 15.7 GB recovery partition, and a very small 41 MB emergency recovery tools partition. I don't see any advantage to erasing these things.  

After using vista to create enough room at the end of the disk for linux, I ran the live-cd and created one partition for swap of sufficient size to hold all memory (see the command free -b), and one root partition for linux. I created the swap partition right after the windows partitions (so that it could also be a buffer, in case I needed the space later to enlarge either the windows or linux partitions). I installed linux. After installing I shrank vista's partition a bit more, then used gparted on the live cd to enlarge the swap partition since I miscalculated initially. With 4 GB of ram, I probably will never need to use the swap partition as a swap partition. I'm just using it as a hibernate (suspend to disk) partition, effectively.

Suspend to ram worked out of the box.
suspend to disk, or hibernate, required a bit of work. I'm not sure all of what I tried was strictly needed (I was working at the issue for a couple of hours over two days before getting it to work :( ). 

The power button can be set to suspend to ram, or suspend to disk, using the power management preferences.

If suspend to disk fails, here are some things you may wish to check. I'm not sure any one of these things are needed, but they are not *hurting* on my system. 

1) the uuids of your partitions in /etc/fstab
ls -l /dev/disk/by-uuid
sudo parted 
        print

these will show your partitions, and their UUIDs.

In the /etc/fstab file make sure that any partitions you wish to mount (like root and swap) are properly identified. Otherwise, using sudo, edit the /etc/fstab file so that UUIDs for the swap and root are as shown by the ls command.

2) In the /boot/grub/menu.lst file make sure the UUIDs are correct.

3) In the /boot/grub/menu.lst file, in the section
```
## additional options to use with the default boot option
```
change ```
#def options=quiet splash
``` to ```
#def options=quiet splash resume=/dev/X 
``` where X is the device number (like, for example, sda5) of your swap partition (here being used as a hibernate partition). Then do ```
sudo update-grub
```. Maybe read the Grub manual, I imagine you could specify where to resume as a UUID rather than as a device.

4) in /etc/initramfs-tools/conf.d/resume be sure the line is ```
RESUME=UUID=*your swap's uuid*
```.

5) in /etc/rc.local add ```
echo *your mem size in bytes* > /sys/power/image-size
``` as a line in the file, above ```
exit 0
```. This will change the default value every time you boot. I'm not certain it is necessary to do this.
  
====
I wish there was an ubuntu help page on how to get hibernate working. I don't think my method will work well if you have a low-memory computer, so that your swap is actually used for something.

==
What's the advantage of suspend to disk? You can be doing some work in linux, suspend, and then login to vista to do some work, log out of vista, and the login to linux to continue working right where you left off. In other words, you never have to shut down any of your two operating systems.

What's the disadvantage? If you suspend Vista to disk, and log in to linux, linux will warn you about mounting active vista partitions, if you try. (I have not tried yet to see what happens: but the warning seems appropriate.)

---

### Post by remiprev on 2009-04-05
> Hi, I just got a New Inspiron 15 (also called a dell Inspiron 1545 I think), core2 duo T6400.

I installed Ubuntu 8.10 64 bit from a DVD in Linux magazine, Ubuntu Special. It works well. I think all the hardware works, including wireless. Everything also worked while running it as a live-cd. 

Is your graphic card an Intel X4500 ? Have you tried with Compiz ?

---

### Post by crf on 2009-04-11
> **remiprev said:**
> Is your graphic card an Intel X4500 ? Have you tried with Compiz ?

I got, for graphics:
```
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102
```

I just installed the compiz-config settings manager, but I currently have desktop effects set to "none" in the appearance prefs (I'm not a fan of effects). It had been set to "normal" during Ubuntu's installation, but the only effect that I noticed were transparent windows: and I didn't like it, so I turned everything off. 

I'm not sure what all the possible compiz-config settings do! If there is something anyone wishes me to test, I'll try it though.

---

### Post by FedericoBArgentina on 2010-05-04
Hello!!!

I have only one question. Can you install Ubuntu if you already have installed Vista? Is not there a problem with the dual boot?

Thanks!

---

