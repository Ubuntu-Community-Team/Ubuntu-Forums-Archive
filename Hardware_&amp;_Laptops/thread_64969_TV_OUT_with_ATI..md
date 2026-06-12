---
title: "TV OUT with ATI."
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-09-12
I dont have my fglrx drivers installed (cant figure it out)

So tv out was my next task...

I installed the gatos driver.
Then followed this



# Grab a X.org CVS snapshot from [http://xorg.freedesktop.org/snapshots](http://xorg.freedesktop.org/snapshots) :
wget [http://xorg.freedesktop.org/snapshots/xorg-x11-6.8.99.4.tar.bz2](http://xorg.freedesktop.org/snapshots/xorg-x11-6.8.99.4.tar.bz2)


# Grab a matching patch from [http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html) :
wget [http://megahurts.dk/rune/stuff/xorg_CVS-20050420-tv_output.patch.gz](http://megahurts.dk/rune/stuff/xorg_CVS-20050420-tv_output.patch.gz)

# Extract, patch and compile:
tar xjvf xorg-x11-6.8.99.4.tar.bz2
gunzip -c xorg_CVS-20050420-tv_output.patch.gz | \
  patch -p1 -d xc/programs/Xserver/hw/xfree86/drivers/ati
mkdir xc-build
cd xc-build
lndir ../xc
make World

#For Red Hat / Fedora Core users
#Remove your current X.org installation (Expect RPM dependency hell.)
rpm -e xorg-x11

# Install:
make install

# Edit your /etc/X11/xorg.conf according to
!!!!!!!!!# ./programs/Xserver/hw/xfree86/drivers/ati/README.out :  !!!!!!!!!!!!!!!!!!!!
# * Set the resolution to 800x600
# * In the "Device" section, add:
    Option "TVOutput" "PAL"     (or "NTSC", etc.)

# Start X and rejoice.
Xorg


I got to this "# ./programs/Xserver/hw/xfree86/drivers/ati/README.out :"

but dont know where this file is to read?? or how to read it ???

so i jsut edited the xorg file as the 2 lines below it said to .
It didnt work however... Does anyone know what is wrong

Do i have to have the fglrx drivers installed first ... I hope not...

---

### Post by mlomker on 2005-09-12
[QUOTE=floyd27]Do i have to have the fglrx drivers installed first ... I hope not...[/QUOTE]

Yes.  The fglrx driver has the tv-out feature built into it.  Those 'gatos' instructions actually had you reinstalling the X-server...a much bigger deal than just changing a driver!  I hope you didn't overwrite too many important files while trying that...

Read through [this thread.](http://www.ubuntuforums.org/showthread.php?t=64286&highlight=mlomker+ATI)

---

### Post by floyd27 on 2005-09-12
I didnt do any of the steps that said for redhat or fedora so i hope i didnt mess too much up,...
I just want to get it working then im gona re-install because i have been messing with alot of stuff and would just like to get it going ..

I read that post of yours and i ill give it a try..
one question..

i am assuming that the driver that was used by the guy you were helping is the ATI .rpm converted to the deb file...and not the one in the packages????
So do i use the LATEST off the ati site ...?
thanx

---

### Post by Granji on 2005-09-12
No you shouldn't use the latest, that's what I had been doing before it wasn't working, I had to take off all the fglrx packages that I had installed, through synaptic, using complete removal, and then take the steps to use the .rpm > .deb conversion and dpkg

---

### Post by floyd27 on 2005-09-12
Yes i understand that..
However that rpm package you got...where did you get it? the ati website?
Becasue that is waht i mean by the latest. the one from the ati website.. 

fglrx_4_3_0-8.16.20-1.i386.rpm

there are perviouse ati drivers with lower numbers in the file name.. 
Is it ok to use the latest from ati..?

if not which version of the "ati website" drivers should i use?
i would assume that the latest would be better, as the latest windows ati drivers had a significant improvment in performance  
thanx

---

### Post by mlomker on 2005-09-12
[QUOTE=floyd27]i would assume that the latest would be better, as the latest windows ati drivers had a significant improvment in performance  
thanx[/QUOTE]

Yup, the latest drivers will work best for most people.  There is a bug in the latest version for certain laptop owners...the driver works but you are stuck at 1024x768.  I had *that* particular problem myself and am running the slightly older version with 200 fps less performance.  That's okay, though...the huge icons would drive me bananas!   :grin:

---

### Post by floyd27 on 2005-09-12
thanx for the reply...
i have tried with no success for so long im hoping this one works for me...
im preping my system now to do it..
1 more qiuck Q if you dont mind..
the control center....
Will that come with the driver or do i have to add it seperate?
i have it kind now "its listed but doesnt work" i figure i will uninstall it along with everything else related to fglrx...

---

### Post by Granji on 2005-09-12
The control stayed for me, even after the fglrx uninstalls, it still doesn't show my cards proper name, but it does have the drivers loaded, and my 3d apps run awesomely.

---

### Post by floyd27 on 2005-09-12
on the ati site there are several downloads. 
xfree86 4.1,4.2,4.3
xorg 6.8

whick one woul;d i be interested in..
thanx

---

### Post by mlomker on 2005-09-13
[QUOTE=floyd27]on the ati site there are several downloads. 
xfree86 4.1,4.2,4.3
xorg 6.8
[/QUOTE]

Neither, it's Xfree 4.3.  Download [this one](http://www2.ati.com/drivers/linux/fglrx_4_3_0-8.16.20-1.i386.rpm), assuming you have the 32-bit version of Ubuntu.

FYI, I run amd64 and the ATI application doesn't even open...never has.  I use the command **fglrxinfo** in a terminal prompt to see what driver is running.

---

### Post by floyd27 on 2005-09-13
thanx..
I tried this on my friends comp last night with no progress.
However i think it may be his comp at fault..
I had gotten further on his before now it wont let me sh make-install.sh.
i installed the headers but no go.. then i lost the GUI all together , at which point i quit and left him on his own..(just until later today, i wouldnt be that bad a friend)
im gona try it on mine today...
if it doesnt work ill just re-install. and try with a fresh install....

not to sound ungreatful, but there are a few small typo's in your guide. I was able to get around them but someone new might not know why it doesnt work.. (mainly the .deb file need to be changed, it ends up being different from the .rpm it was made from)
but thanx for the help and ill keep trying.

---

### Post by floyd27 on 2005-09-13
sorry again...

the xorg.config file... You said that ..

"It matters a great deal--Ubuntu reads the xorg.conf file. If you used fglrxconfig to create the file then you need to rename it xorg.conf. You shouldn't be seeing anything about MESA when the proper driver is loaded."\

How would i not use the fglrxconfig to create the file, or how do i change the nome to xorg.config if i were to use it...
I have been using it the entire time ...
knowone has ever told me that this has to be done....
i think this is a MAJOR reason why me and most others cant get it to work....
thanx

---

### Post by floyd27 on 2005-09-13
Ok...
latest..

I did everything on the list.
I did not reboot (fear of losing GUI) 
i did not edit any config file or run fglrxconfig 

Do i need to run fglrxconfig? 
Do i need to rename the file? if so how?
Do i have to add fglrx in place of ati in the xorgconfig file?

everything went well till the end of your directions..I just need to know what to do now....

xorg.conf

roderick@ubuntu:/lib/modules/fglrx$ xorg.conf
bash: xorg.conf: command not found
roderick@ubuntu:/lib/modules/fglrx$   dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[fglrx] module unloaded - fglrx 8.16.20 [Aug 16 2005] on minor 0

fglrxinfo

roderick@ubuntu:/lib/modules/fglrx$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

dmesg | grep fglrx

roderick@ubuntu:/lib/modules/fglrx$ dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[fglrx] module unloaded - fglrx 8.16.20 [Aug 16 2005] on minor 0

---

### Post by floyd27 on 2005-09-13
I configured the xorg.conf file..done

I have a prob though
still didnt reboot becasue of this..


"Make sure that "find /lib/modules | grep fglrx | grep ko" reports that only one fglrx.ko exists, and that it is at /lib/modules/fglrx/fglrx.ko. Specifically, make sure there are is no fglrx.ko under /lib/modules/<kernel version>/. Those other modules under /lib/modules/fglrx are fine."


I have other fglrx's listed. and in the /<kernel version>
I moved the fglrx.ko file to the home folder.
<mv /lib/modules.../fglrx.ko $HOME>
but still have this and cant delete/move it at all.....

roderick@ubuntu:~$ find /lib/modules | grep fglrx | grep ko
/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd
/lib/modules/fglrx/build_mod/fglrx.ko
/lib/modules/fglrx/fglrx.2.6.10-5-k7.ko
/lib/modules/fglrx/fglrx.ko
/lib/modules/2.6.10-5-k7/kernel/drivers/char/drm/fglrx.ko

i dont know what is going on here at all???????

any ideas...

---

### Post by mlomker on 2005-09-13
I'm not sure where you're reading about moving the .ko file somewhere...those weren't in the thread that I referenced.  If you're going to use fglrxconfig then you need to rename the file.

From a terminal:

[b]
sudo 
cd /etc/X11/
cp xorg.conf xorg.bak
[/b]

Run this script [online fglrxconfig](http://www.objorkum.com/scripts/fglrxconfig/).
[b]
nano xorg.conf
[/b]

Paste in the output from the web form, Ctrl-X, Y to save. 

[b]
cat /etc/modules
[/b]

There should be a line that has fglrx on it.  If not, run this:

[b]
echo "fglrx" >> /etc/modules
[/b]

Ctrl-Alt-Backspace will restart your Xwindows session.  If it fails you can always copy the xorg.bak file back over the xorg.conf.

---

### Post by floyd27 on 2005-09-13
I did not run fglrxconfig.
i configured the xorgconfig....

so im assuming i dont have to do the latest steps you gave me...

i dont know how to use a backup file...I always backup, but like i said i dont know what to do with it so i just re-format everytime, thats why i HAVENT rebooted yet...

in the post i put above it says i cant have fglrx file besides the one i just installed and I DO so how do i get rid of them....?

i was with yea all the way until your last post , now im kinda lost.. I dont understand..

edit...

ok. i ran the script and copied the file..
when i do

nano xorg.conf
i get something in the terminal the says 

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell  

????????
is htis what im suppost to get?
or the regular config file?

---

### Post by floyd27 on 2005-09-13
sudo gedit xorgconfig

usually gives me the file with everything in it...
but now gives me a blank page?

---

### Post by floyd27 on 2005-09-13
finally copied that to the xorg.conf file




restarted..

LOST GUI.. back to square 1...

looks like a reformat..
i need to get rid of the other fglrx.ko files...
i bet thats the porblem....

---

### Post by mlomker on 2005-09-14
[QUOTE=floyd27]i need to get rid of the other fglrx.ko files...
i bet thats the porblem....[/QUOTE]

I wrote a fairly detailed [HOW-TO](http://www.ubuntuforums.org/showthread.php?p=348911) yesterday.  Give it a try.

---

### Post by floyd27 on 2005-09-14
finally back.
now you see why i dont like trying to do this..
Im not gona try again for a long time..
im hoping it will be included in breezy, if not then i will do without or find a distro that it works with..
I just dont have any more time to spend on a driver...(over a month now), which is rediculus..........

I know the ubuntu people know this is a huge issue with all the posts DAILY on how to do it and most people never getting there.....Its not like ATI cards are not p[opular...they are the best out and no support....wow

Im not ragging just wondering why this is STILL even a issue after this long a time..common people get on the ball...
Pretty bad when members give more help then the ubuntu people do....

---

### Post by mlomker on 2005-09-14
[QUOTE=floyd27]Pretty bad when members give more help then the ubuntu people do....[/QUOTE]

Nobody is paid...Ubuntu is free.  I spent a few hours writing the how-to and day figuring it out and I've done computers for over a decade as a career.  Linspire, Xandros, Windows cost money but they work easier.

---

