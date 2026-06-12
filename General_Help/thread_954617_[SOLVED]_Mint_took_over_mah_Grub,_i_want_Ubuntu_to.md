---
title: "[SOLVED] Mint took over mah Grub, i want Ubuntu to be in charge of that"
date: 2008-10-21
forum: General Help
---

### Post by earthpigg on 2008-10-21
I think the thread title explains it pretty plainly :)

using qgrubeditor, i am able to see that Ubuntu updated its grub to use the -21 kernel... but when my computer starts up, it is looking at the grub stored on my Linux Mint partition.

Ubuntu (and the partition it lives on) is my primary OS, i just want to play around on the rest, be able to format it worry free, etc.

so, whenever i install some other random distro-of-the-week and they take over the grub.... how to i give ze powa of ze grub back to ubuntu?

---

### Post by OrangeCrate on 2008-10-21
Install "Startup-Manager" from Synaptic. You can control which kernel/operating system boots first from there. After installation, there will be an entry on the System > Administration menu.

---

### Post by caljohnsmith on 2008-10-21
You'll need to reinstall Grub to your MBR so that it points back to your Ubuntu partition and not the Mint partition. Just do the following:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Mint and Ubuntu partitions in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whichever one is Ubuntu as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then to boot Mint, you could add to your /boot/grub/menu.lst in Ubuntu the following:
```
title Mint Grub Menu
configfile (hdX,Y)/boot/grub/menu.lst
```
Where (hdX,Y) is the Mint partition. Or you could use Startupmanager or something like that maybe. :)

---

### Post by earthpigg on 2008-10-21
> **OrangeCrate said:**
> Install "Startup-Manager" from Synaptic. You can control which kernel/operating system boots first from there. After installation, there will be an entry on the System > Administration menu.

i have it installed on both Ubuntu and Mint. when i open it in Ubuntu, it shows the info for the grub that is kept on the Ubuntu partition.

when i open it in Mint, it shows the info for the grub that is kept on the Mint partition.

when i turn my computer on, it is using the grub that is kept on the Mint partition.

i want it to look at the grub kept on my Ubuntu partition, so i can wipe mint when/if i feel like it... i see no obvious way in SUM to do that.

---

### Post by OrangeCrate on 2008-10-21
> **earthpigg said:**
> i have it installed on both Ubuntu and Mint. when i open it in Ubuntu, it shows the info for the grub that is kept on the Ubuntu partition.

when i open it in Mint, it shows the info for the grub that is kept on the Mint partition.

when i turn my computer on, it is using the grub that is kept on the Mint partition.

i want it to look at the grub kept on my Ubuntu partition, so i can wipe mint when/if i feel like it... i see no obvious way in SUM to do that.

Control start-up manager from whatever OS you installed last (shown first on your grub menu). I don't think start-up manager on the original OS will control anything *, until it's the first operating system, by deleting the other partition. As you saw, there's an option in the middle of the page to change which kernel/operating system boots first.

* At least, that's how it works on my two partitions. I have Intrepid in one partition, and I installed Hardy as a backup in another. I discovered that I have to control start-up manager from Hardy, the last OS installed. In Intrepid, it does nothing.

---

### Post by earthpigg on 2008-10-21
> **OrangeCrate said:**
> Control start-up manager from whatever OS you installed last (shown first on your grub menu). I don't think start-up manager on the original OS will control anything *, until it's the first operating system, by deleting the other partition. As you saw, there's an option in the middle of the page to change which kernel/operating system boots first.

* At least, that's how it works on my two partitions. I have Intrepid in one partition, and I installed Hardy as a backup in another. I discovered that I have to control start-up manager from Hardy, the last OS installed. In Intrepid, it does nothing.

so you are saying that if i simply format the Mint partition it will default to the grub kept on the ubuntu one?

---

### Post by OrangeCrate on 2008-10-21
> **earthpigg said:**
> so you are saying that if i simply format the Mint partition it will default to the grub kept on the ubuntu one?

No, unfortunately that's not what I'm saying.

I've shown you how to get Ubuntu to boot first, and mentioned that you would need to control which operating systems are on your computer by managing the partitions.

If it's more than that, I can't help you. I'd suggest you take a hint/direction from post #3, and start from there.

Plus, I'm sure that others will come along with additional ideas...

---

### Post by earthpigg on 2008-10-21
thanks, caljohnsmith... i somehow missed your post entirely lol

here is what your instructions return:
```

mason@mason-laptop:~$ sudo grub
[sudo] password for mason: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/brub/stage1
find /boot/brub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1

Error 15: File not found
grub> 
```

edit: dont know if it matters but i am on ubuntu 64 bit 8.04, upgraded from 7.10.

---

### Post by plucky on 2008-10-21
> grub> find /boot/brub/stage1



brub should be grub.You don't need to do the second command ```
find /grub/stage1
```


the "find /boot/grub/stage1" command should show you your Ubuntu and Mint root partitions.

Good Luck

---

### Post by caljohnsmith on 2008-10-21
> **plucky said:**
> You don't need to do the second command
The second find command is for the case if he set up a /boot partition, which it looks like he didn't since the command didn't return anything. :)

---

### Post by earthpigg on 2008-10-21
o right, lol... embarassing. 

anyways, ill give that a shot as soon as i get home from work and get on my box.

---

### Post by earthpigg on 2008-10-22
```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd0,1)
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
mason@mason-laptop:~$ 
```

bout to see if it worked.

---

### Post by earthpigg on 2008-10-22
worked! thanks, folks.

---

