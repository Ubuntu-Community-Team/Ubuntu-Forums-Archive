---
title: "Asus G50V-A1"
date: 2008-09-10
forum: Hardware
---

### Post by Nex82 on 2008-09-10
Hi,
I have just bought that notebook. First action after plugging in was, of course, put in hardy and tries to install. But then crazy running error occurs. So I have tried to install the whole thing thru wubi. That works and I can boot to ubuntu now (not the best solution but ok). 
And now the problem is that I can not get any connection thru wifi or wired link. 
Any one got an idea or solution for?
thx
Nex

---

### Post by Nex82 on 2008-09-11
nobody?

---

### Post by life_s_good on 2008-09-11
What is the output of your

```
sudo ifconfig
```

If it is nothing try

```
sudo ifconfig eth0 up
```

What is your wireless card? Look for it in the command:

```
sudo lcpsi
```

---

### Post by Nex82 on 2008-09-12
hi,
i am at work now but will post the informations asap.
for now:
[http://www.asus.com/products.aspx?modelmenu=2&model=2414&l1=5&l2=74&l3=762&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2414&l1=5&l2=74&l3=762&l4=0)

it is one of those:
Intel® Wireless WiFi Link 4965AGN or Intel® PRO/Wireless 3945ABG 

but i think that the driver is not the problem. the problem is that i am not able to switch the card on. 
this notebook got a switch on the front to turn on bluetooth and wireless at the same time. and a FN+F2 to switch between bluetooth, wireless or both. but when i try to turn on the switch i can only manage to get bluetooth. that's why i think there is the problem for wireless. but there is a problem with wired connections, too.
Nex

---

### Post by Nex82 on 2008-09-14
Errors after pressing "Install"

ubuntu kernel: [722.652931] SQUASHFS error: sb_bread failed reading block 0xbf0d3
and there are several similar errors with anothoer number between []
then
VFS: busy inodes changed media
then cron comes up with INFO (pidfile fd = 3), STARTUP(fork ok), INFO (Running @reboot jobs)

putting in a usb stick to safe syslog leads to a running error SQUASHFS error Unable to read page (something, can't read it) and all consoles r gone/or the keyboard is no longer working

I have tried i386, amd64 cd's and the amd64 dvd hardy 8.0.4.1

i'll try the new alpha-5 releas next.

---

### Post by life_s_good on 2008-09-14
Flick the switch on and try using ifconfig to bring the interfaces up. There is support for those cards and has been for quite some time, so that is safe to rule out.

---

### Post by Nex82 on 2008-09-14
Hi,
i have tried to install with alpha-5 yesterday. And i couldn't manage to get into the live cd system with te same SQUAD errors and freezing.

ANd i have tried almoste everything to get the network running. but i wasn't able to connent via wifi or wired. And there is the little freezing problem.

---

### Post by Keymaster on 2008-09-15
Looks like we are in the same boat.  I'm really hoping the final version of Intrepid Ibex will help us solve our problems.  I've tried ndiswrapper to no effect, and I couldn't get audio working either.  Let me know if you figure anything out.

---

### Post by Nex82 on 2008-09-15
it's a pitty. 1. happy to have a new fency system. then no chance to install ur fav. os. so i have to live with vista as long as alpha 6 or 7 is out (or beta) #-o](*,)](*,)

Nex

---

### Post by Keymaster on 2008-09-15
perhaps we should petition asus to release debian drivers for their systems.
Id' be on board for this.

---

### Post by Nex82 on 2008-09-15
how high would be the chance that a million dollar company release debian driver because of a petition ? I mean there not so much G50 users out there and older systems normally supported out-of-box.



PS: do u have any idea how to update the splashtop linux ?

---

### Post by costing on 2008-09-17
Hi,

It took me 3 full days and nights to install Hardy on a g50v, but now I'm typing from it :) Here is a short walk-through the main steps:
[http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/](http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/)

Please let me know if you figure out how to program the OLED display, the asusoled driver cannot talk with this new variant unfortunately.

Cheers,

.costin

---

### Post by Nex82 on 2008-09-18
so i have tried that now. and something went really wrong. now i am currently redo the whole system because nothing is working. damn. but one good thing i was able to run intre and get a wired connection

---

### Post by costing on 2008-09-18
Mmm, that's not good. What are the symptoms? Do you get a completely black screen by chance? This happened to me as well but you can choose from Grub the recovery mode to fix the xorg.conf file.

If the new kernel doesn't boot at all you probably haven't selected all needed modules. Attached you find the .config file that worked for me.

Good luck!

.costin

---

### Post by costing on 2008-09-18
Sorry, above is the original .config file for 2.6.24-19. Here you have the one for 2.6.27-rc6. This is what happens when you don't have the morning coffee before posting :)

Cheers,

.costin

---

### Post by Nex82 on 2008-09-18
i have done the whole thing by resizing one of my partition and then installing in the new empty space. that works fine and grub recognize every os. BUT then the problems have started. ubuntu got blackscreen, the sounddriver do his job but in the wrong why (beep beep beep beep ...) and then i decided to go remove everything and redo. but windows has been somehow damaged and i got this nice blue screen after startup. so i'll wait for intrepid alpha 6 (which should be released today), if i find a working mirror

---

### Post by costing on 2008-09-18
I hope this time Intrepid will work, a few days ago I got errors installing it related to packages dependencies not resolved on the CD ... 

See, you started the wrong way :) Just drop all partitions and create a fat ext or reiser one :D

Cheers,

.costin

---

### Post by Haventfoundme on 2008-09-18
I definitely would take part in that petition


---ASUS F9S Carrier---

---

### Post by MajinFonz on 2008-09-18
I have the Asus G50V-A2 and I'm having the same problem. What I want most is to get the wired connection working. So if I follow the guide above than that should be fine how me too? Only problem is that I'm not sure if my router has a USB connection :/ (I'll have to check when I'm home). So am I out of luck than?

---

### Post by costing on 2008-09-18
You should try it out, maybe it was something funny with mine only since I don't remember this problem being reported by anybody else before.

And if it really doesn't work you still have several options:
- download all required packages manually, but with the many dependencies that they have it will be a mess
- connect via bluetooth with another computer (or even your router maybe knows BT)
- use a usb special cable to connect to the above computer
- borrow an old(er) USB or PCMCIA wireless card, known to work in linux (either native drivers or ndiswrapper)
- or a USB or PCMCIA ethernet adapter

Good luck!

.costin

---

### Post by Nex82 on 2008-09-19
hi, 
good news everyone. 
I have installed intrepid alpha-6 now. and it works fine after two little changes.

1. i have installed the whole thing with wubi because i am at work and the installing process makes some terrible noise if u do it the normal way.

2. after the first boot u have to delete these acpi files to be able to enable the wireless connection (thx costing)
```

sudo rm -f /etc/acpi/asus-wireless*
sudo rm -f /etc/acpi/*/*asus-wireless*

```

after a short reboot i got a nice intrepid with wireless connection.
cheers


[x] sound
[x]  webcam
[x] nvidia driver 177 works after a long install periode (looks like it is freezing but it is not until it reaches 
     100% but after a short relogin everything is installed. but i seems like it is a little slow/sticky
[x] compiz-fusion
[x] wireless connection
[] wired connection


[x] skype but i have only been able to manage the static verison to go online


And do not try to install the 173 after u have installed 177 nvidia driver. process could die and yeah everything then is a little mess. and surprisingly the wireless connection is also affected.

---

### Post by Keymaster on 2008-09-20
Could you provide detailed instructions for me, on how you got each device working?  I mainly only care about wired/wireless sound, and nvidia.  I have very little understanding of the way the kernel works, and no understanding of compiling in linux.  You can PM me the instructions, if you do not want to post them.  I'd really appreciate it.  Also I'd like to put them on a tech support website for gamers that like linux, so please include a name you'd like to receive credit under.

> **Nex82 said:**
> hi, 
good news everyone. 
I have installed intrepid alpha-6 now. and it works fine after two little changes.

1. i have installed the whole thing with wubi because i am at work and the installing process makes some terrible noise if u do it the normal way.

2. after the first boot u have to delete these acpi files to be able to enable the wireless connection (thx costing)
```

sudo rm -f /etc/acpi/asus-wireless*
sudo rm -f /etc/acpi/*/*asus-wireless*

```

after a short reboot i got a nice intrepid with wireless connection.
cheers


[x] sound
[x]  webcam
[x] nvidia driver 177 works after a long install periode (looks like it is freezing but it is not until it reaches 
     100% but after a short relogin everything is installed. but i seems like it is a little slow/sticky
[x] compiz-fusion
[x] wireless connection
[] wired connection


[x] skype but i have only been able to manage the static verison to go online


And do not try to install the 173 after u have installed 177 nvidia driver. process could die and yeah everything then is a little mess. and surprisingly the wireless connection is also affected.

---

### Post by Nex82 on 2008-09-21
Hi,
First of all, this is only working with the new Intrepid Alpha 6 release. (Alpha 5 is NOT working that way)
1. Before you try to install Ubuntu, you have to change the bios. In there you have to change the hdd operating mode from Enhanced to Compatible mode. ( [http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/]("http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/") ) 
------ This could cause that windows cannot boot properly if u intend to do dual boot ------
------ Make the bios change and try if windows is still working, if not change back if you want to use this windows installation. Else reinstall windows BEFORE (if you only got the rescue disc's) you install Ubuntu -----

2. Install Ubuntu as usual (there are many guides out there how to do that) - be aware if you do a "normal" install 
    A. you have to partition you hard drive
    B. the install makes some terrible noise during the install
       If you install with wubi there is no such problem.

3. After you have restarted open a terminal (Accessories->Terminal) and type in 
```

sudo rm -f /etc/acpi/asus-wireless*
sudo rm -f /etc/acpi/*/*asus-wireless*

```
This will enable you to turn on the wireless connection (the blue light on the front) after u have done a restart. (Press FN+F2)

4. Install all updates - for that u should run the update-manager, either by pressing Alt+F2 and enter "update-manager" (without quotes) or via System->Administration->Update Manager. Click check and then install - this will take sometime depending on your internet connection and server status.

5. After a short reboot you could activate the NVidia driver. Just go to System->Administration->Hardware Drivers and install version 177 or higher

If everything went fine you should now have a nice and cozy Ubuntu. And do not freak out about the nice loading and shutdown screen - it works and is running, most of the time.

---

### Post by Keymaster on 2008-09-21
Thanks for the help.  What do you mean by freaking out over the loading screen?  Also what is a wubi install?  Do the updates get the sound to work as well?

Edit: I'm assuming this will work using LUKS encryption since my job requires all systems have full disk encryption :(

---

### Post by Nex82 on 2008-09-21
wubi - [http://wubi-installer.org/](http://wubi-installer.org/) is the windows installer for ubuntu. Means you can install ubuntu within windows and you do not have to change any of your partition. the whole system is just safed in some big files.

freaking loading screen - since it is a alpha version of ubuntu and there are some thing that will change i wouldn't think of it. but currently there is something like gray and read blocks during loading where the normal ubuntu logo with the loading bar should be. looks creapy but i think they will find a way around and if you do not care it makes no difference to the system so far.

sound - yes sound works without any additional work. it is just during the boot of the install the pc speakers are beeping all the time. but that stops after some times normally and the acctual system is not affected.

LUKS - i haven't tried that. but i think if it is working with the alpha 6 (and i think so) then there shouldn't be any problem

---

### Post by Keymaster on 2008-09-21
Sounds good.  I think the only difference with LUKS is encryption anyway, so that shouldn't matter.  I'm concerned about what that bios tweak will do to my vista system, as I obviously still use that for gaming. ;)

---

### Post by Nex82 on 2008-09-21
i think the worst thing that could be happen is that you get some startup blue screens. 
If you just want to use it for gaming, and you get the blue screens. Change back the bios and do something like this
1. Save ALL data you want to keep, just in case something go wrong. 
2. Then change the bios. 
3. Reinstall vista with the rescure disks to the first partition (there will be a window with three option to reinstall the system and i think the first one is the one you should take)
4. after the vista reinstall
   A. resize your partitions to get the free space you want for the linux system
   B. install ubuntu with wubi (should be the second option in the autorun window of the ubuntu disk) on one of the availible disks. but be aware that this solution slows down the linux system a little bit.

---

### Post by Keymaster on 2008-09-21
I can't use wubi since I'm going to be using LUKS for volume encrypion.  Plus if my Windows gets compromised, then so does my linux.  I'm going to test the bios setting now.

---

### Post by Keymaster on 2008-09-21
Yeah, I got startup BSoDs after 2 seconds.  I think the first time I tried to install 8.04 x64 it worked without the bios setting though.  Anyone know what kernel is going to be in 8.10?

---

### Post by Nex82 on 2008-09-21
This BSoDs is something new coming with the Asus G50 series. Maybe the next kernel or the current will be in adapted. But i do not know exactly why this happens when you switch from enhanced to compatible. maybe someone else knows. 
Why should a compromised windows affect ubuntu installation (if have installed it the usual why?

---

### Post by Keymaster on 2008-09-22
I think since Vista was installed using the Enhanced Mode it requires that mode to boot properly.  If wubi installs Ubuntu in a large file in the Windows partition, and that partition gets hosed, then Ubuntu is gone too.  I'm just hoping that installing Ubuntu by booting off the disk does not require Compatibility Mode in the BIOS.  I don't think it did when I temporarily had 8.04 on here.  I couldn't get 8.04 to work right though.

---

### Post by Nex82 on 2008-09-22
Ubuntu got this problem with the G50 enhanced mode. why i do not know. but maybe there will be a fix soon. and installing with wubi is not as dangerous. you can try to do it without changing the bios . maybe it works. for me it didn't.

---

### Post by Keymaster on 2008-09-22
Perhaps because it's an alpha right now.  I'm really hoping I don't have to reinstall Vista.  I just finished tweaking it, and getting all my custom settings just right.  I guess we will have to wait, and see.

---

### Post by Nex82 on 2008-09-22
i don't like to wait. so i have done the whole "reinstall" thing. and it works

---

### Post by Keymaster on 2008-09-22
You mean you reinstalled Vista, or just Ubuntu?  What bios setting did you use?  Did you try ubuntu without changing the bios?

---

### Post by Nex82 on 2008-09-22
the only thing i have changed was the enhanced to compatible thing. everyhing else says the same. but after that i have to reinstall vista and then i have install ubuntu. simple as that. 

maybe the next releases will not need the bios change

---

### Post by Keymaster on 2008-09-22
I'm hoping it doesn't require the change.  Do you think that if Vista was installed with Enhanced setting, and then after switching it to Compatible, the startup repair on a vista disk would fix it?

---

### Post by Nex82 on 2008-09-23
mmm that could be a option to do that. but i have no time right now to try that.

---

### Post by Keymaster on 2008-09-23
I would try it myself, but I do not have an actual Vista disk in my possession. (Just the recovery disks)  This is the only Windows computer in the house, so I don't really have any Windows disks anymore.

---

### Post by Nex82 on 2008-09-23
----------WARNING-------------
the last updates may cause that the system is not starting correctly. (i have updated todays morning.:mad:
September 23 2008

---

### Post by Keymaster on 2008-09-23
What do you mean it isn't starting correctly?  Does the OS boot? GDM not working?

---

### Post by Nex82 on 2008-09-23
the system boots but the screen stays black or in somefreaky colours. and i think it is freezing after a while. because i am not able to get to a commandline or into the GDM.

---

### Post by Keymaster on 2008-09-23
Hmm, how are you supposed to fix this issue, if you can't even get to a command line?  Sound to me like I'm imaging the drive everytime I'm ready to run update-manager :(

Edit: I'm hoping this type of issue is resolved in the Final Release as well

---

### Post by Nex82 on 2008-09-23
i am pretty sure it will.

---

### Post by Keymaster on 2008-09-23
That's good to know.  Any idea which of the updates was the actual cause?

---

### Post by Nex82 on 2008-09-23
so i have figured out that the problem comes from the nvidia driver. so maybe it is possible to uninstall the driver beforehand and after all update install it again. but that would be a very creapy workaroun for now.

---

### Post by Nex82 on 2008-09-23
so i have just do a restart with general settings graphic settings. and installed all  "new/additional" updates.
but now the system does not recognize the nvidia drivers anymore.

so i have to reinstall all nvidia packages via synaptic. Then i have opened the hardware driver menu and reactivate the 177 driver version. (only the red ball will change to the green one. nothing else happens.) 
now i have done a uninstall of the nvidia driver from within the hardware driver window. now you have to make sure that in the xorg.conf file the driver line has changed to "vesa" before you do a restart. 

then you should be able to reinstall the nvidia drivers

---

### Post by Nex82 on 2008-09-23
ok it's working again. maybe something with the kernel mod tools are wrong. but they have managed to solve the loading screen issue

---

### Post by Keymaster on 2008-09-23
So should I install the Nvidia 177 driver still, or not?

---

### Post by Nex82 on 2008-09-23
ok a little problem here. i cant get a wireless connection now... grml

---

### Post by Nex82 on 2008-09-23
Ok now. hell. these updates driving me nuts. 

i have now managed to get back online. and got the nvidia driver working.

there is/was a problem with the mod tools. i don't know what exactly but thez have added it to the updates now. maybe it works now without any update problems.

---

### Post by archangelenmity on 2008-09-24
Sorry jumping in a bit late here. I have the ASUS G50V-X1, and first of thanks for the help so far. Would this be the same if when I go to install the 177 driver nothing happens, the install box pops up and says 0% then after about a minute it just disappears, no driver installed nothing back to the choice between 173 and 177. No green dot; nothing. 

> **Nex82 said:**
> so i have just do a restart with general settings graphic settings. and installed all  "new/additional" updates.
but now the system does not recognize the nvidia drivers anymore.

so i have to reinstall all nvidia packages via synaptic. Then i have opened the hardware driver menu and reactivate the 177 driver version. (only the red ball will change to the green one. nothing else happens.) 
now i have done a uninstall of the nvidia driver from within the hardware driver window. now you have to make sure that in the xorg.conf file the driver line has changed to "vesa" before you do a restart. 

then you should be able to reinstall the nvidia drivers

---

### Post by Keymaster on 2008-09-24
So, how did you get everything working again?

---

### Post by Nex82 on 2008-09-24
if this happens for me. the server could not be found. try to update the system and instll again. and do not make the failure and install 173.

---

### Post by Nex82 on 2008-09-24
i think the way i did the trick is a little bit confusing.
but for you if the update doesn't work do something like
1. turn off the nvidia driver - to get back to a gdm interface - if you want
2. reinstall the 177 - if it works /check witch the hardware driver window - great else 
3. try to activate it via the hardware driver window - if nothing happens except the red dot turns into green you have to 
4. uninstall the whole driver via that window and
5. reinstall it AFTER a reboot. 
6. BUT you can have some trouble to reconnect via wireless after reinstall. i haven't figured out why yet, but after 3 reboots it is working again.

---

### Post by archangelenmity on 2008-09-24
Hey thanks Nex82. Everything works perfect for me now, not a 100% sure what I did but my first install of Ubuntu went better than thought. Only issue left now is sound.

---

### Post by Nex82 on 2008-09-25
i never run into that problem with ubuntu but once with vista i run into that. this was because i have turned of the post sound in the bios.

---

### Post by Nex82 on 2008-09-26
the last updates working fine for me. no troubles no errors.

@archangelenmity: is the sound working now?

---

### Post by Nex82 on 2008-09-28
news: 
still got the beep until the line:
Loading Hardware drivers [done]

the wireless is now working (daily build/last updates)but do NOT turn it off else you have to reboot to turn it back on. 

and there are some little errors:

> kernel: [    1.554484] input: AT Translated Set 2 keyboard as /class/input/input1
Sep 28 08:38:33  kernel: [    1.644045] fuse init (API version 7.9)
Sep 28 08:38:33  kernel: [    1.708049] uvesafb: failed to execute /sbin/v86d
Sep 28 08:38:33  kernel: [    1.708260] uvesafb: make sure that the v86d helper is installed and executable
Sep 28 08:38:33  kernel: [    1.708470] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
Sep 28 08:38:33  kernel: [    1.708719] uvesafb: vbe_init() failed with -22
Sep 28 08:38:33  kernel: [    1.708962] uvesafb: probe of uvesafb.0 failed with error -22
Sep 28 08:38:33  kernel: [    1.749452] ACPI: SSDT BFF96BC0, 0248 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Sep 28 08:38:33  kernel: [    1.750010] ACPI: SSDT BFF96EA0, 0765 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Sep 28 08:38:33  kernel: [    1.750765] Monitor-Mwait will be used to enter C-1 state
Sep 28 08:38:33  kernel: [    1.750767] Monitor-Mwait will be used to enter C-3 state

and 

>  kernel: [    3.832232] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Sep 28 08:38:33  kernel: [    3.832239] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Sep 28 08:38:33  kernel: [    3.832243] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 28 08:38:33  kernel: [    3.832259] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Sep 28 08:38:33  kernel: [    3.832300] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
Sep 28 08:38:33  kernel: [    3.832370] usb usb5: configuration #1 chosen from 1 choice
Sep 28 08:38:33  kernel: [    3.832389] hub 5-0:1.0: USB hub found
Sep 28 08:38:33  kernel: [    3.832393] hub 5-0:1.0: 2 ports detected
Sep 28 08:38:33  kernel: [    4.028043] usb 2-2: device not accepting address 2, error -71
Sep 28 08:38:33  kernel: [    4.040162] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 28 08:38:33  kernel: [    4.040169] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Sep 28 08:38:33  kernel: [    4.040173] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 28 08:38:33  kernel: [    4.040189] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Sep 28 08:38:33  kernel: [    4.040223] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
Sep 28 08:38:33  kernel: [    4.040292] usb usb6: configuration #1 chosen from 1 choice
Sep 28 08:38:33  kernel: [    4.040311] hub 6-0:1.0: USB hub found
Sep 28 08:38:33  kernel: [    4.040315] hub 6-0:1.0: 2 ports detected
Sep 28 08:38:33  kernel: [    4.084078] hub 2-0:1.0: unable to enumerate USB device on port 2

and sometimes the screen is black during startup.

---

### Post by Keymaster on 2008-09-30
What are the actual differences between 8.04's kernel and 8.10s?  I'm curious as to how this will affect functionality on my ASUS.

---

### Post by costing on 2008-10-08
Once you have the system running you might want to take a look at this piece of software to make use of your OLED display ;)

[http://asusg50oled.sourceforge.net/](http://asusg50oled.sourceforge.net/)

---

### Post by Keymaster on 2008-10-08
I'll definitely install that once everything important is running, but right now I'm waiting for Intrepid's final release, before trying anything.  I'm not too good with customizing, or installing from source.

[http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/](http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/) helps but I do not have access to a router that supports usb links.  I think I actually have an RJ45 to USB cable, but I don't know where it is or if it'll work.  My network is quite unusual. :guitar:

---

### Post by costing on 2008-10-08
Intrepid should help, it has the proper kernel version that has everything working by default. The installation CD didn't work for me a couple of weeks ago (unsatisfied packages dependencies...), but maybe that is fixed now and you can already install it. I would give it a try since the alpha/beta tags don't apply to the software packages themselves.

---

### Post by Keymaster on 2008-10-08
I wonder if I'll have to change that SATA bios setting still with Intrepid.  When I change it to compatible it causes Vista to crash, and I don't want to reinstall Vista again :(  However Hardy 64 installed last time I tried it without changing that, but I never got drivers working, cause it was before I found all these walkthroughs.  What do you think will work out of the box with Intrepid?

---

### Post by costing on 2008-10-08
Yes, changing the SATA mode will cause Vista to crash. It doesn't matter the direction though, "enhanced" -> "compatible" or "compatible" -> "enhanced". It looks like with Vista you are stuck with the setting from when you installed it.

When I get home I'll try to boot with the BIOS setting put to "enhanced" and I'll let you know if it works or not. Since it's the same kernel as in Intrepid it should be a good indicator of what to expect from it.

---

### Post by Keymaster on 2008-10-08
Thanks.  I'm looking forward to the results.

---

### Post by costing on 2008-10-08
I've played a bit with the BIOS settings and it seems that:
- Enhanced mode works fine with 2.6.27-rc
- You can switch Linux from Enhanced to Compatible and back without problems
- Vista doesn't boot when you change SATA mode from what it saw at installation
- Enhanced mode seems slower than Compatible in Linux (copying a large set of files to /dev/null takes ~28sec/file in Enhanced vs ~22sec/file in Compabile). 

So, you could switch to Compatible just for installing Ubuntu in case you have problems at installation, make it run the latest kernel then switch back to Enhanced so that Vista can survive without changes.

---

### Post by Keymaster on 2008-10-08
Out of curiosity how large were the files you were testing this with?  (I want to cross reference your results with a test of my own, so any details you have as far as file size/type/partitioning would help)  Also with Vista I tried playing with Startup Repair after switching to no effect, so I'm not sure what exactly causes that mode change to crash it.  I'm glad to see the new kernel works in either mode, but I remember when using the x64 disk 8.04 Desktop installed without me switching modes.  I only learned of the mode change after seeking help here.  I can't wait for Intrepid final :-D

---

### Post by costing on 2008-10-08
Standard 350MB files ;)

Linux partition is 120GB, reiserfs (notail,noatime).

Test was:
for a in *; do time cp $a /dev/null; done

The set of files should be larger than the physical memory otherwise you don't measure the disk performance, if you run it more than once after a reboot.

cp is not very efficient but it's probably good enough for relative measurements. dd with bs=1M is a bit faster, or you can use iometer for more advanced benchmarks.

---

### Post by Keymaster on 2008-10-08
Thanks.  I'm curious, why ReiserFS instead of ext3?

---

### Post by costing on 2008-10-08
Old habits die hard ... ext used to be a crappy fs. Now I would've chosen xfs (just because Hans is AFK for a long time) but the Kubuntu installer just failed to install grub at the end when using xfs. It looks like there are still some bits missing from the right places. Rumors are that ext is now pretty good, if you get over fsck taking a lifetime to finish on large partitions and the mandatory full check every now and then (when you need your laptop the most of course).

---

### Post by Keymaster on 2008-10-08
I see.  I just use ext3, and change the options on the mount to check it every 400 mounts instead of 26 ;)  Not sure how to do that manually, but webmin makes it easy.

Edit: My friend who knows more than I do convinced me to use ReiserFS on my servers, and it's making it hard to put quotas on certain folders since I'm not sure how to convert blocks to MBs. (An admin with horrible math skils?!? lol)

---

### Post by Grabster22 on 2008-11-05
MY laptop is a asus g50v, and i cant seem to be able to get the wireless capability to work on it... is there a button i have to press to enable it?  The internet and router are fine, its just my laptop that isnt working.  Is there a guide online or could you just tell me what to do?

---

### Post by Grabster22 on 2008-11-05
This totally sucks, i know i have to press F2 but i dont know what the 2nd button is, god damn,\

Dont be a smart *** and say read the manuel, cause i threw that out the first day.  That was 2 months ago

---

### Post by Grabster22 on 2008-11-05
nevermind, i found the button and turned off the wireless (it was off the whole time)  


My conclusion: ASUS IS A PEICE OF JUNK AND IM NEVER BUYING 1 EVER AGAIN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by costing on 2008-11-05
I guess Fn+F2 is indeed very hard to find, and it's something that only ASUS has ... Better luck with your next laptop, maybe it will come with the mind-reading module that only ASUS doesn't have yet!

---

### Post by stabby on 2009-02-05
I have G50V and Fn+F2 didn't work, but my wifi is Atheros. What did work instead was pulling terminal up and typing:

#   sudo su
#   echo 1 > /sys/devices/platform/asus-laptop/wlan

For intel card there's some info here:
[http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/](http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/)

Hope this helps

---

### Post by felixnine on 2009-02-25
i'm thinking of picking up a g50vt-x6, which i presume is reasonably similar to the a1. now that ibex has been out for a while (and jaunty looms), has anyone had any better experiences with out-of-box functionality?

---

### Post by costing on 2009-02-25
Network (wired and wireless) as well as sound work fine with the default kernel in 8.10. The SATA enhanced mode works well, at least once the system was installed, but it will probably work also during installation.

I'm not sure if you still have to remove the ACPI event handlers to get the wifi fully working ... But this is only 5 seconds hacking that you might need to do.

Anyway, I'd go for it, it's a nice piece of hardware :)

---

