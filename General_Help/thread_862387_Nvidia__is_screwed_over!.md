---
title: "Nvidia  is screwed over!"
date: 2008-07-17
forum: General Help
---

### Post by Cr0wZz on 2008-07-17
i have an nvidia geoforce 8400 GS

and it worked. So i installed warhammer, and warhammer never crashed once.


time passed, and i was eager to try adding ubuntu to my xp computer(with 250 gigs, i figured itd be fine)

that worked perfectly, booted perfectly, configured perfectly, nividia drivers worked perfectly, compiz worked

but


when i switched back over to windows, every time i would try and play a game (warhammer, or command and conquer 3)

the game freezes, the whole computer freezes, the sound f**ks up, and i have to turn it off by pulling out the plug

it worked fine before ubuntu,

i update the driver

no good

i rolled it back twice

no good

and right now, i cant find my xp cd!

so i cant format!!!

can anyone help me please!!

i get a lot of bluescreens in windows saying something about DRIVER_OSV_X301 or something

---

### Post by Sasa_Ivanovic on 2008-07-17
you really don't have any luck.

but i can't see why is installing ubuntu related in any way with your windows nvidia drivers, have you done something else recently?

---

### Post by Cr0wZz on 2008-07-17
No i cant say ive done anything at all, i dont get what happened to my nvidia card

my comp specs are


Seagate barracuda 250gb hd
AMD Opetron dual core processor
2gb of random RAM from staples
and the nvidia card, i just dont get it..


But then i started thinking...the graphics card has a cache of memory, just like a little hard drive...is there a way to put a virus in a graphics card? :confused:

---

### Post by Viper666 on 2008-07-17
hmmm ubuntu really has nothing to do with your symptoms. It doesnt change anything inside de Windows partition (not even the Wubi installer which only adds 2-3 files)

> But then i started thinking...the graphics card has a cache of memory, just like a little hard drive...is there a way to put a virus in a graphics card? no you cant... first off all it's volatile (when it has no power it erases itself like RAM) and secondly i'm pretty sure noone tried that :))

---

### Post by Cr0wZz on 2008-07-17
> **Viper666 said:**
> 
 (when it has no power it erases itself like RAM)


I figured, just thought id ask, never hurts.

---

### Post by f37u5g0d on 2008-07-17
Turn on your computer. While the bios is doing it's thing and before you get to grub turn the computer off without using the button on the front.  Either pull the plug from the tower or the wall or (hopefully) your power supply has a switch that you can turn off.  I have to do this everytime I want to use my onboard wired network after shutting down ubuntu the correct way.  I have no idea why but if I log into ubuntu and then shut down the system correctly my network card doesn't exist until hit the switch on my psu while the computer is on.

---

### Post by jonian_g on 2008-07-17
I'm not a windows expert but the only I know you can do with problems that give you blue screens is format or call a microsoft support centre for help.

---

### Post by jonian_g on 2008-07-17
> **f37u5g0d said:**
> Turn on your computer. While the bios is doing it's thing and before you get to grub turn the computer off without using the button on the front.  Either pull the plug from the tower or the wall or (hopefully) your power supply has a switch that you can turn off.  I have to do this everytime I want to use my onboard wired network after shutting down ubuntu the correct way.  I have no idea why but if I log into ubuntu and then shut down the system correctly my network card doesn't exist until hit the switch on my psu while the computer is on.
Doest that f**k up your HD? Bad sectors (blocks).

---

### Post by solitaire on 2008-07-17
> **jonian_g said:**
> Doest that f**k up your HD? Bad sectors (blocks).

Doing it once or twice won't harm your drive!

Did you use any partitioning software then you added Ubuntu to the XP machine? Or are you using Wubi?

If you repartitioned the drive, you might want to do a full scan of the XP partition in case something was borked during the repartition....

Best thing to remove is any temp file from the XP partition including Swapfile. It is probably easier to do it under Linux. :D

---

### Post by Pettman on 2008-07-17
> **jonian_g said:**
> Doest that f**k up your HD? Bad sectors (blocks).

Not if you pull the plug before the bios have started reading from the disk.

---

### Post by jimv on 2008-07-17
> I'm not a windows expert but the only I know you can do with problems that give you blue screens is format or call a microsoft support centre for help.

There's much more you can do.

When you get a BSOD in Windows, it will create a log file called a 'bugcheck' that you can look in to see what is causing the problem.  Usually it's a driver conflict.

Here's a writeup on the MSDN on how to debug these kinds of problems:

[http://blogs.msdn.com/ndis/archive/2006/10/26/troubleshoot-a-windows-bluescreen-a-k-a-bugcheck-a-k-a-blue-screen-of-death.aspx](http://blogs.msdn.com/ndis/archive/2006/10/26/troubleshoot-a-windows-bluescreen-a-k-a-bugcheck-a-k-a-blue-screen-of-death.aspx)

It looks complicated, but it's not really that hard.

The worst case scenario is that you'd have to reinstall Windows.  You can use any XP disk that is the same version as yours (Pro vs Home) as long as you have your serial number (so you can borrow one from someone).  If you have laptop, the XP serial number is probably on the bottom of the machine.  If you don't have a laptop, you can display the serial number for your machine with a number of utilities on the web.  Just do a google search for 'display xp serial number'.

---

### Post by jonian_g on 2008-07-17
> **Pettman said:**
> Not if you pull the plug before the bios have started reading from the disk.
And maybe destroy somethin else, like your mobo.

When suggesting such things better say what are the potential dangers and do it at your own risk.

---

### Post by Mgiacchetti on 2008-07-17
ok for bluescreens, write down the stop code, (it will look like 0x0000000) if there's more than one, write them all down.  search google or microsoft for those errors.

for installing ubuntu on a system with windows already installed.  ALWAYS RUN A SCANDISK AND DEFRAG before editing the partition, if you don't things like this can happen.  

for windows messing up.  Don't always assume that another os (which by the way is on a seperate partition, and unless you mount your windows partition in that other operating system, WILL NOT AFFECT windows in any way)   is the problem.  Maybe something is messed up in the bios?  CHECK YOUR BIOS SETTINGS before assuming anything.   Sometimes a del (or f1, f5 or f10 depending on your system) restore to system defaults f10 y enter will do the trick.

If you really think its ubuntu, try uninstalling it totally and I bet your problem will still linger.  you might want to go directly to Nvidia and get the CORRECT drivers for your video card, as the third party drivers (mad dog, pny etc.) can be problematic, and I have actually ran into viruses embedded in things like that (mad dog).

If all else fails, get WINE for ubuntu and run the game there.  No more need for a windows partition.

Best of luck.

---

### Post by stchman on 2008-07-17
> **Cr0wZz said:**
> i have an nvidia geoforce 8400 GS

and it worked. So i installed warhammer, and warhammer never crashed once.


time passed, and i was eager to try adding ubuntu to my xp computer(with 250 gigs, i figured itd be fine)

that worked perfectly, booted perfectly, configured perfectly, nividia drivers worked perfectly, compiz worked

but


when i switched back over to windows, every time i would try and play a game (warhammer, or command and conquer 3)

the game freezes, the whole computer freezes, the sound f**ks up, and i have to turn it off by pulling out the plug

it worked fine before ubuntu,

i update the driver

no good

i rolled it back twice

no good

and right now, i cant find my xp cd!

so i cant format!!!

can anyone help me please!!

i get a lot of bluescreens in windows saying something about DRIVER_OSV_X301 or something

So after you installed Ubuntu the NEXT time you booted into Windows the video drivers were screwed up?  What method did you use to install Ubuntu?

---

### Post by Mgiacchetti on 2008-07-17
The best method to install ubuntu on an already windows computer is to pop the cd in and just restart the pc, hit the "key for boot device" and choose cdrom.  install from there, making sure to follow the procedure of manual partitioning (if you know what you are doing, if not read up) and make sure you know how to fix things if they might break (i.e. grub not booting windows bootsector problems)  

again and i cannot stress this enough SCANDISK DEFRAG SCANDISK RESTART  this makes sure there are no files where you might want to split the partition if you go that route, plus its good maintnence for windows anyway (dang fragging filesystem)   i prefer flashbangs but hey windows is windows.

---

### Post by Ataris on 2008-07-17
A great classic of example of Microsoft's corruption. I hope Apple or Linux can defeat them next year when they start leasing Windows instead of selling it.

Go Ubuntu!

---

### Post by jimv on 2008-07-17
> **Ataris said:**
> A great classic of example of Microsoft's corruption. I hope Apple or Linux can defeat them next year when they start leasing Windows instead of selling it.

Go Ubuntu!

Yeah, because Ubuntu NEVER crashes, locks up, or has driver issues.

Zealotry is useless, btw.

---

### Post by doas777 on 2008-07-17
Actually, strangely enough i have seen cross OS issues with NVIDIA cards. 

for instance, we installed a new Nvidia card in a box and booted into windows. the BIOS on the TV out showed up in color. we installed the driver and everything was great.

we then booted into Ubuntu, and installed the nvidia-glx-new restricted driver. TV outs function but are in black and white. rebooted. now the BIOS is in B&W not color. 

We determined that we needed to set the TV out format to SVID and now once booted the TV will be in color, but the BIOS is always B&W.

As close as we can tell, the output type is determined by a hardware switch in the vidcard firmware.

I know that this doesn't help the issue, but it is a strange tale of woe, isn't it?

good luck,
Franklin

---

### Post by Nexusx6 on 2008-07-17
this:
> adding ubuntu to my xp computer
and this:
> i switched back over to windows, every time i would try and play a game... ...the game freezes, the whole computer freezes,

Are not related to each other. In my experiance, this problem you are having is caused either by driver conflic or by bad data being called from the memory. Since you don't mention installing any new drivers on the windows side this problem is likely stemming from either your hard drive or your ram.

I highly suggest running a scan on your hardrive for any bad blocks. Also, try to duplicate the problem by testing each ram stick. You can do this by pulling one stick out, trying a game, then replacing that stick with the one you had pulled so that they are tested individualy. The Ubuntu Live CD also comes with a Memtest program to scan your sticks.

---

### Post by Cr0wZz on 2008-08-21
> **solitaire said:**
> 

Did you use any partitioning software then you added Ubuntu to the XP machine? Or are you using Wubi?


I used Ubuntu 8's auto partitioner, i made ubuntu 28% of my disc

[B]
According to tuneup utilities, my disc is fine.[/B]

[B]
I HAVE FOUND MY XP CD, MY NVIDIA DRIVERS, AND MY MOTHBOARD SUPPORT CD, I WILL ERASE UBUNTU, I THINK ILL STICK WITH FEDORA ON ITS OWN INSTEAD OF DUAL BOOTING AGAIN[/B]

---

### Post by Cr0wZz on 2008-08-21
> **ataris said:**
> a great classic of example of microsoft's corruption. I hope apple or linux can defeat them next year when they start leasing windows instead of selling it.

Go ubuntu!


corruption?! I paid $189 for that card, ubuntu was *free*
partoining with ubuntus partioner screwed up my hard drive!

---

### Post by rbmorse on 2008-08-21
Probably not, but if it makes you feel better to think that...

---

