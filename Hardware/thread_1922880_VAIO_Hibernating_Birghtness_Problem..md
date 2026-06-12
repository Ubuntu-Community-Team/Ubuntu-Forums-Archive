---
title: "VAIO Hibernating Birghtness Problem."
date: 2012-02-09
forum: Hardware
---

### Post by jhonnytunes on 2012-02-09
Hi Ubuntu Masters.

I've recently installed oneiric in my VAIO laptop and everything is fine. Well almost. Somethings are not working:

1-I cant Hibernate: Neither by unity menu nor the 'pm-hibernate' command. AFAIK it does hibernate because the disk led is blinking when I ordered. But when I turn it on again it shows the login screen instead of the unlock screen asking for the password.

2-I Cant Change the Brightness of the screen. When I press the Fn+key combination, unity display the modal panel displaying the supposed brightness level, but it just remain the same always.

3-My Memory Stick Pro Duo integrated card reader neither works. This have two card readers, the one I just mentioned and one for SD cards(This works perfectly).

4-Blank Virtual Terminals. I Cannot Crtl+Alt+ F* anymore. Also Ubuntu splash gets a littler lower resolution. This used to work before I Change from Nouveau to NVIDIA driver.



My Laptop: Sony Vaio CW VPCCW19FX.
My Video Card: NVIDIA GFORCE with CUDA G210M.
My Card Reader: Ricoh Co Ltd Memory Stick Host Controller.
My Kernel: 3.0.0-15-generic 64bits
My NVIDIA Driver: nvidia_current_updates (Via Jockey)


Anything else you need please let me know.

[http://pastebin.com/4NJfr4Pm](http://pastebin.com/4NJfr4Pm) >> My PC-Config

---

### Post by ahallubuntu on 2012-02-09
How much RAM do you have?  How large is the swap partition?

I have done little with Oneiric but have spent time with hibernation in Natty.  Hibernation actually works beautifully in Natty but the installer in one case did not make the swap space quite large enough to make hibernation work.  I enlarged the swap just a smidgen with the live CD to be just as big as the RAM, and hibernation (or the resume from hibernation, to be precise) worked beautifully after that.

FYI, the swap space is used to save off a snapshot of your RAM during hibernation, so if it's smaller than the amount of RAM you have, it may not work.

I use gparted to check partition sizes and to resize.  I'm not sure it's included in the Oneiric CD anymore - you may have to use a different live CD (like Parted Magic) to resize.  Or you can install gparted in a live CD (one time til you end the session) if you are on the internet while it's booted...

There are solutions for the brightness keys for various laptops.  I fixed it for a few of mine - involves adding a string to your /etc/default/grub file and update-grub.  Google for it, I forget exactly how I did it.

---

### Post by jhonnytunes on 2012-02-09
Thanks for your Reply.

I have 7971MB of RAM and 7.81GB of SWAP. Do you think if I resize the swap it will work?

---

### Post by ahallubuntu on 2012-02-09
> **jhonnytunes said:**
> Thanks for your Reply.

I have 7971MB of RAM and 7.81GB of SWAP. Do you think if I resize the swap it will work?

Resizing the swap to make it 8.00GB exactly (or slightly more if you aren't sure of the math in Gparted) it is the first thing I would do.  Err on the size of a few more MB to the swap than a few less.

If that means resizing a partition next to it that has any sort of important data on it, make sure you backup that data before attempting a resize operation.  Partition resizing with Gparted is very reliable but still the possibility of an error exists, and that could cause you to lose all data in that partition.  Partition resizing can take a long time, but since you aren't adding that much to the swap, it might not take much time in your case.

---

### Post by jhonnytunes on 2012-02-09
SWAP now is ~16GB. Hibernate not working yet. VAIO-buntu sucks. I got to change this for a DeLL 1.

---

### Post by ahallubuntu on 2012-02-09
> **jhonnytunes said:**
> SWAP now is ~16GB. Hibernate not working yet. VAIO-buntu sucks. I got to change this for a DeLL 1.

Sorry to hear that.  Hibernation/Suspend issues can be challenging in Ubuntu on laptops, unfortunately.  I have an Acer netbook that suspends/resumes fine 9/10 times but the 10th time it freezes and I have to do a hard shutdown.

Some Dells (like mine) definitely work better, in part because Dell some of their laptops with Ubuntu not Windows on them, so they work out some of the issues like this.  My Dell is extremely reliable with suspend and hibernation on Ubuntu 10.04 LTS.

---

### Post by jhonnytunes on 2012-02-09
I consider my laptop is a War Tank, everything is powerful but the procesor. But VAIO is not made for the penguin. I think I should think about change this.

---

### Post by Toz on 2012-02-09
> **jhonnytunes said:**
> 
1-I cant Hibernate: Neither by unity menu nor the 'pm-hibernate' command. AFAIK it does hibernate because the disk led is blinking when I ordered. But when I turn it on again it shows the login screen instead of the unlock screen asking for the password.
You have an encrypted swap partition. Unfortunately hibernate does not work with encrypted swap partitions.

> 2-I Cant Change the Brightness of the screen. When I press the Fn+key combination, unity display the modal panel displaying the supposed brightness level, but it just remain the same always.
Two suggestions. Either/and:
[LIST=1]
[*]Add:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of your xorg.conf file (log out and in again for it to take effect)
[*]Add:
```
acpi_backlight=vendor
```
...to the kernel boot line (see: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot") for temporary test procedures
[/LIST]

---

### Post by jhonnytunes on 2012-02-10
Hey, Thanks for the reply. I tested the option in the Xorg file and the argument after the kernel in the grub2 boot screen, didnt work. Thanks for the swap tip, im gonna work on that.

Sorry for make you lost your time, I Think I got to change to Dell  Laptop soon or early because they support linux. Esta mierda, make me lose time while working on college project.

---

### Post by mebomechanicno1 on 2012-02-10
> **jhonnytunes said:**
> SWAP now is ~16GB. Hibernate not working yet. VAIO-buntu sucks. I got to change this for a DeLL 1.
 
Vaio really are not good with linux, but I am now having excellent results running 11.10 on mine, but since it worked straight out of the box I am unlikely to be able to help.

---

### Post by Rafterman414 on 2012-02-10
I've actually had pretty good results on my VAIO VGN-CS215J, the only issue that I run into is that the keyboard does not function after resuming from sleep.

---

### Post by Toz on 2012-02-10
> **Rafterman414 said:**
> I've actually had pretty good results on my VAIO VGN-CS215J, the only issue that I run into is that the keyboard does not function after resuming from sleep.

Have you tried the **i8042.reset** kernel parameter? I've had luck in the past resolving a similar problem with this parameter.

---

### Post by Rafterman414 on 2012-02-10
> **Toz said:**
> Have you tried the **i8042.reset** kernel parameter? I've had luck in the past resolving a similar problem with this parameter.

I have not tried it, usually what I do is just use the on screen keyboard to login and then reboot or SSH from another machine and reboot that way. The keyboard still wakes the machine from sleep so I might also try SysRQ + REISUB to see if that works.

For the OP I'll try out the brightness changing thing on my machine when I get home to see if that is something common to VAIO laptops running Ubuntu. I don't think I have ever tried to change brightness, I'll report back after I try it.

---

### Post by jhonnytunes on 2012-02-10
Im not really good at Linux. Im just a novice. I googled some solutions and will try them. I'll post my result for others VAIObuntus...

Regards.

---

