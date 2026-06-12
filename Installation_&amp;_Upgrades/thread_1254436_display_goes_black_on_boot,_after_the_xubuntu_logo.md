---
title: "display goes black on boot, after the xubuntu logo and loading bar, please help"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-08-31
hello all

as explained in this thread,
[http://ubuntuforums.org/showthread.php?p=7875287#post7875287](http://ubuntuforums.org/showthread.php?p=7875287#post7875287)
i think i've managed to install xubuntu jaunty on a kohjinsha SA1F00 mini pc.
yet something is wrong with the display. when i try to boot, after the xubuntu logo and the starter bar, the screen goes black.
i've tried the "automatically resolve graphics option", but to no avail.
i tried booting to GParted to see what the partitions looked like, but the graphic mode didn't work (the screen wasn't black though, just a display issue)

how can i fix this ? i have no clue as to what to do next, and do not know how to use the command lines to reach the xorg etc...

can somebody help me out ? i'm totally stuck

thanks in advance

ben

---

### Post by bjaz on 2009-09-01
sorry to be insistant, but i'm completely stuck here. this forum is pretty much my only hope of getting this machine to work, especially since windows doesn't work anymore and there is no CD to reinstall from, just a licence.

 is there anything i can do to check that xubuntu is properly installed, and eventually fix the graphic display mode ? 

thanks in advance for your help

ben

---

### Post by bjaz on 2009-09-01
I really need help with this.

if there is another place where I should ask, or look into, please let me know. as of now i'm just sitting with a useless machine on my hands, trying to find info online to no avail.
about to try to download a japanese windows xp and renistall it, don't even though if this will work though.

since the xubuntu command line display works, i'm sure something can be tried... i hope so anyway.

all the best

b

---

### Post by PaulReaver on 2009-09-01
hi I'll try to help if I can. Could you explain in as much detail about your problem as you can.
also could you explain exactly what you were doing before it broke.

from your post i gather that it is probably X that is failing to start
can you log in on a console?

could you post a copy of your /etc/X11/xorg.conf

---

### Post by PaulReaver on 2009-09-01
sorry did'nt read your post properly.

to edit your xorg.conf file in a terminal you want to type

sudo nano /etc/X11/xorg.conf

it'll ask you for your password and will open a very basic text editor.

---

### Post by bjaz on 2009-09-01
thank you so much for your answer.
the only thing i did was try to install xubuntu. i think it actually did install, but there is an issue with the display setting, which causes the screen to go black on booting, after the xubuntu logo and loading bar.
i'm trying to install ubuntu now, in safe graphic mode. first try didn't work, but this attempt seems to be working.

 we'll see if it can boot or not, after the install.

i chose a "side by side" install. 

apparently xubuntu was installed, since the partition table contained a 20Gig ext3 ubuntu partition. I wonder why the previous install messed up the japanese windows partition's boot.

---

### Post by PaulReaver on 2009-09-01
try this first 
in a terminal


sudo dpkg-reconfigure xserver-xorg


that'll configure your xserver. if that does'nt work i'll try help you edit your xorg and install the graphics card drivers.:P

---

### Post by bjaz on 2009-09-01
ah well. the new installation seemed to have gone  well,  (ubuntu 9.04), meaning I should now have ubuntu 9.04 and xubuntu on the machine.

yet at first boot i get "grub loading, please wait", then Error 18....

I no longer have booting options to choose upon start up.


how do i open a terminal in this case ?

---

### Post by PaulReaver on 2009-09-01
Grub error 18
the selected cylinder exceeds the maximum cylinder value supported by the bios.


did you install grub to the master boot record.
or a partition 
it, it ideally should be installed as near to the beginning of the hard disk as possible 

there may be a compatibility option for the hard disk in the bios settings.

either that or you've hosed it mate.

---

### Post by bjaz on 2009-09-01
thanks.

i'm reinstalling xubuntu. deleted the 2nd ubuntu partition and swap i'd just created, formated the former xubuntu part, ext3, mounted to /, reinstalling on it, in safe graphic mode.

now the partitioning table consists of 2 ntfs windows partition, plus on ext3 root and one swap. we'll see how this goes with the grub

---

### Post by PaulReaver on 2009-09-01
I hope your install goes well for you.
sorry I'm knackered. I'm off to bed.

but just in case you end up at a terminal again looking at a black screen

first thing to do if your display does'nt work
in a terminal type 
sudo dpkg-reconfigure xserver-xorg
and set framebuffer to yes and display to vesa

then type 
"startx" to start your x server



if that does'nt work try this in a terminal

sudo nano /etc/X11/xorg.conf

to edit your xorg.conf to look Exactly like this:



Section "Device"
Identifier "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "vesa"
SubSection "Display"
Depth 16
Modes "640x480@50"
EndSubSection
EndSection



ctrl x to exit and save it



then type 

"startx" to start your x server


After you get your Display working here are the drivers for the other bits
[http://www.kohjinsha.com.sg/products/drivers.htm](http://www.kohjinsha.com.sg/products/drivers.htm)

good luck

---

### Post by bjaz on 2009-09-01
it worked ! i'm really stoked because i'd been fighting with the machine for a while.
the re-install in safe mode worked, the graphics are fine and the wireless works out of the box.
looking into the other functions

---

### Post by bjaz on 2009-09-02
ok, so everything is working fine now.

the only slightly alarming aspect is that I cannot read multimedia files. I'm a little surprised because when the windows side was still working it worked fine. the machine has a 500mhz AMD geode processor and 512mb of ram.

i tried to open files (movies, mp3's) with VLC but that did not work. On the built in "movie player", i get sound, but only still images.

looks like i'm going to have to try and repair the windows side of things for multimedia applications, which is a disapointement.
unless something can be done to make the most out of xubuntu

ben

---

### Post by PaulReaver on 2009-09-02
have you tried to install the lib 's for playing these formats.

it should be able to play these.
i can play videos fine when i scale back my atom processor to save battery

---

### Post by bjaz on 2009-09-02
thanks for your help.
 I thought it should be able to play them as well.
I haven't installed the librairies and i'm not really sure how to do so, since i thought most came bundled in with xubuntu. I only did the upgrades and installed vlc player.
is there a simple way to install most of the most commonly used ones for sound and video files ?

I also realized the display should probably be in 800 x 480, according to the specs, instard of 800x600.
 from what i remember, this has to be modified in root mode in the xorg conf file, is this correct ?

i tried editing the xconf, using the steps above, changing the display to 800x480. doesn't seem to have worked, the display is still in 800x600 in the display settings.

at the moment my xconf file looks like this

------------------

Section "Device"
Identifier "Configured Video Device"
Diver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Depth 16
Modes "800x480@50"
EndSubSection
EndSection

-------------

the main difference being this "configured video device". should i replace it to have this, ie what you wrote yet with the 800x480 res ?

Section "Device"
Identifier "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "vesa"
SubSection "Display"
Depth 16
Modes "800x480@50"
EndSubSection
EndSection

----------------------

thanks again

ben

edit ; i changed the xconf file for a 800x480 res.
i don'treally know if it worked, since the display settings still show 800x600, but i guess it's ok.

what should i do to install the libs for multimedia files :?

thanks

b

---

### Post by bjaz on 2009-09-03
i'm also wondering if the libs issue is why i can't what a flash video on you tube, despite having installed the firefox plugin. i hope this isn't the processor's fault, it's pretty slow at 500Mhz I guess.
i there anyway to get the multimedia aspect going with xubuntu on this 500mhz AMD geode with 512Mb of RAM box ?

---

