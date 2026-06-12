---
title: "Strange Problem with grub"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by pi.theta on 2009-04-21
i have windows xp along with ubuntu 8.10 installed. Today i had a problem with the display in xp, after some troublesome amount of experimentation, i finally reinstalled it. That caused an overwrite in the mbr ( where grub was initially stored). Now grub is not getting installed anywhere nor is ubuntu getting booted.

when booting with a grub cd (which i made following instructions in the grub gnu manual), and giving the kernel parameters for booting i get the error:

Bad filename (must be absolute pathname or blocklist)

and on typing 

setup (hd0)
it also gives some block error


on command line in live cd (ubuntu 8.10) i get the following errors
oot@ubuntu:/home/ubuntu# grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/hda: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub-install /dev/hd0
/dev/hd0: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub-install /dev/sda5
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub-install /dev/sda6
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# 





thanks for any help in advance

---

### Post by ajgreeny on 2009-04-21
Using the live ubuntu CD can we see the output of sudo fdisk -l please, just to check that you have not overwritten your ubuntu install.  If it really is still there, again using the live CD follow these steps:-
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader. If not come back again for more help.

---

### Post by ronparent on 2009-04-21
To keep things as simple as possible, your action with windows had merely overwritten the mbr. All the grub files are probably intact where they originally were. They can be restore to their original state by these actions:

1 - boot from a live cd

2 - start a terminal session

3 - Type the command - grub

4 - From the grub prompt (grub >) type - find /boot/grub/stage1

5 - Also from the grub prompt using the output from the above command  type - root (hdx,y)  ##notations from prior command

6 - Now type setup (hd0)

Your grub should now be restored to the mbr and rebooting should restore the normal grub booting action.

---

### Post by pi.theta on 2009-04-21
> **ronparent said:**
> To keep things as simple as possible, your action with windows had merely overwritten the mbr. All the grub files are probably intact where they originally were. They can be restore to their original state by these actions:

1 - boot from a live cd

2 - start a terminal session

3 - Type the command - grub

4 - From the grub prompt (grub >) type - find /boot/grub/stage1

5 - Also from the grub prompt using the output from the above command  type - root (hdx,y)  ##notations from prior command

6 - Now type setup (hd0)

Your grub should now be restored to the mbr and rebooting should restore the normal grub booting action.

thanks a ton
that worked!!!

but can u explain that why the same commands were not working from the grub shell when booted from a cd.
i used exactly the same commands!!

---

### Post by pi.theta on 2009-04-21
> **ajgreeny said:**
> Using the live ubuntu CD can we see the output of sudo fdisk -l please, just to check that you have not overwritten your ubuntu install.  If it really is still there, again using the live CD follow these steps:-
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader. If not come back again for more help.

thanks a ton
that worked!!!

but can u explain that why the same commands were not working from the grub shell when booted from a cd.
i used exactly the same commands!!

---

### Post by ajgreeny on 2009-04-21
No, sorry, I have absolutely no idea why that didn't work.  I know it can work with other live CD eg Puppy linux, because I have used that in the past when a ubuntu live CD was not available, but can't help with your grub boot CD.

---

