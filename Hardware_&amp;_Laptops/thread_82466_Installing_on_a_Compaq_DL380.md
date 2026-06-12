---
title: "Installing on a Compaq DL380"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by kmcgregor-cow on 2005-10-26
I've been trying to install 5.10 on a RAID array on a Compaq ProLiant DL380. It recognizes all hardware and runs through the  first part of the install fine. After the last screen where it says it will reboot and finish installing some more software, after the reboot it complains about /dev/ida/c0d0p1 not being there any more. Where did it go? Is the cpqarray.o module built into the kernel?

---

### Post by crmanski on 2005-10-27
I am having the same exact problem when trying to install to a Compaq Proliant ML370 with a compaq smart array 420 card.  I have tried different install options noapic, nolapic, etc, but nothing seems to work...

---

### Post by vjshah on 2005-10-28
I managed to get the job done. The problem is that the installer does not know enough to add the modules necessary for your hardware to the initrd.img. So you have to build a new initrd.img with the additional modules.

Here are the steps (from memory):

1. Use your install CD to boot into rescue mode (insert CD and type "rescue" at the Boot: prompt).

2. mkdir /target; mount /dev/ida/c0d0p1 /target (or whatever is your root partition. NB I did not have to provide any options. I did not have my partition map handy so I just mounted every partition on an empty dir and viewed the contents to figure out what was in each partition.)

3. If you created separate boot and usr partitions, mount the partitions on /target/boot and /target/usr (you are recreating the required tree under /target). You don't need any other partitions.

4. chroot /target (now it looks like you are in your installation).

5. add cpqarray to /etc/modules (nano /etc/modules and add "cpqarray" as the last line).

5. /usr/sbin/mkinitramfs -o /boot/initrd.img /lib/modules/2.6.12-9-686/ (this will build the new initrd.img in /boot).

6. Cd to /boot and verify that you are happy (I just ensured the new img was larger than the old one). Then backup the old img and rename the new img to the same name as the old img (initrd.img-2.6.12-9-686 for me).

7. Reboot. Everything went smoothly after that.

---

### Post by crmanski on 2005-10-28
Thanks, I might try this. My initial thought is: "What happens when there is a kernal update down the road. Will I have to do this each time?
In another post elsewhere in the forums ( [http://ubuntuforums.org/showthread.php?t=53894](http://ubuntuforums.org/showthread.php?t=53894) ) someone mentioned that Debian Sarge does not cause this problem. So I might use that on the server and avoid future headaches...

---

### Post by vjshah on 2005-10-31
I might have got step 5 wrong. The actual file is /etc/mkinitramfs/modules.

Haven't had to make a new kernel yet so don't know about that.

---

### Post by TragicWarrior on 2005-10-31
Thanks vjshah!

Using the steps you provided here, I was able to resolve the problem on my desktop workstation which uses the Mylex dac960 raid controller (same problem as the smartarray controller).

Step 5 was indeed incorrect but once I figured out the correct file it was okay.  Also, I think the 3rd args for mkinitramfs is not /lib/modules/2.6.12-9-386 but rather just the version number.  So:

/usr/sbin/mkinitramfs - /boot/initrd.img 2.6.12-9-386

:)

---

### Post by jwilsie on 2005-11-01
"vjshah :I might have got step 5 wrong. The actual file is /etc/mkinitramfs/modules."

I had to use this to get it to work correctly.

Thanks for the great fix vjshah!

---

### Post by snipes on 2005-11-08
Tried install 5.10 onto a Compaq Proliant 1600 and had the same issue. I find it weird it can find the initrd.img on the drive, but can't mount it.

Anyway, I followed the instructions and couldn't get it to work.

Going into 'rescue' mode, I let the CD do its thing when it errored at the Rescue part of the procedure. It happens after going through the partitions setup (sorry, at work, so I don't have the server on hand to get the names right).

Once the select step comes up, I can go to the option to open a shell.

No issues with Step 2, and Step 3 didn't apply.

The rest is a little bit of a nightmare. I used chroot easily enough, but trying to use nano in it failed. Said it couldn't find the little fellow. So I exited and editted the modules file outside of the chroot shell (Nano worked just fine from there).

When I returned to the chroot shell, I made sure the modules file had the cpqarray listed in the file, and it did. Is this ok? The target directory dissappears after reboot, so am I altering files that are sitting in RAM?

Using the mkinitramfs, I got an initrd.img only 40 odd bytes larger than the original. I think this is where I may have gone wrong, as I can't remember if I used /etc/mkinitramfs/modules or just 2.6.12-9-386 for the third parameter.

I spent most of last night trying to fix this before letting Debian Sarge install via a network install CD. It had no issues and booted up cleanly, but I intend to try Ubuntu again tonight to make sure I didn't stuff up. I would prefer to use just one distribution in the house... Plus I want to put Ubuntu and the Linux Terminal Service Project on my Proliant 5500 :D

---

### Post by snipes on 2005-11-09
Nevermind on the RAM thing, I actually read the dialog box :???: 

nano refuses to work in the chroot shell however.

Also, using "/usr/sbin/mkinitramfs -0 /boot/initrd.img /etc/mkinitramfs/modules" reports "/etc/mkinitramfs/modules is not a valid kernel version".

So I'm kinda stumped. Any suggestions out there?

---

### Post by Crackez on 2005-11-28
After following vjshah's revised directions, with the DAC960 RAID controller, my machine booted fine. I could not run nano in the chroot, but I could use vim. The TERM environment variable caused me some grief, even after setting it to Linux :( but this worked for me:
^x
:9
o
DAC960 <esc>
:wq

I suppose you could also do: echo DAC960 >> /etc/mkinitramfs/modules


--Andy

---

### Post by outstanding on 2005-12-05
Hi Team

I have a Compaq DL380, with 4 X 18.2Gb drives in raid 5.
I am an absolute newbie at Linux, could you list the steps I need to do to get Ubuntu installed, were the files are, how to access them and with what program to use etc.
Thanks
Craig

---

### Post by JBBxWolf on 2006-04-11
[QUOTE=snipes]Nevermind on the RAM thing, I actually read the dialog box :???: 

nano refuses to work in the chroot shell however.

Also, using "/usr/sbin/mkinitramfs -0 /boot/initrd.img /etc/mkinitramfs/modules" reports "/etc/mkinitramfs/modules is not a valid kernel version".

So I'm kinda stumped. Any suggestions out there?[/QUOTE]

replace  the nano syntax with   vi    this worked for me.. 

the command I used to build the initrd.img was: 

/usr/sbin/mkinitramfs -o /boot/initrd.img /lib/modules/2.6.12-9-686/

that worked like a charm..

---

### Post by JBBxWolf on 2006-04-11
[QUOTE=Crackez]After following vjshah's revised directions, with the DAC960 RAID controller, my machine booted fine. I could not run nano in the chroot, but I could use vim. The TERM environment variable caused me some grief, even after setting it to Linux :( but this worked for me:
^x
:9
o
DAC960 <esc>
:wq

I suppose you could also do: echo DAC960 >> /etc/mkinitramfs/modules


--Andy[/QUOTE]

I usually will just do 

export TERM=DAC960
then execute vi

---

### Post by CiaranG on 2006-04-16
Many thanks vjshah, that solved the problem for me. (DL380, cpqarray) The same fix is required, and works, for both Breezy and the latest Dapper. I gave mkinitramfs just the version number.

---

### Post by DavidRa on 2006-05-20
[QUOTE=snipes]Nevermind on the RAM thing, I actually read the dialog box :???: 

nano refuses to work in the chroot shell however.

Also, using "/usr/sbin/mkinitramfs -0 /boot/initrd.img /etc/mkinitramfs/modules" reports "/etc/mkinitramfs/modules is not a valid kernel version".

So I'm kinda stumped. Any suggestions out there?[/QUOTE]Seems that you've used "mkinitramfs -0" (zero) instead of "mkinitramfs -o" (Oscar).

---

### Post by rwilson on 2006-12-06
Thanks vjshah, worked perfectly!

Although, nano didn't work for some reason. I used vi.

---

### Post by mootpoint on 2007-03-19
Beginning with Edgy AKA 6.10, the file that needs editing has moved:

nano /etc/initramfs-tools/modules

instead of:

nano /etc/mkinitramfs/modules.

Hopefully that will save someone some of the frustration I went through. :-)

m00t

P.S. After I got the box working, I compiled a 2.6.20 kernel. As long as cpqarray is listed in the modules file, compiling new kernels works just fine. 

If anyone wants to use the .deb's to upgrade kernels, that would work fine, IF AND ONLY IF you follow this process for the new kernel after installation. The initrd.img file in the repository won't have cpqarray built in, which is why this problem happens in the first place.

---

### Post by punda on 2007-04-02
Hi,

I'm in trouble with Edgy and a DAC960 controller, 3 disks in raid5 with reiserfs: i followed your instructions but my GRUB says:

Error 17 

everything i change... so  i tryed debian-sarge net-inst and all went ok...

any suggestion? I want my server to "wear" an ubuntu...

BTW: tried with dapper drake and Grub Error "switch" to 18... ;-(

PS. firmware on the board is the latest: 2.73

cya,

Punda

---

