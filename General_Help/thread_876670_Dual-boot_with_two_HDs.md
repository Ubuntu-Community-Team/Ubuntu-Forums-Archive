---
title: "Dual-boot with two HDs"
date: 2008-08-01
forum: General Help
---

### Post by NeoAndersen on 2008-08-01
Hello!!

 I have 2 HDs sata...
I firstly installed XP in the 500 GB HD...
Immediately after this I installed Ubuntu 8.04.1 amd64 in the 320 GB HD...

The PROBLEM is that the option to boot windows dont appeared in the GRUB options...

I've tried to edit the GRUB and then the XP option appeared but it haven't worked. When I choose start XP just a error message appears: NTLDR is missing...

Help please!!

---

### Post by falcon61102 on 2008-08-01
If you could, post the content of your menu.lst and that will help eveyone out in fixing you problem

---

### Post by NeoAndersen on 2008-08-01
Well...

I entered this command "sudo gedit /boot/grub/menu.lst" and that is what I've got: 

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=97ad771b-65d7-44e1-9b79-9b55fc73a5b8 ro quiet splash locale=pt_BR
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=97ad771b-65d7-44e1-9b79-9b55fc73a5b8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by falcon61102 on 2008-08-01
Under the line that says "### END DEBIAN AUTOMAGIC KERNELS LIST" there should be a couple more sections and one of them should refer to your windows install.  If you could post the remainder of that file as well as the results for:
```
sudo fdisk -l
```
-l being a lower case L

---

### Post by NeoAndersen on 2008-08-01
neoandersen@neoandersen-desktop:~$ sudo fdisk -l
[sudo] password for neoandersen: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ce53ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38161   306528201   83  Linux
/dev/sda2           38162       38913     6040440    5  Extended
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff43ff43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS
neoandersen@neoandersen-desktop:~$ sudo gedit /boot/grub/menu.lst




Nothing appears under "### END DEBIAN AUTOMAGIC KERNELS LIST".

---

### Post by TreeFinger on 2008-08-01
Add the following to menu.lst

```

title Win/XP
        rootnoverify (hd1,0)
        chainloader +1

```

Should work.

Test on floppy or usb key first though.

---

### Post by falcon61102 on 2008-08-01
Yeah, the entry that TreeFinger posted should work.  What most likely happened is that the GRUB loader did not recogize the XP installation when it set up the GRUB.  No big deal, just add it to the menu.lst like TreeFinger says and you should be good to go.

---

### Post by NeoAndersen on 2008-08-01
This time "NTLDR is missing" dont appeared.
But the GRUB dont stop to offer the choices if I dont click esc and when I select win xp the process stopped in a black screen saying "Starting up..." but after 5 min. or more nothing more happened.

---

### Post by falcon61102 on 2008-08-01
That's normal about the GRUB not stopping to show the menu.  You can edit the menu.lst in order to change that.

Try adding "makeactive" just about the chainloader+1 line and try it again.

---

### Post by NeoAndersen on 2008-08-01
I entered this way:

title Win/XP
        rootnoverify (hd1,0)
        chainloader +1
        makeactive



But nothing happen after "Starting up..."

There can't be something about the motherboard BIOS configuration?

---

### Post by falcon61102 on 2008-08-01
Oops, I made a type in my last post, about is supposed to be above.  Though I don't think it will make a difference, try it that way and if it still doesn't work then it's most likely the fact that Windows does not like being on the second drive.  For whatever reason Windows has a hard time starting up when it's not the first drive, which is why it's normally suggested to install Windows first and then Ubuntu if you are going to do a dual boot.  

There is a couple a ways to go about fixing this.  
The first thing I would try is using "map" in the GRUB.  When you boot up and get to the GRUB menu, and press "c" for command line.  You should now be at the command line, run this:
```
map (hd0) (hd1)
map (hd1) (hd0)
```
After completing those commands, press ESC to return to the menu.  Now select your windows option and see if that boots.

If that works, you may be able add the map command to your menu.lst that way you don't have to run those commands everytime you boot.  But try it manually first.

---

### Post by nacho32 on 2008-08-01
I would suggest in downloading the super grub boot loader ISO burn to disk.
A must have for multiple OS

---

### Post by NeoAndersen on 2008-08-01
I tried the map command and the "NTLDR is missing" appears again...

I will try the Super Grub Disk if it brings permanent solution but first I'd prefer keeping my fight with the GRUB... 

If there isn't permanent solution at all by these means I will consider to repartitioning the 500 GB HD splitting it in 2 parts, one for XP and other for Kubuntu, but without lost my 320 GB that I am using with Ubuntu now... But I will just do this if there is an easy way to put the 3 OS to start by the GRUB options...

I installed the XP first... I don't know why the GRUB don't detected it automatically...

---

### Post by falcon61102 on 2008-08-01
Instead of partitioning and reinstalling, you could physically change the order of the drives and update your GRUB.  That might be a little easier/faster.  You'd have to switch the Ubuntu paths from hd(0,1) to hd(1,1) and the windows XP path from hd(1,0) to hd(0,1).  Or use Super Grub disk to do it, but that should work.

---

### Post by NeoAndersen on 2008-08-01
What do you mean by physically change the order of the drives?
I must change the places where the cables are connected in the motherboard?
Or do you mean change just in the BIOS?
Forgive me for my ignorance... :confused:

---

### Post by falcon61102 on 2008-08-01
Change the cable connections on the motherboard is what I mean.  If you place the Windows XP HD as the first/primary drive and then update the GRUB, you should be fine.

---

### Post by jocko on 2008-08-02
> **NeoAndersen said:**
> I tried the map command and the "NTLDR is missing" appears again...
If you just run the map commands in a grub prompt without first telling grub where the windows boot loader is, it will look for the boot loader in the wrong drive, hence the "NTLDR is missing" error...


The problem is that Windows needs to be on the first drive (hd0).
If you try to boot xp from the second drive, grub will correctly find the NTDLR on (hd1,0), but as NTDLR tries to boot from (hd0), the windows boot loader will just wait forever... Probably without giving any error.
You can have grub re-map the drives like this:
```
title Win/XP
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```This means grub will first understand that the boot loader (NTLDR) is on (hd1,0), then it will swap the drives around so that (hd1) becomes (hd0) and the other way around (the way windows needs it to be), then it will load the windows boot loader (from the drive that is now called (hd0)).
You could probably also put the map commands before the "rootnoverify" command, but then you would have to change to (hd0,0)...

[Here's an excellent page]("http://users.bigpond.net.au/hermanzone/p15.htm") with everything you would ever need to do with grub.

---

### Post by steefjeqv on 2008-08-02
Hi,

Have you tried changing the boot disk priority in your BIOS setup ?

This may give you back your XP, but your GRUB bootloader may not appear anymore.

Greetings,
Steven

---

### Post by jocko on 2008-08-02
> **falcon61102 said:**
> Change the cable connections on the motherboard is what I mean.  If you place the Windows XP HD as the first/primary drive and then update the GRUB, you should be fine.

> **steefjeqv said:**
> Hi,

Have you tried changing the boot disk priority in your BIOS setup ?

This may give you back your XP, but your GRUB bootloader may not appear anymore.

Greetings,
Steven

Swapping the physical connections is not necessary. The drive that is set to boot in bios will by default become (hd0).
But there's no need for changing the boot order and reinstalling grub. Just try the lines from my post above.
They will tell grub to virtually swap the drives only when you boot windows. This also means that the original mbr will still be intact on the windows drive, so if you by some reason would like to completely remove ubuntu and grub from the other drive, or the drive dies, you would still be able to boot windows (after you change the boot order in bios...).

---

### Post by NeoAndersen on 2008-08-02
I made the re-map as you said but still Starting up... and "NTLDR is missing"...

I am studying a book about Ubuntu. I just begin the chapter about the BASH Shell... So unfortunately I don't have time to study about GRUB now... I want be free from Windows... I just need XP to record me playing guitar in a home studio using a M-Audio Fast Track Pro hardware with the Pro Tools software... and I like to host a kind of karaoke in Skypecasts... But in the near future I want to find replacements for these programs in Linux...

My first experience with Ubuntu was about 6 months ago. I have a similar problem that was solved by a friend. In the BIOS there is a kind of "Hard Disk Write Protected" enabled by default. Then my friend, after try a lot of things, just disabled it, so I could start both XP and Ubuntu... But now this option remains disabled...

I saw there a "Configure SATA as (IDE)"... I could change it for 2 other options but as I don't know what that means I let it the way it is...

---

### Post by NeoAndersen on 2008-09-05
Hello!!

I began from the beginning...

 I have 2 HDs, first 500GB, second 320GB.
I've installed XP in the first one in about 120GB. Now I want to install Ubuntu in the 380GB of the fist HD and Kubuntu in the 320HD or vice-versa if that is better.

I don't want lost XP again as it happens 2 months ago... I need it while I don't learn to use a homestudio software in Ubuntu...

What your advice is?

---

### Post by falcon61102 on 2008-09-05
With the setup you have now, Ubuntu should be an easy install going in directly behind XP.  To help you through the install process, I recommend that you take a look at this page before you get started:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Just take your time and double check your work.  I've always found it's much quicker to double check something than to have to go back and redo it.

---

