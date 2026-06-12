---
title: "replace Express Gate with UNR on alternate power button"
date: 2010-02-18
forum: Hardware
---

### Post by Hansmc on 2010-02-18
I have an Asus 1005pe, and it has two power buttons. One is like a normal power on button and the other starts up a little fast operating system called Express Gate. It is based on splashtop (see splashtop.com). And that intern is based on linux. I would like to make it, so the Express Gate power button would load right into a full version of Ubuntu Netbook Remix. The normal power button would then be made to load windows. Does any one know how this could be done? Thanks.

---

### Post by linuxuser21 on 2010-02-19
I too would like to know this.  I have the Asus G71GX and it also has two power buttons to start the different OSs.  Is it possible to install Ubuntu in place of Express Gate?

---

### Post by djuhas on 2010-02-20
same problem. i have asus ul50 and it runs a second os (express gate) - is there any way to modife the same button to work with ubuntu?

---

### Post by linuxuser21 on 2010-02-25
Bump

---

### Post by linuxuser21 on 2010-03-03
Bump.

---

### Post by Zaf9670 on 2010-03-17
I would also like to know more about this if anything comes about. I have searched for this before and saw where people were looking at the source code to see if it could be done.

If any news comes about let me know. I have an ASUS G51vx (similar to the G71 just smaller) so I also would like to replace it.

If I find anything I will try to come back here and share.

---

### Post by Zachzor on 2010-04-04
I'd love to know the answer to this question too. I don't use the Express Gate feature, and I'd love to remap it to boot an new operating system.

---

### Post by essexboyracer on 2010-04-25
I posted the same question on the Asus Forum, [http://vip.asus.com/forum/view.aspx?id=20081220024905627&board_id=3&model=G71V&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20081220024905627&board_id=3&model=G71V&page=1&SLanguage=en-us)

Essentially the Expressgate gets installed into the BIOS as a small image.

Still dont know how to mess with it though. For any G71 owners out there, you can change the OLED display above the keyboard to show system performance info etc.

I would also like to know how to switch off the external case lighting on my G71v?

---

### Post by HoMie_G on 2010-05-11
i have been trying to figure this out too. i would love to install ubuntu light instead of express gate. if i ever figure it out i will post back here.

---

### Post by welshmike on 2010-05-12
Maybe people could think about dual boot XP/W7 and Ubuntu and forget about the Express Gate boot button?

---

### Post by samsonite801 on 2010-05-20
> **welshmike said:**
> Maybe people could think about dual boot XP/W7 and Ubuntu and forget about the Express Gate boot button?

I think what these people are after is to remap the command of that left-hand power button so they could in-effect, have a one-button-press solution to enter Ubuntu, or a different button-press to directly enter Windows. Also the coolness factor of this is way higher than the Express Gate because Express Gate is about worthless and it is paining to know that the hardware of this awesome machine is so uselessly utilized into this configuration where the button does this totally pointless function. 

If the command that runs right after initial powerup (on pushing the left power button) in the BIOS could somehow be remapped to load a GRUB bootloader while the right power button would just initiate the standard MBR which would load the M$ bootloader (BCD) then this might be how to make this possible. My big brother used to know how to hack into BIOS images and manipulate them. He's a very busy programmer now so getting his time is hard but I should ask him if he thinks this task is feasible, and even if he might even know where one would start at trying to figure out how to make it possible. My feeling is that if this mapping is done in the BIOS image that this might be possible to change with an altered BIOS image but if the mapping to a command is done using some other protocol or done on the hardware level, then it might be impossible to remap it. If one even knew what the command was that gets initiated, you might be able to make that command instead load a second alternate MBR type file which would load a GRUB bootloader. Because if you had a GRUB bootloader that had Ubuntu set up as the default OS set to load in 1 second, and then you still had the standard MBR which loaded the M$ (BCD) bootloader and Windows 7 would be the default OS on there set to load in 1 second, then this would be ideal. 

From what I understand, Express Gate is just an image file on the hard drive and some command possibly starting from the BIOS invokes this image to be loaded and ran. People have manipulated this Express Gate image file (in other forums) as well to change functionality of the Express Gate OS, so this might be a potential place to re-direct in the begininng before it executes the running of whatever script or code loads Express Gate,  and instead run a command to load GRUB from. Need more research.

I DO believe this would be super cool to engineer this function into my new 1005PR, but the question would be is itworth the time to figure out HOW to do it? I see a lot of people here asking for the same thing (ie they want their pizza delivered in 30 mins or less), but how many of these people asking are willing to pitch in and help do the research because I too am busy and I do not have gobs of surplus time to figure this out all on my own. If everybody does research and Googles a lot with me we might have a chance at figuring this out. Perhaps as a far-fetched last resort if we could find some contact at ASUS who could even offer some insight as to this issue.
.
.

---

### Post by Hansmc on 2010-05-22
A few things I found:

On my Asus 1005pe express gate is in the windows partition in a directory called ASUS.SYS. In there there is a bunch of *.sqx files that can be uncompressed with unsquachfs command.

I looked around to try and find something like a boot loader that could be edited, but have not got very far. 

I have a feeling this will not help much but it is the only thing I can figure out. One option would be if we could put a command in there some place that would make express gate boot into a full Linux os on another partition after it has partly or fully booted itself.

Any ideas?

Thank-you.

---

### Post by ElTimo on 2010-11-11
Sorry to resurrect an old thread, but I had a thought. Maybe there's some way to manipulate the *.sqx files to contain an installation of Ubuntu. That would make messing around with BIOS images and the bootloader unnecessary, right?

---

### Post by kalos on 2011-01-27
Phoronix forums has info on hacking the ExpressGate install (to change apps and fix resolution). 

[http://phoronix.com/forums/showthread.php?11610-Hacking-Express-gate-(Asus-Splashtop)](http://phoronix.com/forums/showthread.php?11610-Hacking-Express-gate-(Asus-Splashtop))

---

### Post by Percius on 2011-02-14
I read through ALL 25 pages trying to figure out how to load another Linux distro via the express boot. There was some interest burred within plenty of other comments. 

1st. Darkstar2000 on 5-11-2009 @11:58AM claimed you could launch ubuntu with a command such as this...
```
kexec --load /mnt/dvmdrive_root/linux/vmlinuz --append="root=UUID=XXX ro vga=791 pci=nobios pnpbios=off" --initrd "/mnt/dvmdrive_root/linux/initrd.img --console-vga
kexec -e
```
He notes that you still have to create an icon with that as the command and you still have to click the icon....

Someone else noted that it uses Bootsplash... As this is a linux graphical linux boot loader one would presume this could be modified.

Note: There are 2 different kinds of Express Gate installs out there... Some use space on the hard drive while others have a dedicated solid state for them. It seems some solidstates are read only and others are readwrite... I am dealing with the harddrive variety...

---

### Post by Percius on 2011-02-16
I do not know how to make Asus ExpressGate (splashtop) load any os, however ASUS ExpressGate Cloud (VideACE) uses Grub (legacy). It has a standard menu.lst file... From that file it is easy enough to chainload grub2.

I tried loading my kernel directly however the build of grub does not seem to have ext4 support and seemed to ignore stage 1.5 files... I am sure this could be fixed, but having a standard grub that is auto updated when kernels get updated seemed to make sense to me.

---

### Post by Swindlerz on 2011-03-29
hehe im here to join in, i got the ul30a and of course i got this button that gives me xpressgate, if only i can change it to boot something else up... hmmm

---

### Post by stevenswall on 2011-05-12
Definitely interested... I have the UL80Ag, with the HDD version of ExpressGate (Splashtop) This laptop is nearing the end of it's cycle though, so I'm not sure much will come of the second power button.

---

### Post by Nohajc on 2011-05-26
> **Percius said:**
> I do not know how to make Asus ExpressGate (splashtop) load any os, however ASUS ExpressGate Cloud (VideACE) uses Grub (legacy). It has a standard menu.lst file... From that file it is easy enough to chainload grub2.

I tried loading my kernel directly however the build of grub does not seem to have ext4 support and seemed to ignore stage 1.5 files... I am sure this could be fixed, but having a standard grub that is auto updated when kernels get updated seemed to make sense to me.

OK, I may have a solution for booting another distro with *ASUS ExpressGate Cloud*.
But, as I haven't got any real ASUS box (at least not yet, I am planning to buy eee soon), I was testing the boot process only in VirtualBox (quite surprising that I could actually install ExpressGate from a Windows XP virtual machine - and it worked). 

After experimenting with menu.lst located in **C:\ExpressGate** I realized that this particular version of Grub is somewhat crippled to say the least. And it's probably on purpose. It seems that it lacks any support of ext file system completely.
As soon as you try to change root to an ext partition it just gets stuck. However, it can start loading any kernel and initrd image present in the same (Windows) partition. That is until you try to set the root to a linux partition - in that case, you end up with kernel panic. In one word: this Grub is completely useless. :-k

To "boot up our way from this mess" we need a better bootloader. So, I figured why not use **Grub4dos**. To make it clear, I wasn't trying to replace current Grub (maybe it could be done, but I'm not that capable hacker). I chose a simpler way.

[SIZE=3]**This is what you should do:**[/SIZE]

**1.** **Download Grub4dos from sourceforge** ([http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/))

**2. Install your preferred linux distro** (Ubuntu Natty in this example) 
When you'll be setting up bootloader, **and this is important**, you should probably install it to the partition (e.g. /dev/sda3) not to MBR (we don't want to compromise Asus' way of booting) Also, we must not delete Windows partition, of course.

This is how the partition table could look like at the end:
```
/dev/sda1 [BOOT] NTFS - Windows loader
/dev/sda2        NTFS - Windows root (C:\)
/dev/sda3        ext4  - Ubuntu root (/)
/dev/sda5        swap
```(and Ubuntu's Grub2 goes to /dev/sda3)

**3. Edit menu.lst** [B]and prepare Grub4dos
[/B]The original C:\ExpressGate\menu.lst looks like this:
```
default saved
timeout 0
hiddenmenu

title minik
  kernel /ExpressGate/vace ro no_win_installer=0 pci=nocrs i8042.reset quiet video=intelfb acpi_backlight=vendor acpi_display_output=vendor vaKBD=us VALANG=en_US fastreboot=no acpi_osi=Linux av_flag=1 rw_flag=1 debug_log=1 nwm=1
  initrd /ExpressGate/vace-id
title Win_1 
  savedefault 0    
  rootnoverify (hd0,0)
  chainloader +1
title Win_2
  savedefault 0
  rootnoverify (hd0,1)
  chainloader +1
title Win_3
  savedefault 0
  rootnoverify (hd0,2)
  chainloader +1
title Win_4
  savedefault 0
  rootnoverify (hd0,3)
  chainloader +1
```Now, we'll just edit the first entry:
```
...
title minik
  **kernel /grub.exe**
title Win_1 
  savedefault 0    
...

```For this to work we'll need to copy **grub.exe** and **grldr** from grub4dos archive to C:\
and then we create second **menu.lst** file also in C:\ (it will be used for accessing our ext partition and loading Grub2)

It can look something like this:
```
timeout 0
default 0
hiddenmenu

title Ubuntu 11.04
root (hd0,2)
kernel /boot/grub/core.img
```From Grub4dos you could of course load Ubuntu kernel directly but this way you won't have to change anything manually after a kernel update (just let Grub2 take care of it).

**4. Reboot the system and see what happens**

OK, now I just wait for you to try it and confirm whether it works.
[COLOR=Red]**[SIZE=3]EDIT: Yes, it works just fine. [/SIZE]**[/COLOR]

Unfortunately, owners of the older versions of ExpressGate cannot use this method because it is based on Splashtop and I've no idea how it boots... but maybe someone will figure it out eventually.

---

### Post by Nohajc on 2011-06-17
No one interested?

---

### Post by Hansmc on 2011-06-18
> **Nohajc said:**
> No one interested?

I am interested. I was think I would have time to try it out on my Asus Eee some time soon but have not done so yet. I was wondering if I could just make the C:\ExpressGate\menu.lst load the windows operating system on the c: drive. That way I would not have to use grub4dos. Then the other power button would just keep on loading the grub from the mbr, and I could turn off the prompt and have that grub just load Ubuntu.

---

### Post by Nohajc on 2011-06-18
You mean you would switch the buttons? 
EG button -> Windows
Power button -> Ubuntu

Clever, I haven't thought of that...
I'll try to test it in VirtualBox and see what happens.

---

### Post by Nohajc on 2011-06-18
Ok well, in VirtualBox it just freezes like everything else except grub4dos...
I tried
```
title minik
   rootnoverify (hd0)
   chainloader +1
```But that doesn't necessarily mean it couldn't work on the real hardware.
You'll have to try for yourself.

---

### Post by levrin on 2011-06-21
I'm not running Ubuntu on my 1215B, but I have successfully gotten grub4dos to chainload grub on Mageia installed on an SD card in the built-in cardreader when using the Express Gate button. I should probably switch to a distro with proper UEFI support, so I can see what efibootmgr tells me about the system.

---

### Post by Nohajc on 2011-06-28
Yes, you're right. Using grub4dos it works. I just got my 1215B yesterday and have successfully managed to chainload arch linux.

Just a note: Express Gate came installed in a hidden fat32 partition (no C:\Express Gate on the windows boot partition) but the rest remains the same.

---

### Post by gcorreai on 2011-07-05
I have a UL30Vt and it came with the Splashtop based Express Gate. It seems I'm not able to install Express Gate Cloud on my laptop, or that I'm not using the correct installer. Anyway, I've been tinkering with my installation (which is in a hidden partition called RECOVERY) to, at least, being able to change the screen resolution, which by default doesn't match the native one for my screen. I have failed every time.

Can you help me in any way? I've been trying to replace Express Gate with ChromiumOS (even if it seems to not support my wifi card at the moment), and have read possibly everything there is on the internet on this topic in the past week. This post seems as the biggest achievement, so congratulations on that.

I apologise for my english. I am really frustrated with this thing, so please help me!

---

### Post by levrin on 2011-07-25
So since I've got chainloading working on my 1215B, I'm trying to figure out just how much of the rest of the gig-and-a-half of stuff in the ExpressGate folder can be deleted. Near as I can tell, for booting it just looks for /ExpressGate/stage2 on any ntfs partition, so how much do I really need to keep in there besides that and menu.lst?

Edit: Turns out I don't need any of it besides stage2 and menu.lst, so I moved those and grub4dos onto the main windows partition and deleted the hidden recovery partition it used to be on. Still chainloads correctly.

---

### Post by Nohajc on 2011-07-26
**levrin:** Thank you for this information. I was curious about this myself but so far have been too lazy to actually do the research. :D

Anyway, what was driving me crazy about the boot was that there seemed to be an unnecessary step when grub4dos was loading its built-in default menu for about 1 second before redirecting to the linux partition. I just didn't like to see it there every time.

So, I eventually figured out a way to get rid of it completely by patching grub.exe and effectively inserting my own menu.lst in it which by the way eliminates the need of an external menu.lst file.

Yes, the default menu is built into the binary itself but can be replaced by other plain text boot entries without any problem.

This is a script I wrote for the task (it will probably work only with grub4dos version 0.4.4 since the absolute offsets may be different in other versions):
```
#!/bin/bash

g=grub.exe # grub
og=grub.exe.bak # grub backup
mn=menu.lst # menu file to embed

mv $g $og
dd if=$og ibs=1 count=230018 > $g
cat $mn >> $g
dd if=$og ibs=1 skip=230567 >> $g
```Now it looks nice! :)

**gcorreai:** I'm sorry, I wish I could help but the problem is that no one actually understands how Splashtop boots so far. I can't even test it in virtual environment, it just won't work, so the chances I can crack this are very slim...
However, earlier in this thread there are links to the phoronix forum where they're hacking Splashtop and some of the darkstar2000's posts about *kexec booting* look promising. 
It wouldn't be the cleanest solution since you would be loading your distro from an already running Splashtop but it is possible according to him. It's just that there is no simple step-by-step howto so you'll have to study more on the subject if you want to understand it.

---

### Post by gcorreai on 2011-08-03
ok, thanks a lot! I've already read the phoronix forum posts but it was not what I was looking for. Replacing Spalshtop with EGC would have been a good solution, but it won't install on my UL30Vt.

Anyway, thanks for the help.

---

### Post by liuyanghejerry on 2011-08-07
Well, the grub4dos method not worked for my Asus N50S. I didn't use the combination file, but only put grub.exe, grldr and a menu.lst at C:/, write a new menu.lst into the hidden partition.

Sadly, when booting, the screen only has a cursor at the left top. Nothing happens after.

I'm not sure why but maybe because my Ubuntu is at a usb2.0 hard drive. Any suggestions, please?

Thanks, anyway.

EDIT: I've got everything fine. I wrote the root wrong in the original menu.lst to the hidden partition. Now I can 2nd init to my ubuntu. Than you very much.

---

### Post by iSpitFire on 2011-08-12
> **Nohajc said:**
> OK, I may have a solution for booting another distro with *ASUS ExpressGate Cloud*.
But, as I haven't got any real ASUS box (at least not yet, I am planning to buy eee soon), I was testing the boot process only in VirtualBox (quite surprising that I could actually install ExpressGate from a Windows XP virtual machine - and it worked). 
 
After experimenting with menu.lst located in **C:\ExpressGate** I realized that this particular version of Grub is somewhat crippled to say the least. And it's probably on purpose. It seems that it lacks any support of ext file system completely.
As soon as you try to change root to an ext partition it just gets stuck. However, it can start loading any kernel and initrd image present in the same (Windows) partition. That is until you try to set the root to a linux partition - in that case, you end up with kernel panic. In one word: this Grub is completely useless. :-k
 
To "boot up our way from this mess" we need a better bootloader. So, I figured why not use **Grub4dos**. To make it clear, I wasn't trying to replace current Grub (maybe it could be done, but I'm not that capable hacker). I chose a simpler way.
 
[SIZE=3]**This is what you should do:**[/SIZE]
[COLOR=red](I'll need someone to test this on actual Asus box to determine if it is in fact possible)[/COLOR]
 
**1.** **Download Grub4dos from sourceforge** ([http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/))
 
**2. Install your preferred linux distro** (Ubuntu Natty in this example) 
When you'll be setting up bootloader, **and this is important**, you should probably install it to the partition (e.g. /dev/sda3) not to MBR (we don't want to compromise Asus' way of booting) Also, we must not delete Windows partition, of course.
 
This is how the partition table could look like at the end:
```
/dev/sda1 [BOOT] NTFS - Windows loader
/dev/sda2        NTFS - Windows root (C:\)
/dev/sda3        ext4  - Ubuntu root (/)
/dev/sda5        swap
```
(and Ubuntu's Grub2 goes to /dev/sda3)
 
**3. Edit menu.lst** **and prepare Grub4dos**
The original C:\ExpressGate\menu.lst looks like this:
```
default saved
timeout 0
hiddenmenu
 
title minik
  kernel /ExpressGate/vace ro no_win_installer=0 pci=nocrs i8042.reset quiet video=intelfb acpi_backlight=vendor acpi_display_output=vendor vaKBD=us VALANG=en_US fastreboot=no acpi_osi=Linux av_flag=1 rw_flag=1 debug_log=1 nwm=1
  initrd /ExpressGate/vace-id
title Win_1 
  savedefault 0    
  rootnoverify (hd0,0)
  chainloader +1
title Win_2
  savedefault 0
  rootnoverify (hd0,1)
  chainloader +1
title Win_3
  savedefault 0
  rootnoverify (hd0,2)
  chainloader +1
title Win_4
  savedefault 0
  rootnoverify (hd0,3)
  chainloader +1
```
 
Now, we'll just edit the first entry:
```
...
title minik
  **kernel /grub.exe**
title Win_1 
  savedefault 0    
...

```For this to work we'll need to copy **grub.exe** and **grldr** from grub4dos archive to C:\
and the we create second **menu.lst** file also in C:\ (it will be used for accessing our ext partition and loading Grub2)
 
It can look something like this:
```
timeout 0
default 0
hiddenmenu
 
title Ubuntu 11.04
root (hd0,2)
kernel /boot/grub/core.img
```
 
From Grub4dos you could of course load Ubuntu kernel directly but this way you won't have to change anything manually after a kernel update (just let Grub2 take care of it).
 
**4. Reboot the system and see what happens**
 
[COLOR=red]**[SIZE=3]I repeat that this is not a verified solution! It is only a theory proven to work in VirtualBox but no physical environment yet. So, try this at home only if you actually know what you're doing.[/SIZE]**[/COLOR]
 
OK, now I just wait for you to try it and confirm whether it works.
Unfortunately, owners of the older versions of ExpressGate cannot use this method because it is based on Splashtop and I've no idea how it boots... but maybe someone will figure it out eventually.
 
 
I'm willing to try this on an ASUS N53SV which has ExpressGateCloud installed.
 
One question. After modding the original menu.lst in C:\ExpressGate, I need to copy the new grub.exe (4DOS) and it's menu.lst directly to C:\ root? 
Also, before doing all this, I need to install Ubuntu. But it should work in the same way with any distribution of Linux? Not just Ubuntu, right?

---

### Post by Nohajc on 2011-08-12
Yes and yes. It will work with any operating system you can boot from grub. That includes even various versions of Windows.
Regarding menu.lst: First stays in EG directory, second goes to root, just as you said. You can either copy the grub's default menu and edit it or write one from scratch. That's probably cleaner. 

Anyway, as I pointed out in my later post, the grub4dos' menu can be incorporated into the grub.exe itself (see the patch script) so you end up with just one separate menu.lst in EG directory after all.

---

### Post by HuRRaCaNe on 2011-08-15
Now, I haven't used linux an aweful lot (though, I will soon)

Knowing that you need to install the linux distro first, wouldn't you have the grub bootloader when booting up windows (with the normal power button)? Or could you just remove that, after you've set up the grub4dos (using fdisk /mbr in said windows installation)

Also, would reïnstalling windows not mess up the connection between expressgate and the already installed windows? Or can you install express gate on top of that windows installation? (implying your computer had express gate in the first place)

---

### Post by bakape on 2011-08-15
> **HuRRaCaNe said:**
> Now, I haven't used linux an aweful lot (though, I will soon)

Knowing that you need to install the linux distro first, wouldn't you have the grub bootloader when booting up windows (with the normal power button)? Or could you just remove that, after you've set up the grub4dos (using fdisk /mbr in said windows installation)

Also, would reïnstalling windows not mess up the connection between expressgate and the already installed windows? Or can you install express gate on top of that windows installation? (implying your computer had express gate in the first place)

Honestly I wouldn't recommend this option to choose between Windows/Linux. Setting it up for Chromium OS and such is tempting (and I was very interested in it myself until I discovered how much it supported my hardware). Personally I found a regular grub2 installation coupled with a bit of extra functionality from the grub-customizer package much more usable. The biggest perk being the ability to boot the last selected OS, giving you persistent restarts. :)

Though tweaking for the sake of tweaking is something I can relate to easily after breaking my installation so many times. :P

Also to answer the second question, you can download the installer from Asus to do just that.

---

### Post by HuRRaCaNe on 2011-08-15
> **bakape said:**
> Honestly I wouldn't recommend this option to choose between Windows/Linux. Setting it up for Chromium OS and such is tempting (and I was very interested in it myself until I discovered how much it supported my hardware). Personally I found a regular grub2 installation coupled with a bit of extra functionality from the grub-customizer package much more usable. The biggest perk being the ability to boot the last selected OS, giving you persistent restarts. :)

Though tweaking for the sake of tweaking is something I can relate to easily after breaking my installation so many times. :P

Also to answer the second question, you can download the installer from Asus to do just that.

I don't see why I wouldn't use the second button, which will be completely useless otherwise, to boot into linux. Windows will definitely be my primary OS (I'm sorry :() but I will definitely have to use linux either way. So having a dedicated button for linux is such a nice extra, is it not? Instead of having to deal with grub to select either windows or linux, you can just press this button here or the other one there.

I don't see why having one button with grub is more convenient. Well I guess it's a personal preference :-)

---

### Post by bakape on 2011-08-15
> **HuRRaCaNe said:**
> I don't see why I wouldn't use the second button, which will be completely useless otherwise, to boot into linux. Windows will definitely be my primary OS (I'm sorry :() but I will definitely have to use linux either way. So having a dedicated button for linux is such a nice extra, is it not? Instead of having to deal with grub to select either windows or linux, you can just press this button here or the other one there.

I don't see why having one button with grub is more convenient. Well I guess it's a personal preference :-)

Well, yes it is. Perhaps I scheduled a restart too many times and went on to brew a cup of tea, just to come back and have the wrong login screen staring at me. But if you are sticking to Windows most of the time, that is a completely different situation, and the Linux button is that much more convenient. Sigh, if only there was a way to "talk to grub" and schedule you next boot choice from within Win/Lin. :(

---

### Post by HuRRaCaNe on 2011-08-15
> **bakape said:**
> Sigh, if only there was a way to "talk to grub" and schedule you next boot choice from within Win/Lin. :(

Not even that, it should know all by itself. Mind reading, telepathy, whatever.


Technology!

---

### Post by bakape on 2011-08-15
> **HuRRaCaNe said:**
> Not even that, it should know all by itself. Mind reading, telepathy, whatever.


Technology!

Yup!

But on a serious note, date/time, wifi network recognition or even dare I say geopositioning shouldn't be that hard to implement, if we could just "talk to grub". Not that I'm a developer, so I have no idea if that is even possible. 

So off topic...

---

### Post by Nohajc on 2011-08-19
Actually, you can talk to grub. There's the "grub-set-default" script which you can invoke before reboot. 

I'm using it in combination with EG button because I couldn't reboot back to linux without it. 
This way, I need one additional grub installation in mbr but it works without breaking the Windows boot or the EG button functionality.

---

### Post by Try Again on 2011-08-21
Hi. I found a way to boot whatever OS you want using the Splashtop button, using the CEFULL file to hijack the boot process and execute your own boot code. A Splashtop OS installation is not necessary to achieve this, eliminating the need for Windows. It's my first true program in assembly, I didn't try to optimize my code and everything is pretty much hard-coded (suggestions are welcome). However, it's been a good exercise to practice switching between protected mode and real mode. :)

The tarball, containing source and binaries : [stboot-0.1.tar.gz]("http://trya.alwaysdata.net/stboot/stboot-0.1.tar.gz")

Documentation and instructions can be found in the README.

Testers needed!

---

### Post by gcorreai on 2011-08-25
Try Again

I will try your program as soon as I get a few spare hours and report back my experience! Probably I'll use it to boot Chromium OS or maybe Ubuntu on my ASUS UL30Vt. Who knows.

---

### Post by Nohajc on 2011-08-26
> **Try Again said:**
> Hi. I found a way to boot whatever OS you want using the Splashtop button, using the CEFULL file to hijack the boot process and execute your own boot code. A Splashtop OS installation is not necessary to achieve this, eliminating the need for Windows. It's my first true program in assembly, I didn't try to optimize my code and everything is pretty much hard-coded (suggestions are welcome). However, it's been a good exercise to practice switching between protected mode and real mode. :)

The tarball, containing source and binaries : [stboot-0.1.tar.gz]("http://trya.alwaysdata.net/stboot/stboot-0.1.tar.gz")

Documentation and instructions can be found in the README.

Testers needed!
Man, you're awesome! This is precisely the reason why I want to become a real programmer. :D To have the absolute control over what my machine does. :)
I myself won't be able to test it for you but fingers crossed. This looks like the real thing.

---

### Post by Try Again on 2011-08-26
I'm eager to get feedback! :popcorn:

I've made a new tarball, it's mainly a code clean-up, but copy operations should be a little faster : [stboot-0.1.1.tar.gz]("http://trya.alwaysdata.net/stboot/stboot-0.1.1.tar.gz")

With a lightweight installation (including readahead and systemd) and a 5400rpm HDD, I manage to get from POST to Chromium in about 30 seconds, POST and GRUB4DOS taking about 7 seconds before loading the kernel, so there's still much room for improvement. I'm now looking for a lighter alternative to GRUB4DOS. SYSLINUX would get my preference, but even more stripped-down bootloaders exist.

---

### Post by Nohajc on 2011-08-26
OK, even without a Splashtop hardware I couldn't resist, so I attached the CE_BZ header to your program and tried in VirtualBox. It works right but the runtime is about 5 seconds (from grub to grub :D). I haven't tried your update though.
Anyway, you've done a great job. I only wish I could understand this stuff but assembler is still a wizardry to me. :D

---

### Post by gcorreai on 2011-08-27
OK, so I installed ubuntu 11.04 on a partition on my hdd and used your program to chainload grub2. It was a bit tricky, but it worked at last!

Works like a charm, except it's taking a long time to boot. I'll tinker a bit with grub2 config, but the step from boot to grub4dos it's not that bad actually.

Thanks a lot man! You just made my splashtop button useful!

Maybe I'll install chromium os to get an "instant-on" OS (my original idea) this week.

---

### Post by welshmike on 2011-08-27
Probably academic but does it make any difference in boot time between which power button is used to boot a system?
e.g. if both power buttons booted the same system.

Edit: Currently my alternate button boots Express Gate and the normal button boots to Grub for selection of Ubuntu or XP.

---

### Post by Try Again on 2011-08-27
> **welshmike said:**
> Probably academic but does it make any difference in boot time between which power button is used to boot a system?
e.g. if both power buttons booted the same system.
Technically, the boot procedure is the same from the one involving the normal power button (copy a bootloader at 0x7c00, load a kernel, boot), there's no magic in it. But the entire purpose of the Splashtop button is to have a non-interactive way of booting an OS. So, theoretically, you're saving time from not having to choose, but it's not that obvious at the moment : GRUB4DOS does partition probing in the order specified by the partition table, so if your stboot partition is not the first one, it might take some time... That's why I'm looking for a lightweight alternative or another boot method (for example, by reading boot sectors with stboot).

But, sincerely, there's no point in booting your regular OS with the additional button, except for rescue purposes. With two power buttons, your PC is not tied to only one bootloader anymore, thus you are free to find a specific purpose for one button or the other.

---

### Post by welshmike on 2011-08-27
OK no magic just some hard graft research and coding to make use of one button to boot one opsys and the other to boot another opsys.

---

### Post by HuRRaCaNe on 2011-09-09
Right, so I have my laptop - installed expressgate (cloud) - no menu.lst file. What now? :confused:

EDIT: Actually, the C:\ExpressGateUtil folder is only 17mb, where is the rest?

---

### Post by Nohajc on 2011-09-09
**HuRRaCaNe:** Well, unless they've come up with a new type of EG, it should certainly be there. Have you tried to look for it on a hidden partition? 
(First, unhide it using gparted, for instance.)

---

### Post by HuRRaCaNe on 2011-09-09
Oh you silly asus with your silly tactics. Used paragon partition manager to unhide the recovery partition, and assign a drive letter so it can be accessed via windows.

Will try booting into linux mint soon :D

EDIT: Uh, little update. Apparently linux mint installed grub (before, probably) the MBR, which is not what i want. Will restore the MBR first, then restore grub like this:


1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> fdisk -l (Mine is /dev/hda6)
5. Mount the root partition of Ubuntu -> mount -t ext3 /dev/hda4  /mnt/ubuntu (replace /dev/hda4 by your Ubuntu partition determined at  the step 4)
6. Chroot the mounted partition -> chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> grub-install /dev/hda (tis is where i change it to 'hda6', where my linux is installed
8. Exit the shell
9. Reboot


Would this be the correct way of doing things?

EDIT2: I'm not quite sure how I would install grub to the linux partition without compromising the MBR.
EDIT3: Oh my, installed xubuntu because it's sexier and now i've discovered the 'install bootloader to this other thing'- option. I think i maybe getting close now.
EDIT4: There we go, got it working. Thanks!

---

### Post by Hirs on 2011-10-29
Thanks to the stboot (thank you for that!) I'm able to load grub4dos (using asus ul30a), now I'm trying to load chromeos vanilla from the image file. This are my config lines:

title Boot Disk Image 
map --mem (hd0,0)/ChromeOS-Vanilla-1232.0.2011_10_27_1640-ra72180fc.img (hd1) 
map --hook
root (hd1) 
chainloader (hd1)+1 
rootnoverify (hd1) 

But I end up with error 63

I know I could install chromeos, but it needs two partitions, and I already have a lot and space is limited :)

---

### Post by infowars on 2011-12-26
Getting a 1215P with EG in a few days... trying to find ways to TWEAK duh EG/W7.

You all rock.... with this work to IMPROVE the EG thing...

I'll Macrium Reflect Free n copy C: drive as a bkup to stick. 
Also unhide EG partition with EPM free and than copy that partition to USB with Macrium Bkup.
THAN
Partition the big partition into Logical partitions. than and wipe C: with LiveMint CD. 
Reinstall W7  on C: without SP1, with Macrium Restore and than install MINT 11 with Grub2 on Mint "/" partition. 

Reboot to W7 and EasyBCD the MBR to add Mint to boot on that side.

And if all works with my new 1215P than do more Coping C: and Mint Backup those partitions again for another BKUP....

Than may re-install EG to W7..... see if EasyBCD can adjust that situation so I have a TRI boot to choose whatever.

Since I have "terminal fear" I'd try all this great programing, but for the n@@b in me.... I'll just watch and learn.

Ya can call that n@@b stew. LOL

Great Board. THX

---

### Post by arunpatal on 2012-01-01
Hi, it would be great help if someone can explain how to use express gate cloud button to boot ubuntu step by step.
and of course it would be fantastic if someone can make a video.
Please try to use as simple language as possible. 
I have 1015PN netbook.
Thanks  :)

---

### Post by King_Richard on 2012-01-13
I have an Asus G50Vt-A1 and will try this metod (stboot) as soon as i get my new internal HDD ;-) and some time to sink in this project.
If all goes well will be assigning it to Android-x86 and then will have a full lightweight OS instead of the ExpressGate (too many OS installed actually on my laptop). Just one question: to use this metod is necessary the bootloader of the OS? Or can we just assign it to the partition of it? Asking that because i already have 4 bootloaders on system (Chameleon, Grub 2, Grub and Windows bootloader) and wondering how to manage all of them with that.

The idea of an instructive video is quite interesting, would help many people.

---

### Post by Asxetos on 2012-05-30
@[Try Again]("http://ubuntuforums.org/member.php?u=196629") and others

I have been pulling my hair trying to make the Dell Precision ON button (Dell Precision M6500) boot anything other than the total crap Reader 2.1 Dell offers.
It is a VERY crippled down version of Slashtop, using splash.idx and CEFULL just like ExpressGate (the crippling is so deep, the hole thing is contained in a 1.5mb CEFULL file).
I tried stboot 0.1.1 and 0.2 methods, i even tried a method i saw that uses PowerCinema for Linux (that also uses grub, is for Latitude E4200 - 4300, but the bios loader module is very similar and again made by Splashtop).

It always gives me the message "bla bla boot to windows and repair or reinstall Reader bla bla".

I am quite experienced with tweaking so i don't think it is a procedure problem, but rather some Dell specific thing.

Any pointers? Thanks...

---

### Post by Try Again on 2012-05-30
> **Asxetos said:**
> @[Try Again]("http://ubuntuforums.org/member.php?u=196629") and others

I have been pulling my hair trying to make the Dell Precision ON button (Dell Precision M6500) boot anything other than the total crap Reader 2.1 Dell offers...
I'd need a copy of the original CEFULL and most importantly a copy of the bios ROM, so I can pinpoint the differences between Dell's CEFULL and my implementation.

---

### Post by Asxetos on 2012-05-30
Thanks for the reply, i uploaded the files in link below (CEFULL and the ROM module extracted from bios, not the full bios). 

[http://www.multiupload.nl/HW9HS14K1Q](http://www.multiupload.nl/HW9HS14K1Q)

Any advise is welcome...

---

### Post by Try Again on 2012-06-03
> **Asxetos said:**
> Thanks for the reply, i uploaded the files in link below (CEFULL and the ROM module extracted from bios, not the full bios). 

[http://www.multiupload.nl/HW9HS14K1Q](http://www.multiupload.nl/HW9HS14K1Q)

Any advise is welcome...
Well, from what I see, your DVM loader is quite different from mine (coming from an Asus laptop). I still have to understand what it does expect in order to bypass the checks. You should have uploaded the full BIOS image, because it may contain a stripped down CEFULL whose function is to load the CEFULL on the HDD. If I can extract it and try it on my Asus, maybe I can figure out a solution for your Dell laptop.

EDIT: I'm so stupid, the included CEFULL is already in 26_30.ROM... Gotta make some tests now.

---

### Post by Try Again on 2012-06-04
I managed to install the Dell Reader on my computer and it loaded the Reader CEFULL. After then, I tried the embedded CEFULL from the BIOS, nothing was loaded, nothing was shown, but the computer was responsive and rebooted as soon as I pressed a key. It will be hard to know what this particular CEFULL expect to load my own CEFULL as long as I can't test the real thing on a Dell laptop...

Now I have a question: did you still have this 2GB "READER" partition? Maybe the DVM loader needs this specific partition with some sort of marker I'm not aware of and will only load the CEFULL on the HDD only from this partition.

---

### Post by Asxetos on 2012-06-04
Hi Try_Again, and thanks for your efforts...

The "Simple" Dell Reader does not need a dedicated partition. It simply installs in ANY partition, and "splash.idx" points to the folder of "CEFULL".

I think they integrated check routines inside the bios loader to prevent hacking, because the same loader is used for 2 different setups:

First is the free version you have, a totally crippled Splashtop.
The second is a full Splashtop (with a separate kernel file and lots of *.sqx addons) which they sell for big bucks together with an msata module . You cannot install it without the module (at least without hacking the installer) or use it without the module.

I thought the loader was standard but looks like it is custom made...

---

### Post by arunpatal on 2012-07-05
> **Nohajc said:**
> OK, I may have a solution for booting another distro with *ASUS ExpressGate Cloud*.
But, as I haven't got any real ASUS box (at least not yet, I am planning to buy eee soon), I was testing the boot process only in VirtualBox (quite surprising that I could actually install ExpressGate from a Windows XP virtual machine - and it worked). 

After experimenting with menu.lst located in **C:\ExpressGate** I realized that this particular version of Grub is somewhat crippled to say the least. And it's probably on purpose. It seems that it lacks any support of ext file system completely.
As soon as you try to change root to an ext partition it just gets stuck. However, it can start loading any kernel and initrd image present in the same (Windows) partition. That is until you try to set the root to a linux partition - in that case, you end up with kernel panic. In one word: this Grub is completely useless. :-k

To "boot up our way from this mess" we need a better bootloader. So, I figured why not use **Grub4dos**. To make it clear, I wasn't trying to replace current Grub (maybe it could be done, but I'm not that capable hacker). I chose a simpler way.

[SIZE=3]**This is what you should do:**[/SIZE]

**1.** **Download Grub4dos from sourceforge** ([http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/))

**2. Install your preferred linux distro** (Ubuntu Natty in this example) 
When you'll be setting up bootloader, **and this is important**, you should probably install it to the partition (e.g. /dev/sda3) not to MBR (we don't want to compromise Asus' way of booting) Also, we must not delete Windows partition, of course.

This is how the partition table could look like at the end:
```
/dev/sda1 [BOOT] NTFS - Windows loader
/dev/sda2        NTFS - Windows root (C:\)
/dev/sda3        ext4  - Ubuntu root (/)
/dev/sda5        swap
```(and Ubuntu's Grub2 goes to /dev/sda3)

**3. Edit menu.lst** [B]and prepare Grub4dos
[/B]The original C:\ExpressGate\menu.lst looks like this:
```
default saved
timeout 0
hiddenmenu

title minik
  kernel /ExpressGate/vace ro no_win_installer=0 pci=nocrs i8042.reset quiet video=intelfb acpi_backlight=vendor acpi_display_output=vendor vaKBD=us VALANG=en_US fastreboot=no acpi_osi=Linux av_flag=1 rw_flag=1 debug_log=1 nwm=1
  initrd /ExpressGate/vace-id
title Win_1 
  savedefault 0    
  rootnoverify (hd0,0)
  chainloader +1
title Win_2
  savedefault 0
  rootnoverify (hd0,1)
  chainloader +1
title Win_3
  savedefault 0
  rootnoverify (hd0,2)
  chainloader +1
title Win_4
  savedefault 0
  rootnoverify (hd0,3)
  chainloader +1
```Now, we'll just edit the first entry:
```
...
title minik
  **kernel /grub.exe**
title Win_1 
  savedefault 0    
...

```For this to work we'll need to copy **grub.exe** and **grldr** from grub4dos archive to C:\
and then we create second **menu.lst** file also in C:\ (it will be used for accessing our ext partition and loading Grub2)

It can look something like this:
```
timeout 0
default 0
hiddenmenu

title Ubuntu 11.04
root (hd0,2)
kernel /boot/grub/core.img
```From Grub4dos you could of course load Ubuntu kernel directly but this way you won't have to change anything manually after a kernel update (just let Grub2 take care of it).

**4. Reboot the system and see what happens**

OK, now I just wait for you to try it and confirm whether it works.
[COLOR=Red]**[SIZE=3]EDIT: Yes, it works just fine. [/SIZE]**[/COLOR]

Unfortunately, owners of the older versions of ExpressGate cannot use this method because it is based on Splashtop and I've no idea how it boots... but maybe someone will figure it out eventually.

Yes it works for me also.....  there is only one problem.
when i start ubuntu or any os with express gate button.....
the computer start with only nvidia GPU.....   Of course I try to change the graphic card to intel but no use :(
I have 1015PN netbook

Any solution for this?

---

### Post by Poisoj on 2012-07-09
@arunpatal
Ur netbook uses optimus. There are some problems with ubuntu & optimus. Just google it and you will find a possibility to use your onboard graphics on Ubuntu too.

@Nohajc
Thx a lot! Was looking for this for a long time. I did a clean Windows install on my Asus N53SV so I first had to download and install EG again. I followed your guide and everything went well! After that both buttons led me to GRUB. Just fixed the MBR with a MBR tool and the normal powerbutton now boots Win7 directly. Set the GRUB Timeout to 0 and the left button boots Ubuntu immediately by using GRUB. Perfect solution, thank you!

---

### Post by beefcakefu on 2012-10-19
> **Try Again said:**
> I'm eager to get feedback! :popcorn:

I've made a new tarball, it's mainly a code clean-up, but copy operations should be a little faster : [stboot-0.1.1.tar.gz]("http://trya.alwaysdata.net/stboot/stboot-0.1.1.tar.gz")

With a lightweight installation (including readahead and systemd) and a 5400rpm HDD, I manage to get from POST to Chromium in about 30 seconds, POST and GRUB4DOS taking about 7 seconds before loading the kernel, so there's still much room for improvement. I'm now looking for a lighter alternative to GRUB4DOS. SYSLINUX would get my preference, but even more stripped-down bootloaders exist.

Hey Try Again,

Thanks for the great work! Been wanting to do something like this with my EG button since the day I bought my ASUS Pro23A some 3 years back!

I'll be doing up a dual boot Windows 7 & Ubuntu 12.04.1 environment as a weekend project soon and was hoping to pick your brain on this as I'm not 100% sure I understand the README correctly (plus my previous attempts at meddling with GRUB usually ended badly).

[LIST=1]
[*]Wipe drive & create a partition for Windows 7
[*]Install Windows 7
[*]Copy everything in 'root-example' over to C:
[*]Create partitions and install Ubuntu 12.04.1 (Any special instructions about GRUB configuration, etc?)
[*]Update menu.lst
[/LIST]

Currently, I'm unsure about 4 & 5 but 5 can be easily answered with a Google search. Could you please elaborate more on how to do 4? Thanks!

Cheers,
James

---

### Post by Try Again on 2012-10-21
> **beefcakefu said:**
> Currently, I'm unsure about 4 & 5 but 5 can be easily answered with a Google search. Could you please elaborate more on how to do 4? Thanks!
Beginning with 4, you have two possibilities depending on the version of stboot:
- with stboot 0.1.1, once you installed Ubuntu, just edit your menu.lst from GRUB4DOS (but it's quite slow compared with the second method)
- stboot 0.2 includes a simple bootloader which chainloads the first active partition, so you can install Ubuntu on a partition you made active and install GRUB2 on this partition boot sector. For example, if you install Ubuntu on /dev/sda2, install GRUB2 on /dev/sda2 and not /dev/sda, as it's usually done

There are more possibilities, but these are the simplest.

---

### Post by beefcakefu on 2012-10-25
> **Try Again said:**
> - stboot 0.2 includes a simple bootloader which chainloads the first active partition, so you can install Ubuntu on a partition you made active and install GRUB2 on this partition boot sector. For example, if you install Ubuntu on /dev/sda2, install GRUB2 on /dev/sda2 and not /dev/sda, as it's usually done

Hey Try Again,

I'm still fumbling with stboot 0.2, your assistance is much appreciated! Here's what I did:

Installed Windows 7, which created 2 partitions sda1 & sda2. Taking care to choose 'Something else' from the Ubuntu Installation Type selection, I created 3 new partitions:
[LIST]
[*]/dev/sda3    ext4    /        (Primary Partition)
[*]/dev/sda5    ext4    /home    (Logical Partition)
[*]/dev/sda6    swap             (Logical Partition)
[/LIST]
Next I set /dev/sda3 as 'Device for boot loader installation' and let the Ubuntu installer run to completion. Upon restart, the system booted into Windows 7 and I saw no apparent way to access the new Ubuntu installation.

At this point, I downloaded [stboot-0.2.tar.gz]("http://trya.alwaysdata.net/stboot/stboot-0.2.tar.gz") and copied the contents of 'root-example' to C:. Next I tried to EG with the example setting and got 'Chainloading from partition...' before Windows appeared to be loading, then a spontaneous reboot and then a Windows Error Recovery prompt.

Next I tried booting from the Ubuntu CD and did "dd if=/dev/sda3 of=1st_sect.bin bs=512 count=1", overwrote bootsect.bin with 1st_sect.bin and installed yasm but when I tried to "yasm -o CEFULL stboot.S", it complained about a missing stboot.S.

I guess the few things I have doubt about are:
[LIST=1]
[*]Was I supposed to make sda3 active during Ubuntu installation, a step I perhaps missed?
[*]Does running dd from the live CD work? I've uploaded my '1st_sect.bin' [here]("https://dl.dropbox.com/u/1267338/1st_sect.bin") if you wouldn't mind taking a look, in case this method doesn't work.
[*]I obtained my copy of 'stboot-0.2.tar.gz' from 'trya.alwaysdata.net/stboot/'. Is this the correct copy or is it missing stboot.S?
[*]Was there a step I missed that compiles the .asm files into stboot.S?
[/LIST]
I've I feel I'm getting really close and thanks again for all you've done!

Cheers,
James

---

### Post by Try Again on 2012-10-25
> **beefcakefu said:**
> [*]Was there a step I missed that compiles the .asm files into stboot.S?
You're almost there, but it's all my fault, because I forgot to update the README when I renamed the source files from *.S to *.asm. You should read stboot.asm when it mentions stboot.S.

The README is the SVN repo is the correct one: [http://stboot.googlecode.com/svn/trunk/README](http://stboot.googlecode.com/svn/trunk/README)

EDIT: [stboot 0.2.1]("http://trya.alwaysdata.net/stboot/stboot-0.2.1.tar.gz") is up in order to avoid any confusion.

---

### Post by beefcakefu on 2012-10-25
> **Try Again said:**
> You're almost there, but it's all my fault, because I forgot to update the README when I renamed the source files from *.S to *.asm. You should read stboot.asm when it mentions stboot.S.

The README is the SVN repo is the correct one: [http://stboot.googlecode.com/svn/trunk/README](http://stboot.googlecode.com/svn/trunk/README)

EDIT: stboot 0.2.1 is up in order to avoid any confusion.
You, sir, are a prince among men! It's working for me now and I can't tell you how much I LOVE it! Thank you so much!

---

