---
title: "Hoary 855resolution guide :)"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by wildcard on 2005-04-08
This is the definitive 855resolution guide for Hoary/Ubuntu, written with the novice in mind...

Using a terminal window, type in the following:

cd /etc/X11
sudo gedit xorg.conf

Make sure that you have modelines and display subsections that show your target resolution. My Dell 700m, on a fresh install, had the 1280x800 resolution already set. Yours may vary-since you're in here, you can add your target resolution in the display subection...

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection

And for your modelines...

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-90
        VertRefresh     50-160
        Option          "DPMS"
        Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828
        -HSync +Vsync

My theory is that X.org is a little smarter that XFree86, so you should have these already present and will not need to modify this xorg.conf file.

The 855resolution patch can be downloaded from here:
[http://perso.wanadoo.fr/apoirier/](http://perso.wanadoo.fr/apoirier/)

Save this file to your desktop, then extract it. I'd create a folder named 855rez in your /home/xxx directory (where xxx is the user account you're logged in as)

Go to synaptic package manager and install GCC-you'll need this for the install

Using a terminal window, go to the folder where you extracted the patch (/home/xxx/855rez if you're using my defaults). At the prompt, type in:

make

This will process the patch. At the next prompt type:

sudo make install

This will install the 855resolution files to the /home/xxx/855rez folder. At the next prompt, type:

sudo 855resolution -l

You will see a bunch of resolution modes. This is my output for reference:

VBIOS Version: 3104

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel
Mode 7c : 1280x801, 8 bits/pixel
Mode 7d : 1280x801, 16 bits/pixel
Mode 7e : 1280x801, 32 bits/pixel

As you can see I already have 1280x800 resolutions enabled. Choose a Mode that you will never use for sure, like a ridiculously high resolution that your monitor can't support, and run the patch against it. 
At your terminal prompt, type:

sudo 855resolution 5a 1280 800

What that will do is set mode 5a (the one I picked) to a resolution of 1280 800. If you need to set this to something different, use those values..for example, if your monitor is 1440x1000, your line should look like "sudo 855resolution 5a 1440 1000".

At your next prompt, rerun:

sudo 855resolution -l

Check to see that your new modeline is in place. If so, you can restart X windows by hitting the CTRL, ALT, and Backspace keys on your keyboard at the same time...your new resolution should now take effect.

You'll need to run this patch every time you boot, as the BIOS will forget it on reboot. Go to Applications/Text Editor and create a new document with the following line:

855resolution 5a 1280 800 (remember, my example is for the 1280x800 widescreen resolution)

Save this file as "startupscript" on your desktop.

Go into a terminal window again and type:

sudo cp /home/xxx/Desktop/startupscript /etc/init.d/startupscript

This will move the file to where it needs to be. At your next prompt, type in:

cd /etc/init.d

At your next prompt, type in:

sudo chmod a+x startupscript

This sets the script file with the correct permissions.

To have this run at boot, you'll need to use Synaptic Package manager to get rcconf (apt-get install rcconf). Once this is done, go back to a terminal and type:

sudo rcconf

You should see a window with a bunch of choices with * next to them. Scroll down, and you should see startupscript on that list. Use the spacebar to place * next to startupscript, then tab to OK and this should get you back to the terminal window.

Last (and this gets missed a LOT!),the applications in rcconf are loaded in alphanumerical order. Ubuntu's runlevel (used by rcconf) is 2, so at your terminal window, type:

cd /etc/rc2.d
dir

The dir command will give you a list of files, all with names like S00nameoffile. Take note of where the GDM line is. On Hoary 5.04 live, mine shows as S13gdm. Your startupscript file should be in here too, probably as S20startupscript. The issue is that your script needs to run BEFORE GDM starts! To do this, note where the Sxx gaps are...if you go from S05 to S10, you have a range to work with...At your terminal window, type in:

sudo cp /etc/rc2.d S20startupscript /etc/rc2.d S09startupscript

This will place a copy of your startupscript BEFORE GDM in the boot order. If you run:

dir 

from the terminal prompt, you should now see your S09startupscript in the directory list.

At this point, restart Ubuntu. While all the verbose parts of your kernel are loading, you should see a line about 855resolution and patch applied to 1280 800 (or whatever target resolution you were gunning for...).

Enjoy!

---

### Post by desiboston on 2005-06-03
Everything worked like charm except the last part.

shiv@ubuntu:~$ sudo cp /etc/rc2.d S20startupscript /etc/rc2.d S09startupscript
cp: `S09startupscript': specified destination directory does not exist
Try `cp --help' for more information.
shiv@ubuntu:~$


please help....



I have to restartx after I log in and the resolution works fine

---

### Post by Sav on 2005-06-05
If you add in the repository list the universe and multiverse databases, you'll find the deb package of 855resolution.
It installs the script.
You have only to edit the configuration file to add the mode you want.

---

### Post by desiboston on 2005-06-05
This is my repository list: Kynaptic can't find it...
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by desiboston on 2005-06-05
So finally it worked, I installed manually. Everything looks cool BUT the fonts are too big, I made them small but still if I open the Openoffice half the screen is occupied by toolbars...what to do now? :-#

---

### Post by YenningComity on 2005-06-21
Ok two things one when you go to copy the link in the final step should the resulting file S09startupscript be a link like the original was?

And two can someone with a dell 700m post their xconfig i broke mine so x no longer starts up.

---

### Post by Kingedgar on 2005-06-21
Couple questions...

1 What is 855resolution?

2 I have a D600 dell, only goes up to 1024x768 does that hinder me if I decide to install this?

---

### Post by banditti on 2005-08-02
cd /etc/rc2.d
mv S20startupscript S09startupscript

That should do it, it did for me.

---

### Post by melon on 2005-08-06
IMHO it would be more elegant to create symlinks to the **rc[0-6].d** directories and leaving the original script in **/etc/init.d**

Anyway, thanks for the HOWTO it worked for me as well. :)

---

### Post by ad noiseam on 2005-08-10
Dumb me, I installed this by mistake (it doesn't work with my setup). Now, how do I uninstall it? :(

---

### Post by slowwalk on 2005-08-10
I think it's now easier to download the debian unstable updated package at
[http://packages.debian.org/unstable/x11/855resolution](http://packages.debian.org/unstable/x11/855resolution)

install it: "dpkg -i 855*.deb"

and follow the instructions of the readme file:

* "sudo -s" to go root
* "855resolution -l" to see the modes that your VBIOS detects
choose the mode that you want to overwrite (a resolution which you will never use)

then edit the /etc/default/855resolution
and set 
MODE=(the mode which you want to overwrite)
XRESO...=new resolution width (1280 in my case)
YRESO...=new resolution height (800 in my case)

that's it, reboot or type "/etc/init.d/855resolution start"

NOTE:
for 915GM chipsets (Intel GMA900) only this updated version (>=0.4) from the debian unstable works.
(I previously suggested [http://www.debian.or.jp/~kmuto/855resolution/](http://www.debian.or.jp/~kmuto/855resolution/) which is outdated, forget it)

---

### Post by ahh_dee on 2005-08-15
I just installed a fresh dual boot system with Windows XP and ubuntu.  I am new to ubuntu and i am having trouble with setting up my resolution.  
i extracted the file into a different folder and and typed 

$make b

then i get this error

/home/dennis/Desktop/855resolution # make
cc -s -Wall -DVERSION='"0.3"' -DPLUGINS='plugin1,plugin2' -DREF_PLUGINS='&plugin1,&plugin2'    -c -o 855resolution.o 855resolution.c
make: cc: Command not found
make: *** [855resolution.o] Error 127


can someone help me?   thanks

---

### Post by nyheat on 2005-08-30
[QUOTE=ahh_dee]I just installed a fresh dual boot system with Windows XP and ubuntu.  I am new to ubuntu and i am having trouble with setting up my resolution.  
i extracted the file into a different folder and and typed 

$make b

then i get this error

/home/dennis/Desktop/855resolution # make
cc -s -Wall -DVERSION='"0.3"' -DPLUGINS='plugin1,plugin2' -DREF_PLUGINS='&plugin1,&plugin2'    -c -o 855resolution.o 855resolution.c
make: cc: Command not found
make: *** [855resolution.o] Error 127


can someone help me?   thanks[/QUOTE]
to fix that problem you need to install GCC
go to System>Synaptic Package Manager > GCC
right click and select Mark for installation


Thanks a lot for the guide, I am new to Linux myself but after some persistence I got it to work. 

One thing that needs to be mentioned however is that I didn't find rcconf listed in Synaptic Package Manager, so I had to find th .deb package manually and install it myself

---

### Post by strongmantim on 2005-10-23
Dear God I am glad there are people who are smart than me. Lots of people. 

So far, I'm moderately impressed with Ubuntu. Wifi worked out of the box. Startup is rather long. 1280x800 resolution is now working (WOOHOO!). Now I need to get DVD, MP3, and multimedia working. Looks like my Sunday will be spent in the forums changing "moderately impressed" to "OMG WTF TH15 15 t3h \/\/1|\|!!!"

(BTW, I had to follow Banditti's instructions to use "mv S20startupscript S09startupscript" but I also had to put "sudo" in front of it. If one were to modify Wildcard's final instruction to be "sudo cp /etc/rc2.d/S20startupscript /etc/rc2.d/S09startupscript", would that work? I think it would. Wildcard probably just had a typo towards the end of a long and insanely helpful post.)

---

### Post by sroets on 2006-01-15
[QUOTE=nyheat]to fix that problem you need to install GCC
go to System>Synaptic Package Manager > GCC
right click and select Mark for installation


Thanks a lot for the guide, I am new to Linux myself but after some persistence I got it to work. 

One thing that needs to be mentioned however is that I didn't find rcconf listed in Synaptic Package Manager, so I had to find th .deb package manually and install it myself[/QUOTE]

I did install GCC, but this is the error that I get when running the make comand:

cc -Wall -I`pwd` -DVERSION='"0.4"' -DPLUGINS='plugin1,plugin2,plugin3' -DREF_PLUGINS='&plugin1,&plugin2,&plugin3'    -c -o 855resolution.o 855resolution.c
855resolution.c:14:19: stdio.h: Onbekend bestand of map
855resolution.c:15:20: stdlib.h: Onbekend bestand of map
855resolution.c:16:20: string.h: Onbekend bestand of map
855resolution.c:17:20: unistd.h: Onbekend bestand of map
855resolution.c:18:20: sys/io.h: Onbekend bestand of map
855resolution.c: In function `find_modes':
855resolution.c:31: error: `NULL' undeclared (first use in this function)
855resolution.c:31: error: (Each undeclared identifier is reported only once
855resolution.c:31: error: for each function it appears in.)
855resolution.c: In function `find_resolution':
855resolution.c:53: error: `NULL' undeclared (first use in this function)
855resolution.c: In function `list_modes':
855resolution.c:63: let op: implicit declaration of function `printf'
855resolution.c: In function `parse_args':
855resolution.c:79: error: `NULL' undeclared (first use in this function)
855resolution.c:81: let op: implicit declaration of function `strlen'
855resolution.c:99: let op: implicit declaration of function `atoi'
855resolution.c:101: let op: implicit declaration of function `fprintf'
855resolution.c:101: error: `stderr' undeclared (first use in this function)
855resolution.c:122: let op: implicit declaration of function `strtol'
855resolution.c: In function `main':
855resolution.c:140: error: `NULL' undeclared (first use in this function)
855resolution.c:160: let op: implicit declaration of function `iopl'
855resolution.c:161: let op: implicit declaration of function `perror'
855resolution.c:172: error: `stderr' undeclared (first use in this function)
855resolution.c:195: let op: implicit declaration of function `putchar'
make: *** [855resolution.o] Fout 1

can anyone help me out ???
thanks!

---

### Post by hriwo on 2006-01-15
This finally worked after I figured out I need to install make, This is a great help.


Thanks

---

### Post by shuttleworthwannabe on 2006-01-28
Thanks this worked perfectlly well fo rme.

---

### Post by spock2263 on 2006-01-31
Is this 855 only for Intel cards? I have the same resolution problem and I have ATI card, would it work for me? Sorry if I'm saying nonsence, I' new to linux and I have this problem for weeks and I can't figure out a way to solve it (please see
[http://ubuntuforums.org/showthread.php?t=121478](http://ubuntuforums.org/showthread.php?t=121478)) Thanks a lot

---

### Post by Xitanto on 2006-03-31
I have followed all the instructions in this thread to the letter, but my Ubuntu still doesn't work with 1280x800 resolution.

It does all the way until I am logged in, and then it reverts to 1024x768.

---

### Post by agyat on 2006-04-27
I used these steps before with breezy. It worked as gold till yesterday. Yesterday, I have my auto update on and it seems something got updated and resolution went back to 1024x768. Now If I the repeat the steps of changing the resolution in bios using

"855resolution 5a 1280 800" restarting  X then X crashes.

Any god like idea again...:-)

Ajay

---

### Post by danbert on 2006-09-18
I installed the 855resolution program but it would not overwrite the vbios settings.  I think this is because I have the Intel 955 graphics chip.  When I try and install the 955resolution package, it says that libc6 is not satisfiable.  However, Synaptic shows that libc6 is installed on my system.  What can I do to convince my computer that the dependancy is satisfied?

---

### Post by surhudm on 2007-01-02
I think the Modeline that has been written up here in the post is not valid for all the users.

So to get the correct Modeline one should go to
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Here you should put the values corresponding to your monitor. In case you do not know any of these values, then do the following:

bash# sudo apt-get install xresprobe

This installs the utility ddcprobe. 

Then

bash# sudo ddcprobe

This will lists the monitor capabilities. Note the dtiming. In my case it gave 1280x800@59

59 is the number that you should enter in the Modeline generator refresh rate. Change the resolution you want to 1280 800 and change no other values. Press enter or click on Get Modeline.

Copy the modeline into your /etc/X11/Xorg.conf in the Monitor section. Make sure you have the Mode 1280x800 in the Screens Section.

Follow the rest of the guide as it is... And it should work...

Surhud

---

### Post by LouisvilleLIP on 2007-05-10
I'm trying to fix the resolution on a Gateway 400VTX.  I've read several places that this laptop is a punk, but it has the 855 chipset, so I'm hoping this will work for me.

I made it to the part in this guide where you hit ctrl-alt-bksp.  If everything worked, I should have gotten the new resolution.  I didn't.  So, I'm stuck. 

This is my first real effort with Linux, so be gentle.

---

### Post by LouisvilleLIP on 2007-05-11
bump

---

### Post by LouisvilleLIP on 2007-05-11
bump

---

### Post by lenninct on 2007-06-09
help with the XPS M1210 by dell resolution to low,

---

### Post by nufyoot on 2007-08-05
I'm having trouble with my configuration.  I'm using a Samsung SyncMaster 920BW which is a 19" widescreen that supports 1440x900 @ 60Hz.  I'm also using an intel 865 integrated graphics card.  I've tried both 855resolution and 915resolution with no luck.  Every time I use either 855 or 915resolution I provide "sudo 855resolution 5a 1440 900" and I then restart X server, only to find my monitor saying that the current display is not supported and that the recommended display is 1440x900 @ 60 Hz.  Any ideas?

---

### Post by alekander on 2008-04-28
Hi all,

The first solution worked like a charm for my Acer Travelmate 660 and Ubuntu Hardy Heron. I was stucked with 1400x1050@56Hz! My LCD supports 1400x1050@75Hz. Now I can set higher refresh rates not detected before.
However I still have an issue. When suspending the system to RAM and restarting it later I guess the script is not loaded anymore, as the resolution goes back to 1280x1024@60Hz, which was a mode detected before the use of 855resolution, and there's no way to set it back right but restarting the computer. Where have I to hook the script to make it run after coming back from suspend mode?

BTW, it was supposed the Hardy Heron was going to be able to detect better the refresh rates but in my case it behaves exactly the same as Gutsy.

Thanks a lot!

---

