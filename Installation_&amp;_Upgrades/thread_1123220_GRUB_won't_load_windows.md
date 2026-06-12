---
title: "GRUB won't load windows"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by techted on 2009-04-11
As I had to upgrade my primary hard disk, I finally decided to try out Ubuntu. I did a clean dual-boot install of Windows XP SP3 MCE and Ubuntu 8.10 on one drive. I installed Windows first on partition 1. Installation was Ok. Then installed Ubuntu on partition 2. Installation was Ok. 

But then when I tried to select Windows on boot, it wouldn't run. Error saying that 'Windows could not start because the following file is missing or corrupt: <Windows root>\system32\ntoskrnl.exe. Please re-install a copy of the above file.'  

Without going into too much detail over all the fixes I attempted, what worked is using a Super Grub Disk CD. With it I can select and boot into Windows but not into Ubuntu!!! (The Super GRUB problem with Ubuntu 8.10 is a documented problem) Needless to say I would rather not have to boot from a CD everytime I need to use Windows.

But this at least confirms that both OS are intact and that there must be a problem with the boot manager setup. But what is wrong with it? Any and all help would be much appreciated by this first time user.

**Partition info:**
/dev/sda1 ntfs windows XP id7 150gb
/dev/sda2 ext3 ubuntu 8.10 id83 70gb
/dev/sda3 extended id5
  /dev/sda5 linux-swap id82 2gb
/dev/sda4 ntfs my files id7 70gb

**Grub menu.lst windows entry:**
title  Windows XP Media Center Edition
rootnoverify (hd0,0)
chainloader +1
boot

What confounds me is that the menu.lst entry above is exactly what is on the Super Grub CD which works to load windows!!! But grub on the hard disk doesn't. Why??? I have tried several versions adding/deleting 'makeactive' & 'savedefault' & 'boot' to no effect.

**Windows boot.ini contents:**
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect[/FONT][/FONT]

Here I tried playing around with the values of the partition changing it to 0,2,3,4,5 to no avail.

Other things I have tried
- re-installing windows
- re-installing ubuntu 8.10 using different partition parameters (though I still maintain Windows in the primary partition)
- installing ubuntu 9.04 beta
- copying ntoskrnl.exe file from the windows CD
- disconnecting my other 3 hard disks so that only the boot drive is connected
nothing worked :(

HELP!

---

### Post by lisati on 2009-04-11
EDIT: I read the original post again. Please disregard this.

---

### Post by meierfra. on 2009-04-11
> multi(0)disk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

See what happens if you change this to

multi(0)disk(0)[COLOR="Red"]rdisk(0)[/COLOR]partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

---

### Post by techted on 2009-04-12
> **meierfra. said:**
> See what happens if you change this to

multi(0)disk(0)[COLOR="Red"]rdisk(0)[/COLOR]partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
Sorry, the boot.ini has that entry. My mistake in that I didn't type that in. I edited my post accordingly.

---

### Post by meierfra. on 2009-04-12
> the boot.ini has that entry. 

Actually that was my guess.

The "\ntoskrnl.exe. missing" message can be caused by a bug in Grub. The only cure I know, is to add Grub to the Windows boot loader:


**Step 1** Install Grub to the boot sector of the Ubuntu Partition:

Open a terminal in Ubuntu and type:

```
sudo grub
```

and at the grub prompt:

```
root (hd0,1)
setup (hd0,1)
quit

```

**Step 2 **Copy the Ubuntu boot sector to a file on your Windows partition:

```
sudo mount /dev/sda1 /mnt
sudo dd if=/dev/sda2 of=/mnt/ubuntu.bin  count=1
```
(be very careful with the "dd" command. If it runs for more than a couple of seconds press "Ctrl+C" to stop the process)

**Step 3** Edit boot.ini:

```
sudo nano /mnt/boot.ini
```

(Do not use "gedit" in place of "nano": gedit   does not  handle "dos" files very well)

Add this to the end of the file (start a new line, but do not leave a blank line):

C:\ubuntu.bin="Ubuntu"

Follow the instructions on the bottom of the screen to save the file.

**Step 4**  Install a Windows style MBR

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo lilo -A /dev/sda 1   (the last 1 is a the number 1 not the letter l)
```


Reboot and see whether you can boot into both OS's.


** Step 5 ** Edit menu.lst so that you don't have to go through two boot menus

In an Ubuntu terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Change

timeout 10

  to

 timeout 3

and

#hiddenmenu 

to 

hiddenmenu.

Save the file and you should be all set.

---

### Post by techted on 2009-04-12
Hi meierfra,

Thanks so much for the detailed intructions. I can now boot into Windows but unfortunately I have lost the option to select what OS to boot into. The computer now directly boots into Windows.

I must admit that the command line instruction bits are a bit over my head but it looks like it was successful in re-instating the Windows MBR. Since your instructions also appears to have installed GRUB into the ubuntu partition instead, I assume in order to get the GRUB menu back at bootup, my computer should boot from partition 2 instead of 1? How do I do that? If the OS were on different hard disks I imagine I could just change the boot sequence in BIOS but how do you change what partition to boot into? I thought partition1 was always the boot partition?

---

### Post by meierfra. on 2009-04-12
Something must have went wrong. At boot up, you should get  the Windows boot menu, where you can choose between XP and Ubuntu.


To figure out what went wrong, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by techted on 2009-04-12
Hey meierfra,

While trying out the numerous options on the Super Grub Disk, I ended up doing something bad that in frustration I re-installed Ubuntu again. So I gave your solution another go and this time it worked!!! Woohoo!!!!!! Thanks so much!!!

I have a some questions on your codes as I want to better understand what you made me do. Hope you don't mind. I really want to understand the process.

```
grub> setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

Is the error listed above anything to worry about?

```
sudo lilo -A /dev/sda 1
No partition table modifications are needed.
```

Does this mean that last bit of code is not necessary?

If I were to install Ubuntu again, is there a way to do things 'correctly' to get the same results without having to go through the coding you supplied? Would installing Ubuntu on partition1 and Windows on partition2 do this? Is it even possible to install Windows in a partition other than the first one?

During one of my numerous Ubuntu installs, I played around with the advanced setting during the manual partition stage and had the boot loader installed in the Ubuntu partition (parition2). I thought this would be a good idea so as not to mess with the Windows MBR but then of course during the boot process, the computer would go directly to boot Windows. Is it possible to have the computer boot from the 2nd partition?

And lastly, would your solution work if i used it on Ubuntu 9.04 using the newer ext4 format? Coz I read somewhere that GRUB doesn't work on the new ext4 - is this right?

---

### Post by techted on 2009-04-12
I thought of a another question - in the future, if I decide to upgrade my Windows version (hypothetically to Windows 7), I assume doing so would rewrite the MBR on the first partition such that I would loose the nice boot selector I now have going on.

What is the best way to get the selector back without having to re-install Ubuntu as well and going through the same process again?

---

### Post by meierfra. on 2009-04-12
> And this time it worked!!
Great.


> Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)

That's normal. It happens every time Grub is installed to a boot sector instead of the MBR.  


> ```
sudo lilo -A /dev/sda 1
No partition table modifications are needed.

```
Does this mean that last bit of code is not necessary?

That's exactly what it means.   "lilo -A /dev/sda 1" sets the boot flag to the first partition. So if the boot flag is already on the first partition, this step is unnecessary.

 > Is it possible to have the computer boot from the 2nd partition?

Yes.  Just set the boot flag to the second partition:

```
sudo lilo -A /dev/sda 2
```

and you will  boot directly into Ubuntu.

> And lastly, would your solution work if i used it on Ubuntu 9.04 using the newer ext4 format?
Yes.

> Coz I read somewhere that GRUB doesn't work on the new ext4 - is this right?

True for the regular grub. But the version of grub, which comes with Ubuntu 9.04, has been modified  to work with ext4.

> I assume doing so would rewrite the MBR on the first partition such that I would loose the nice boot selector I now have going on.


The "lilo" code you installed in the MBR does the same thing as the regular Windows MBR (namely  call the boot sector of the active partition). So upgrading to Win7  should not cause any problem.


Just curious: what happens if  you choose "Windows XP" at the grub menu (press "esc"  during the "321" countdown to get the grub menu).  Does that let you boot into XP, or do you get the "ntoskrnl.exe" error?

---

### Post by techted on 2009-04-12
> **meierfra. said:**
> Just curious: what happens if  you choose "Windows XP" at the grub menu (press "esc"  during the "321" countdown to get the grub menu).  Does that let you boot into XP, or do you get the "ntoskrnl.exe" error?

Selecting Windows XP at the grub menu now brings me back to the Windows boot selector

---

### Post by meierfra. on 2009-04-13
> Selecting Windows XP at the grub menu now brings me back to the Windows boot selector
Good.

Could you do another experiment?

Set the boot flag to the Ubuntu partition via:

```
sudo lilo -A /dev/sda 2

```

At boot up, press "esc" to bring up the grub menu.  Select XP. The Windows boot menu should appear. Select XP again. 

Does that boot you into XP?  

Next time you boot into ubuntu, just do

```
sudo lilo -A /dev/sda 1 
```

to revert to your current set up.

Thanks.
Of course you can ignore my request, I'm just trying to figure out whether there is an easier way to fix the "ntoskrnl.exe" problem

---

### Post by daniluk on 2009-07-06
**[]("http://forums.dpreview.com/forums/read.asp?forum=1009&message=32127799")**
Thanks meierfra, I followed your advice, but I have one question...

How I can change in the new boot-menu (where I have now only Windows and Ubuntu) time counting , from 30 sec to.. eg 5 ?

---

