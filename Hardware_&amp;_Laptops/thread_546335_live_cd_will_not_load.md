---
title: "live cd will not load"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by Anacranom on 2007-09-08
I tried to get my brother into Ubuntu, my home desktop and work laptop installed (dual-boot) smoothly. just after the initial boot screen with the options to install, check cd, etc. the screen goes greyish white and nothing after that as far as graphics, i did hear the drums as it loads the live desktop... I just figured it was because it was a new laptop (Vista) and Ubuntu didnt have driver support, well i just bought a new (refurb) laptop with win XP MC and tried to install Ubuntu and same result, tried the different res, and the install for AMD 64, same result, am downloading the alternate cd now but not sure i know enough command line to do it right. I want to be completely windos-free by the end of the year but i run my own business and need this laptop to run Ubuntu as fantastically as my home desktop. Any and all help will be greatly appreciated.

System as follows:
Averatec 7100 series
AMD Turion 64 X2 TL-50 Dual Core
1024 DDR2 533mhz RAM
100 GB HDD
Nvidia GeForce Go 6100
Windoz XP Media Centre (partitioned to 50 GB, rest is aside for Ubuntu)

---

### Post by merlinus on 2007-09-08
Video card issues.  The Alternate text-based install cd is straightforward, and has menus.

Be sure at the partitioning menu to select the space you have set aside for ubuntu.

-merlin

---

### Post by Anacranom on 2007-09-08
Thank You for the reply, I will try that and reply here if that doesn't do the trick, Thanx again.

---

### Post by merlinus on 2007-09-08
You are most welcome.  Glad to help.

Nothing that you do, in terms of partitioning, will be written to disk until you select that option, so feel free to experiment.  You can use the Back feature to return to previous screens.

-merlin

---

### Post by Anacranom on 2007-09-08
i already partitioned the HDD with Partition Magic, so the space is there and waiting. Is already in ext3 format as well.

---

### Post by merlinus on 2007-09-08
Excellent,  It should go smoothly.  You will need one partition for / (root), and about 1.5G partition for /swap.

If you have enough space, you might consider creating a separate partition for /home, which is where configurations, settings, preferences, email, bookmarks and such live.

Then if you reinstall or upgrade, those will remain intact.

-merlin

---

### Post by Anacranom on 2007-09-08
I wish i knew how to add a partition for the home folder, I kinda do that in windows but i am still learning linux and Ubuntu has made it very easy for me.

---

### Post by merlinus on 2007-09-08
Make space in the partition you set aside for /home.  / needs about 12-15G, swap 1.5G, and give the rest to /home.

You will be able to do this at the partitioning menu, specifying how much space for each and selecting a mountpoint (e.g. /home).  

Just do not format your windows partition!

-merlin

---

### Post by Anacranom on 2007-09-08
so...
mnt point / gets 15g, swap gets say 3 g, and the rest set to mount point /home? is it that simple?

---

### Post by merlinus on 2007-09-08
You do not need more than 1.5G for swap.  And yes, it should be that simple.

If you are wanting to set up a shared partition for data that can be accessed from both windows and ubuntu, then give 10G for /home and create yet another partition for sharing.

It can be formatted as ext3 as well, since you can install drivers wo windows can read and write to it.

Not trying to be confusing..... but wanting to offer you lots of options.

:)

-merlin

---

### Post by Anacranom on 2007-09-08
man, I wish i lived next door to you, in 20 minutes i could get up to speed with this and be rollin on down the road and be able to help others to get there too. Just as a side note, I have my shop PC also dual-booted with ubuntu and when a customer needs files backed up from a corrupt hard drive (windows) and windows will not read it, i boot in Ubuntu and can pull all their docs/pics/personal files for back-up and they are happy again, where-as before i had linux i had to refer them to Seagate recovery systems. I do have to do a permissions conversion as mentioned on my site, [http://wood-bee-co.com](http://wood-bee-co.com), because most of the time it will tell me that access is denied to copy even though i can see it. BTW, been trying to download the alternate cd,, keeps hanging at 35%, even  tried differrent servers/mirrors and on 2 different PCs, hmm.

---

### Post by Anacranom on 2007-09-08
man, I wish i lived next door to you, in 20 minutes i could get up to speed with this and be rollin on down the road and be able to help others to get there too. Just as a side note, I have my shop PC also dual-booted with ubuntu and when a customer needs files backed up from a corrupt hard drive (windows) and windows will not read it, i boot in Ubuntu and can pull all their docs/pics/personal files for back-up and they are happy again, where-as before i had linux i had to refer them to Seagate recovery systems. I do have to do a permissions conversion as mentioned on my site, [http://wood-bee-co.com](http://wood-bee-co.com), because most of the time it will tell me that access is denied to copy even though i can see it. BTW, been trying to download the alternate cd,, keeps hanging at 35%, even tried differrent servers/mirrors and on 2 different PCs, hmm.

---

### Post by merlinus on 2007-09-08
Patience furthers.  Busier on the weekend.

If you post the permissions problem here, I may be able to help.

-merlin

---

### Post by Anacranom on 2007-09-08
Update: downloading the alternate cd ISO, is at 43% this time, maybe just heavy traffic on the ftp server...

---

### Post by Anacranom on 2007-09-08
i have the "NTFS" convert tool on my work desktop, and that works well, as linked to on my website

---

### Post by samb0057 on 2007-09-08
would you guys mind posting some of this stuff on ubuntuhcl.org? Signups are increasing, but we still need more constributions.

UbuntuHCL.org is a hardware compatibility list for ubuntu.

---

### Post by Anacranom on 2007-09-08
Merlin would be be better than Myself, as i am just muddling thru this at the moment, i am learning more and more each step but I am not yet able to offer any help other that the probs i have run into, I will be learning more of the structure so I can determine the cause/effect solutions but right now i am not qualified, and wouldn't want to give false hope when others like Merlin have far more knowledge than myself. I will however post all solutions on my website.

---

### Post by Anacranom on 2007-09-08
OK, Update, downloaded the alternate, booted the disk, got to the "Install in text mode" hit enter and same hapened, screen went to kernel loading, and all went grey/white. and nothing further. do i need to disable APIC?

---

### Post by Anacranom on 2007-09-08
OK, that did not work, got an error in the install, and apparently had already written to the boot sector, had to use recovery  to get the win os back, not a good sign. I will give all info if i know what is needed but Ubuntu is not loading on this laptop. all help is appreciated and i am sorry that i am not more knowledgeable on linux

---

### Post by merlinus on 2007-09-08
Did you checksum the .iso?  Info here:

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

Did you check the cd for errors?  There is an option to do this at the opening menu.

Did you burn at 4x or less?

Also, post system specs.

-merlin

---

### Post by Anacranom on 2007-09-08
I did not check disk for errors,
and i posted sys specs in first post:
System as follows:
Averatec 7100 series
AMD Turion 64 X2 TL-50 Dual Core
1024 DDR2 533mhz RAM
100 GB HDD
Nvidia GeForce Go 6100
Windoz XP Media Centre (partitioned to 50 GB, rest is aside for Ubuntu)
i am in process of reloading the sys with the restore disc provided with the new laptop software that created a restore dvd on first boot,,, and i did not burn the alternate cd at 4x or -...

---

### Post by Anacranom on 2007-09-08
as soon as the original config is operational, i will boot off of the cd and do the check for errors, but right now have been in the "Image restoration" phase for 35 minutes and at 48%, so I assume all thet i have  added since the creation of this disk is gone, no worries there- as i save all externally.

---

### Post by merlinus on 2007-09-08
Keep on keeping on....

I look forward to the next installment of the adventure.

-merlin

---

### Post by Anacranom on 2007-09-09
Well, the cd checks out ok. I've restored the laptop back to factory settings from the the restore disk. Starting over withe the alternate cd, 1st time got the greyed out screen just after choosing install, tried again this time changed from vga to 1280x1024---> got the language screen, and the keyboard layout, now giving me a msg "Your network is probably not using DHCP..." Yes it is but oh well! gets to "setting up partitioner..." choose manual,,, guided resize... RESIZING PARTITION,,, Installing the base system...  OK, finished the install Successfully, now get the grub loader,,, option for Ubuntu or windows,, ubuntu and goes to grey/white screen

---

### Post by merlinus on 2007-09-09
Boot into recovery mode.  At the prompt:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

---

### Post by Anacranom on 2007-09-09
I HAVE GUI!

It does recognise my Vid card,, but this averatec has "AveraBrite" i think was interferring,, maybe. I use "Envy" to load the nvidia drivers

---

### Post by Anacranom on 2007-09-09
OK, weird, didn't realize till now but it auto logged me in as root,tried to switch users and says thet GDM not running, running xserver, not gdm, so in a terminal i typed "/etc/init.d/gdm start" and got the msg about x already running do i want to try to run another,, ok, in root there is no network so cant install the correct vid drivers.. not sure what to do here if it wont load gdm. just black screen with the circle timer running- trying to load gdm i guess

---

### Post by merlinus on 2007-09-09
Try restarting in normal mode.  Running recovery mode automatically logs you in as root so you can make system changes.

Also, back up /etc/X11/xorg.conf once it is working so you can revert, if need be, before trying envy.

---

### Post by Anacranom on 2007-09-09
Nope, booting normally is the grey/white scree, can hear the drums for the log-in screen but no graphics :-(

---

### Post by Anacranom on 2007-09-09
I boot into recovery and startx, works fine, i have desktop and all things root,,, not sure how to proceed from here.

---

### Post by merlinus on 2007-09-09
Take a look at /etc/X11/xorg.conf to see what video driver is listed.

Here's mine, for a matrox card, just so you know in which section to look:

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "mtx"
    BusID        "PCI:1:0:0"
    Option        "OldDmaInit"        "True"

---

### Post by Anacranom on 2007-09-09
here's the section- this is working,, the trouble is with GDM, so i can log into main user to get network/internet,


Section "Device"
    Identifier    "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
    Driver        "vesa"
    BusID        "PCI:0:5:0"
EndSection

---

### Post by Anacranom on 2007-09-09
here is the xorg.conf from this (desktop-home PC):

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "GeForce 7300"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7300"
    Monitor        "Generic Monitor"
    DefaultDepth    24

---

### Post by merlinus on 2007-09-09
So when you start up nomrally via grub, what happens?

---

### Post by Anacranom on 2007-09-09
Get Grub choices, start normally, says starting up, and something,, "timer not connected, flashes too fast then the screen goes grey and thats it, well i do hear the drums when the log-in screen apparently comes up back there somewhere, and i can even successfully log in, well i can hear the drums again after i blindly type un the user name and password

---

### Post by merlinus on 2007-09-09
At grub menu press e, arrow down to the kernel line, press e again.

Delete quiet and splash.  

Press Enter, then b to boot.

This will show you what is going on during startup, and perhaps indicate the problem.

---

### Post by Anacranom on 2007-09-09
ok, the part that flashes by,,, "MPBios bug: 8254 Timer not connected to IO APIC...
Loading... " about a half of a second then grey screen

---

### Post by merlinus on 2007-09-09
Following the above instructions, add

noapic apic=none

to the end of the kernel line.

---

### Post by Anacranom on 2007-09-09
havent done the last yet, all i did was the delete and it BOOTED!, i have log-IN!

---

### Post by Anacranom on 2007-09-09
Still have not done the last addition to kernel,, but how do i save this, or will i have to delete everytime?

---

### Post by merlinus on 2007-09-09
If it works, you can edit the kernel entry in /boot/grub/menu.lst to make it permanent -- until the next kernel upgrade,  :)

---

### Post by Anacranom on 2007-09-09
I am replying from the laptop in Question! :-)
I will attempt to edit the menu.lst. as i do have to delete every time. 

Thank you so much for all the help and patience, now to battle with the nVidia card! 

(says dependencies..."Envy" is an application written in Python which will download the latest Nvidia driver or the Legacy driver (for older cards) (according to the model of your card) from Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to use the driver on Ubuntu Linux.

Says : Error:Dependency is not satisfiable: xserver-xorg-dev

but i will work on that,,, now to figure out a faster way of installing this so my brother can do it (the original prob was on his laptop, mine just did the same). Any way, now that I can Play COH on my desktop with the help of Cedega, i don need windoz for anything! i run my business Database on here and all is good, No more paying M$ thru the nose.

---

### Post by merlinus on 2007-09-09
Great news!  Well-done....

Upon install on a similar machine, boot from the live cd, press F6 at the opening menu, and you will be able to add those parameters to the boot line.

Keep us posted on how you do with getting the correct drivers for your video card.  Envy usually works very well..... excpet when it doesn't.   

:)

---

### Post by Anacranom on 2007-09-09
how do you edit/save in vi, or is there a better way to do, has to be root though?
I opened a terminal, 
´&#347;udo vi /boot/grub/menu.lst´
scrolled down to the line in the first menu, the kernel line, edited it, but cant save it?

---

### Post by merlinus on 2007-09-09
You like torturing yourself?

```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by Anacranom on 2007-09-09
*Evil Laugh*

what is the ¨gk¨ in gksudo?
I gonna go thru this thread copy/pasteing into notes so i can post on my website, obviously this is the 2nd time ie run into it, there must be others with same issues.
How do i uninstall this ubuntu, think thats 1 of many things i dont know how to do. i may uninstall and try the live cd like you suggested, but in any case i want to make a walk-through for this problem and post that on my site.

Again, Thank you for all the help!
Shawn

---

### Post by Anacranom on 2007-09-09
hey!  i just thought of something,, in the menu.lst, if i put the windows first, will that change the default load to windows? Just a thought for brother.

---

### Post by merlinus on 2007-09-09
Yes, but be sure to put it before

### BEGIN AUTOMAGIC KERNELS LIST

This will also place it at the beginning of the list of grub menu options.

---

### Post by merlinus on 2007-09-09
> **Anacranom said:**
> *Evil Laugh*

what is the ¨gk¨ in gksudo?
I gonna go thru this thread copy/pasteing into notes so i can post on my website, obviously this is the 2nd time ie run into it, there must be others with same issues.
How do i uninstall this ubuntu, think thats 1 of many things i dont know how to do. i may uninstall and try the live cd like you suggested, but in any case i want to make a walk-through for this problem and post that on my site.

Again, Thank you for all the help!
Shawn

gk prefaces sudo command for graphical apps.

You can uninstall by reformatting the ubuntu partition, and restoring windows bootloader to the mbr.

More info here:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Glad to help.  The most important things are that you got it working, and learned enough in the process to assist others.

---

### Post by Anacranom on 2007-09-09
yes, thanx again. I still have to ¨e¨ at the grub loader every time but all is working great. That is the way i had ¨un-installed¨ it before just thought there was an uninstall option somewhere. Hey, I wish you could visit my site once in a while and maybe post some good Ubuntu stuff there, I just started it so lots to do but could use all the help i can get. Anyway, stop by anytime- [http://www.wood-bee-co.com](http://www.wood-bee-co.com)

Thanks for EVERYTHING!
Shawn

---

### Post by merlinus on 2007-09-09
> 
I still have to ¨e¨ at the grub loader every time


Did you edit the applicable kernel line in /boot/grub/menu.lst?

---

### Post by Anacranom on 2007-09-09
yes, but did not keep the settings, went back and repeated the process and this time chose save-as, and replaced the file, works now, Thanx!

now trying to get Cedega and Crossover working, nothing on this laptop is going as smoothe on my desktop.

---

### Post by merlinus on 2007-09-09
But ah, the opportunities for learning!

:popcorn:

---

### Post by Anacranom on 2007-09-09
what does this mean?:

wbcadmin@ubuntu:~$ sudo sh install-crossover-standard-6.1.0.sh
Password:
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/wbcadmin' directory does not belong to you.
Point $HOME to your home directory and try again.

---

### Post by merlinus on 2007-09-09
Is wbcadmin your regular login id?

---

### Post by Anacranom on 2007-09-09
I use crossover to run M$ Access database for my business (wine wont do it) untill i can figure out the Open Office DB and convert, I have no clue how at this point.

---

### Post by Anacranom on 2007-09-09
> **merlinus said:**
> Is wbcadmin your regular login id?

Yes, that is the only user (other than root)

---

### Post by merlinus on 2007-09-09
Did you try running the command without sudo?

---

### Post by Anacranom on 2007-09-09
wbcadmin@ubuntu:~$ sh install-crossover-standard-6.1.0.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
/home/wbcadmin/.setup9486: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.5
Check the system requirements at:
[http://www.codeweavers.com/products/cxoffice/requirements/](http://www.codeweavers.com/products/cxoffice/requirements/)

You might be missing the 32bit compatibility libraries

thats what i got without sudo

---

### Post by merlinus on 2007-09-09
Says you are missing needed libraries.  Follow directions....

Also, are you running all this from your /home directory?

---

### Post by Anacranom on 2007-09-09
well did all that, still fail, i think its because its a 32 bit system and i running a 64 bit amd, will look more but didnt see a 64 bit choice on their downloads,,, looking

---

### Post by Anacranom on 2007-09-09
yes, home dir... /home/wbcadmin

---

### Post by Anacranom on 2007-09-10
well, So long and thanks for all the fish. I guess I'm up and going as much as i can be till I figure out what else to do differently. let me know if you discover a easy fix or an updated version. [email]shawn@wood-bee-co.com[/email]. And visit the site when you can.

---

### Post by merlinus on 2007-09-10
Glad to help, and keep in touch via PM if nothing else.

I will have a look at your website sometime next week.

I try not to run commercial apps at all, except for one that will not even run in a VM.

All the best...

---

### Post by Anacranom on 2007-09-12
Hey merlin, if you're still there, have a question, just tryin to write the walk-thru for this problem. Ok, boot from live cd, "e" at the boot menu- delete the 2 values, continue to the desktop where the option to install is... (Not the alternate cd) and choose to install. then after install,,, i assume you can "e" again and do the same, then once fully loaded do the [gksudo gedit /boot/grub/menu.lst]  and make permanent. 

That sum it up?
Thanx bro!

---

### Post by Anacranom on 2007-09-15
how do i uninstall Ubuntu now that its in the mbr, so i still have windows? i want to re-do the whole process to make the best walk-thru for this issue.

---

