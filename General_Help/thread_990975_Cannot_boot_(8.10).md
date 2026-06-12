---
title: "Cannot boot (8.10)"
date: 2008-11-23
forum: General Help
---

### Post by TheGuyWhoGotOn on 2008-11-23
I may be in 8.10 beta still I have all the upgrades though.

Okay everything was running fine (GRUB loaded my system properly) but then I installed Mandriva. I had to install their GRUB bootloader because my current one wouldn't detect Mandriva. So I did, after I decided that I liked Ubuntu a lot better and booted back into Ubuntu. I then removed the Mandriva partitions and restarted my computer. It wouldn't boot...Just and error (Like error 2 or something like that). Okay, I insert the Ubuntu 7.10 Live CD because I can't find my 8.10 Beta disk. I boot using that...Then I run "sudo grub-install hd0". Seemed to work fine...Restart my computer...GRUB loads I pick Ubuntu 8.10...Then I get an error about a missing/bad file/directory...It doesn't say what file/directory...Just that it's missing/bad...

After all that I install Ubuntu 7.10 on another partition, restart my computer and I can boot in 7.10 and not 8.10 (Because some file/directory is missing/bad)...Please help?

---

### Post by caljohnsmith on 2008-11-23
How about posting the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
sudo blkid
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```
And please post the output of all the above commands. We can work from there if you want.

---

### Post by TheGuyWhoGotOn on 2008-11-23
> **caljohnsmith said:**
> How about posting the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
sudo blkid
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```
And please post the output of all the above commands. We can work from there if you want.

I'm pretty sure it's sda1 but I will give you the output...Also don't forget one partition is Ubuntu 7.10 and one is Ubuntu 8.10 so they are both Linux. The smaller one is 7.10 because I think I gave it roughly 12GB.

(With Ubuntu 7.10 on my laptop (The computer we're trying to fix) the USB ports don't work and neither does file sharing -.- so I'm using MediaFire)
[http://MediaFire.com/?c8c0deyzmy0](http://MediaFire.com/?c8c0deyzmy0)

Thanks for your help :)

---

### Post by caljohnsmith on 2008-11-23
OK, I misunderstood your original post; I think I might know what the problem is. When you boot 8.10, do you get a Grub error 2? If so, it's most likely because Intrepid now formats its ext3 partitions to use a larger inode size for the file system (256 bytes vs. previous Ubuntu versions that used 128 bytes); if you try and boot an Intrepid partition using an older Grub (like 7.10 uses) that can't handle the newer ext3 partitions, Grub chokes with an error 2. 

I think the easiest solution for your dilemma is to simply let Intrepid's Grub take control of the booting process, rather than 7.10. You should be able to boot both 7.10 and Intrepid no problem if you use Intrepid's Grub. Does that sound like an OK solution? If so, how about posting:
```
sudo fdisk -lu
```
And please identify your partitions. We can work from there if you want. :)

---

### Post by TheGuyWhoGotOn on 2008-11-23
I want to use Intrepid's GRUB but I can't boot into Intrepid :). And the MediaFire link above contains that output here's what it basically says:

sda1 = Ubuntu 8.10 (Also has boot flag)
sda2 = Swap
sda3 = Ubuntu 7.10

---

### Post by caljohnsmith on 2008-11-23
OK, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
That will install Grub to the MBR and have it point to your Intrepid partition for its boot files. After that, reboot, and let me know how far you get. 

P.S. Thanks for the info from your Mediafire link; if it's possible, can you post the output of the above commands into your next post? You can highlight them and then press the pound sign # graphic at the top of the message box to put "code" tags around it. :)

---

### Post by TheGuyWhoGotOn on 2008-11-23
> **caljohnsmith said:**
> OK, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
That will install Grub to the MBR and have it point to your Intrepid partition for its boot files. After that, reboot, and let me know how far you get. 

P.S. Thanks for the info from your Mediafire link; if it's possible, can you post the output of the above commands into your next post? You can highlight them and then press the pound sign # graphic at the top of the message box to put "code" tags around it. :)

Sorry, I'm on this website VIA my desktop and my laptop on Ubuntu 7.10 has issues...Of course they can be resolved but I'm planning on removing Ubuntu 7.10...I could upload the next file to my webserver if you want so you can view it online.

Actually the output is short...

```

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type

```

Wait /media/sda1/boot/grub/stage1 does exist...

---

### Post by caljohnsmith on 2008-11-23
OK, I see what happened; I forgot that you are using your 7.10 Live CD to run those Grub commands, is that true? If so, that Grub error 2 that you got is for the reasons I mentioned in my previous post. Since you can't boot your 8.10 CD right now, we can work around it by doing the following from your 7.10 CD:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
exit
```
What the above commands do is effectively boot you into your sda1 partition via the "chroot" after mounting all the system directories; that way you can run the Grub commands with Intrepid's version of Grub, so you hopefully won't get the Grub error 2. Please post the output of all the above commands in any way that is convenient for you. :)

---

### Post by TheGuyWhoGotOn on 2008-11-23
> **caljohnsmith said:**
> OK, I see what happened; I forgot that you are using your 7.10 Live CD to run those Grub commands, is that true? If so, that Grub error 2 that you got is for the reasons I mentioned in my previous post. Since you can't boot your 8.10 CD right now, we can work around it by doing the following from your 7.10 CD:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt /bin/bash
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
exit
```
What the above commands do is effectively boot you into your sda1 partition via the "chroot" after mounting all the system directories; that way you can run the Grub commands with Intrepid's version of Grub, so you hopefully won't get the Grub error 2. Please post the output of all the above commands in any way that is convenient for you. :)

Thanks :) I am not using the live CD I installed 7.10 and what's also odd is I tried this:

```

grub> root (hd0,2)

grub> install /media/sda1/boot/grub/stage1 (hd0) /media/sda1/boot/grub/stage2

Error 15: File not found

```

I'm running your commands now...

[http://PhoenixProgramming.org/files/Output.txt](http://PhoenixProgramming.org/files/Output.txt)

Now what should I do? :).

Okay I ran "sudo grub-install hd0" it seemed to work should I restart?

---

### Post by caljohnsmith on 2008-11-23
After doing the "chroot", just follow with the rest:
```
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
exit
```
And please post the output.

---

### Post by TheGuyWhoGotOn on 2008-11-23
> **caljohnsmith said:**
> After doing the "chroot", just follow with the rest:
```
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
exit
```
And please post the output.

Doesn't that do the same as what I just did?  ^_^ here's the output: [http://PhoenixProgramming.org/files/Output.txt](http://PhoenixProgramming.org/files/Output.txt)

It works :) Thank you, I can't boot into 7.10 but I'm deleting that anyways.

---

### Post by caljohnsmith on 2008-11-23
The grub-install command will reinstall all of Grub's stage files to /boot/grub in addition to installing Grub to the MBR, so you really didn't need to use it; doing the Grub commands from the command line as I gave them would have been sufficient, but both will work in your case. Go ahead and reboot, and let me know how far you get.

---

### Post by TheGuyWhoGotOn on 2008-11-23
> **caljohnsmith said:**
> The grub-install command will reinstall all of Grub's stage files to /boot/grub in addition to installing Grub to the MBR, so you really didn't need to use it; doing the Grub commands from the command line as I gave them would have been sufficient, but both will work in your case. Go ahead and reboot, and let me know how far you get.

Thanks :), I booted up fine, deleted 7.10 and all is right in the world again. Your help has been greatly appreciated :) now I can work on making my updater in Python :).

---

### Post by caljohnsmith on 2008-11-23
Glad you're up and running again; cheers and have fun with Ubuntu. :)

---

