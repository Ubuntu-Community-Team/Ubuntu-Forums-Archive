---
title: "[SOLVED] Want to dual boot without losing linux"
date: 2008-10-07
forum: General Help
---

### Post by timstone on 2008-10-07
Ok.  I would like to dual boot XP and linux.  I have 2 hard drives, a 30gb, which ubuntu is installed on, and 80gb, which has nothing....how can I go about doing this without overwriting the MBR or losing the grub loader?

---

### Post by Patb on 2008-10-08
Timstone, you will overwrite the MBR but it's no great cause for alarm. After installing XP, follow the guide here to get your grub back: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

There is plenty of guidance for how to back up your MBR but it's probably not worth worrying about. 

Hope this helps.  Cheers, Pat.

---

### Post by timstone on 2008-10-08
Ok so after I follow those instructions and I reboot and grub shows up, will it give me the choice to load ubuntu or xp at some point?

---

### Post by Patb on 2008-10-08
Not certain on that point, Timstone. It should give you both options but in any case, it is fairly simple to edit your grub menu "sudo gedit /boot/grub/menu.lst" and add/correct as necessary if either Ubuntu or XP grub entries are not functional. 

A good readable guide to grub is here.  [http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

If you decide to go down this route, please post if you have any problems. 

Cheers, Pat.

---

### Post by Calmatory on 2008-10-08
What about installing on different HDD's, and selecting from a list which HDD to boot from? This in case where the motherboard/BIOS supports such a feature(e.g. "Press TAB for boot menu" etc.). 

Though, installing grub shouldn't be that hard task either. :)

---

### Post by sir_cheats_a_lot on 2008-10-08
here is what i normally do when i wipe my windows installs after they start slowing down:
1). turn off the computer
2). unplug my ubuntu drive
3) reboot and install windows on the other drive
and finally,
4,5, & 6). turn the computer back off and plug the drive back in, and turn the computer back on, and i don't even lose my grub :popcorn:
not sure if grub will auto-detect it or not.. it might though.

out of curiosity though...why isn't the ubuntu install on the 80gb drive instead??

---

### Post by timstone on 2008-10-08
> **sir_cheats_a_lot said:**
> here is what i normally do when i wipe my windows installs after they start slowing down:
1). turn off the computer
2). unplug my ubuntu drive
3) reboot and install windows on the other drive
and finally,
4,5, & 6). turn the computer back off and plug the drive back in, and turn the computer back on, and i don't even lose my grub :popcorn:
not sure if grub will auto-detect it or not.. it might though.

out of curiosity though...why isn't the ubuntu install on the 80gb drive instead??

Well, to be honest it was installed on both drives accidentally, and since this drive is the one that boots, I just used this one.....we all know windows takes more space anyways :)


If I use your method of unplugging the ubuntu drive and installing, i still need to use the live cd to convert the other drive over to NTFS, right?

---

### Post by Patb on 2008-10-08
> **Calmatory said:**
> What about installing on different HDD's, and selecting from a list which HDD to boot from? This in case where the motherboard/BIOS supports such a feature(e.g. "Press TAB for boot menu" etc.). 
Isn't that a bit crude? I thought one of the reasons for the development of boot loaders like Grub was to avoid having to go into the BIOS to change the boot partition.

> **sir_cheats_a_lot said:**
> ... and i don't even lose my grub ... not sure if grub will auto-detect it or not.. it might though.
Grub does not auto-detect during normal boot-up; it will use the options listed in /boot/grub/menu.lst. Grub does try to detect and configure itself for all operating systems during the "grub install" process (see the above links in this thread). Your method will work fine as long as the Windows boot partition still retains its previous designation (as is likely) when you reconnect the drive. 

> **timstone said:**
> If I use your method of unplugging the ubuntu drive and installing, i still need to use the live cd to convert the other drive over to NTFS, right?
Not sure what you mean here.  You would not convert the format of a drive but a partition. If it already has a working XP, it will be either NTFS or FAT32 format already - the Windows install will presumably take care of that. You just need to tell the Windows installer where you want it to install (but I'm not a Windows user so I'm not sure on this). 

Hope this helps. Cheers, Pat.

---

### Post by timstone on 2008-10-08
Ok I got XP installed again, how can i find out where that XP drive is located (i.e.  hd(0.1) )so i can edit my grub menu?

Also, I know if I push ESC at the grub loading screen it will give me an option for like recovery mode and all that jazz...but is there a way to make it show me a list of both OS's so I can choose which I want to start when the PC boots?

---

### Post by Patb on 2008-10-08
Sounding good Timstone. To see your partitions, go to a terminal and type:
```
sudo fdisk -l
```
You may also need the UUIDs for your partitions which will be given by:
```
sudo blkid
```
Does Windows appear on your boot menu now? If so, what happens when you choose it? Please post any errors. 

If you want more specific instructions, please post the output of the above commands and also this one:
```
cat /boot/grub/menu.lst
```
Cheers, Pat.

---

### Post by timstone on 2008-10-08
Ok, I did the sudo fdisk -l and got this output....

```

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         860     6907918+  83  Linux
/dev/sdb2   *         861        9349    68187892+   7  HPFS/NTFS
/dev/sdb3            9350        9726     3028252+   5  Extended
/dev/sdb5            9350        9726     3028221   82  Linux swap / Solaris

```

so /dev/sdb2  is going to be the one i want to add

---

### Post by Patb on 2008-10-08
Yes, but as you may have seen on the links I quoted, the designation of disks/partitions for grub starts at 0 whereas for linux, it starts at "a" or 1.  So in your menu.lst file, you will need to add something like:
```
title        Microsoft Windows XP
root        (hd1,1)
savedefault
makeactive
chainloader    +1
```

Let us know how you go.  If it works okay, please mark the thread solved. If not, see my last post.

Cheers, Pat.

---

### Post by timstone on 2008-10-08
adding that to menu.lst didn't do anything....I rebooted and when grub appeared I hit ESC and selected the XP item I added and it just hung on a screen that said "Starting up...."

---

### Post by caljohnsmith on 2008-10-08
When you try and boot Windows XP from any drive other than the boot drive like you are trying to do, you have to use Grub's mapping technique to fool Windows XP into thinking it is on the boot drive:
```
title	   Windows XP
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Give that a shot and let me know what happens. :)

---

### Post by timstone on 2008-10-08
> **caljohnsmith said:**
> When you try and boot Windows XP from any drive other than the boot drive like you are trying to do, you have to use Grub's mapping technique to fool Windows XP into thinking it is on the boot drive:
```
title	   Windows XP
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Give that a shot and let me know what happens. :)

that did it...thanks!

---

