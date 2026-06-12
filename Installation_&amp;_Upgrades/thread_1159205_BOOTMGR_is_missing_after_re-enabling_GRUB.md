---
title: "BOOTMGR is missing after re-enabling GRUB"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by 47_MasoN_47 on 2009-05-14
Here's my scenario.  My laptop originally had a 40GB hard drive (it's a 2005 IBM Thinkpad G41), and that simply was too small so I bought a 160GB drive.  I used partimage and backed up my Ubuntu partition to a USB hard drive, installed the new drive, and restored the partition.  Then I setup 2 more partitions for Windows installs.  Here's how it's laid out.

hd0,0 - Ubuntu 9.04
hd0,1 - Windows 2000 (for WoW only)
hd0,2 - Windows 7 RC

After copying the Ubuntu partition I installed Win2k, then Win7RC.  With the MS bootloader I could boot Win2k and Win7RC without problem.  I wanted to get my Ubuntu back, and prefer GRUB so I used the GrubHowTo in the Ubuntu docs to re-enable it.  After enabling GRUB, Ubuntu boots fine (partimage is FTW) but when I try to boot Win7 it gives me the annoying error below:
> BOOTMGR is missing
Press Ctrl+Alt+Del to restart
I'd like to be able to use Win7 to test on our domain at work, and it actually runs quite well on this old laptop.  Please offer some suggestions for how I can fix this!

---

### Post by 47_MasoN_47 on 2009-05-14
I booted up SuperGrubDisk, selected Windows, then selected boot Windows from 2nd Partition (Laptop) and the Windows bootloader started, allowing me to boot either Win2k or Win7RC.

So...since I know that this works, can someone please help me get it to work with the GRUB I have installed on my MBR so I don't have to boot from the CD every time I want to use Windows?

Thanks.

---

### Post by 47_MasoN_47 on 2009-05-15
Anybody have any ideas?

---

### Post by Belboz99 on 2009-05-15
Hey,

I found your thread earlier when I was having this exact scenario earlier today.

Just now I realized that Win7 creates at least 2 partitions when you install it, even though you may have only one selected and formatted for it's use.

Basically, from what I gather there should be a partition of around 8MB just before or after the actual installation partition for 7.

So, all you have to do to fix this issue is change your target drive for the Win7 OS to the 8MB partition that sits somewhere near the Windows 7 partition.

Try checking our your GParted list of partitions, or if handy with a CLI, use fdisk to check out the list of partitions and their sizes.   You should find one with a very small capacity formatted as NTFS.

In my case though, it was before Win7 install parition.  So, I had done all this before-hand to determine the install partition,  and of course pointing GRUB to this install partition yielded only "BOOTMGR not found".

For me, simply changing (hd0,3) to (hd0,2) resolved my problem.


Hope this helps,
Dan O.

---

### Post by 47_MasoN_47 on 2009-05-15
You are now my hero.

Thanks man, that's exactly what was going on with mine!

---

### Post by ramzai on 2009-07-23
And what is even worse, Win7 may put its bootloader to other existing FAT or NTFS partitions, even on the other hd, as it was in my case. I installed Win7 to (hd1,2) and then found bootmgr file on the (hd0,2) partition with music and video files. That is completely sick.

Belboz99, thanks for the tip.

---

### Post by Swamprat2010 on 2009-11-09
I am having the same problem. My set-up is as show below. It does not seem to make any difference if I use root        (hd0,4) then I get 'Invalid Device Selected' or root        (hd0,3) then i get 'BOOTMGR' is missing '

Any Ideas how to fix this?  If only I didn't need Visual Studio and Solid-works =(( 


GRUB 
> 
title        Windows 7
root        (hd0,4)    OR   root        (hd0,3)
makeactive
chainloader    +1
GPARTED:
> 
/dev/sda1    /home
/dev/sda2    extended
/dev/sda5    linux-swap
/dev/sda6    /
/dev/sda3    ntfs System Reserved 100Mb
/dev/sda4    ntfs --boot


---

### Post by confused57 on 2009-11-10
```
/dev/sda3 ntfs System Reserved 100Mb
```

This should probably be root (hd0,2), if you haven't
tried it already.

---

### Post by Swamprat2010 on 2009-11-11
(hd0,4) = 'Invalid Device Selected' 
(hd0,3) = 'BOOTMGR' is missing '

=((  any-idea how to fix the BOOTMGR. My guess is that (hd0,3) is the correct one but that something else needs tweaking.

Just to be clear Kubuntu works fine. I'm just trying to get Windows 7 on duel boot.

---

### Post by Mark Phelps on 2009-11-11
The partition labeled System Reserved is most probably the one you want to use to boot.  So, have you tried the (hd0,2) as previously suggested?

---

### Post by Swamprat2010 on 2009-11-14
You are indeed right my friend its working fine now. I don't get why though ?
I would have thought that
 
> /dev/sda3    ntfs System Reserved 100Mb
/dev/sda4    ntfs --boot 

is where I should have pointed it seeing as its NTFS and window'seee.... the extended part is 97Gig and /dev/sda4 is about the same which is where i thought windows install would be/is.

All confused but its working =)) 
Thanks for the help.

---

### Post by Aprajita on 2011-10-08
(it worked for my windows 7 system..and for rest i dont know :|)
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]98F0CFF3F0CFD622[/COLOR]
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

find this part in your /boot/grub/grub.cfg
and edit this uuid(in red) in second last line
replace it with the uuid of "system reserved" folder 

for those who dont know what uuid is..just google it..nyways 
type sudo blkid

and u will see the uuid of System reserved folder..copy it and paste it over the red coloured part..
and be happy :) :D
cheers

---

### Post by Rubi1200 on 2011-10-08
Thread closed.

Reason: necromancy

@Aprajita; if you have a support request, please start a new thread.

---

