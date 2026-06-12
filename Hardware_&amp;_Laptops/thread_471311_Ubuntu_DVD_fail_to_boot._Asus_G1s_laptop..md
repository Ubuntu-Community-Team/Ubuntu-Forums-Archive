---
title: "Ubuntu DVD fail to boot. Asus G1s laptop."
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by PsYcHo_SiB on 2007-06-11
Hi,

I recently bought my new laptop, a shiny Asus G1s. So I decided to install Ubuntu on it. I burned a DVD version of Ubuntu, tried to boot both normal mode and safe graphic mode and they both throw this error:

"/bin/sh: can't access tty; job control turned off"

I really don't know what is going on here. 

Thank you for your help.

;)

---

### Post by merlinus on 2007-06-11
This may help:

[http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control)

-merlin

---

### Post by PsYcHo_SiB on 2007-06-11
Just finished installing Ubuntu on my laptop with the link your provided. Works flawlessly. Thank you !

---

### Post by merlinus on 2007-06-11
Glad it worked!

How do you like your new machine?

-merlin

---

### Post by renna on 2007-06-14
hi.

i have the same problem.

but when it's going to enter on ubuntu, ubuntu gives an error :
failed to start the X server. it is likely thar it is not ser up correctly....


can you help me ??

(sorry my english)

---

### Post by briguyd on 2007-06-18
> **renna said:**
> hi.

i have the same problem.

but when it's going to enter on ubuntu, ubuntu gives an error :
failed to start the X server. it is likely thar it is not ser up correctly....


can you help me ??

(sorry my english)

I'm having the same problem here (Asus G2S, but the only difference is the screen, the hardware is the same, as is the problem.)

---

### Post by shaders on 2007-06-19
Ok, guys, I got the same problem (X kick me out), but i have found a solution to boot in graphic mode. 
After the message on the blue screen you've got a command prompt.
Type this to edit the xorg.conf file : nano /etc/X11/xorg.conf
Go to the section Driver and change the 'nv' by 'vesa', then save the file (Ctrl+o) and exit.
Now you just have to type : startx 
and you're in...

(you must be root to do that : sudo bash)

---

### Post by renna on 2007-06-22
> **shaders said:**
> Ok, guys, I got the same problem (X kick me out), but i have found a solution to boot in graphic mode. 
After the message on the blue screen you've got a command prompt.
Type this to edit the xorg.conf file : nano /etc/X11/xorg.conf
Go to the section Driver and change the 'nv' by 'vesa', then save the file (Ctrl+o) and exit.
Now you just have to type : startx 
and you're in...

(you must be root to do that : sudo bash)

THANKS ALLOT!!!

that worked fine for me :D

---

### Post by Meldinov on 2007-07-13
I have a g1s and do the "brak=top" , "modprobe piix" and "exit" thing, but then, the screen goes black, the cd spins for a little time and suddenly, the computer reboots.
Ive tried kubuntu dvd, and a lot of diferent ubuntu versions (alternate feisty, and older stables).

---

### Post by didobuntu on 2007-07-15
Hi all,

I am interested to buy the same laptop, the Asus G1s. 

I just want to know if Alsa recognizes the sound card .. and if not, is it easy to get it working.

Other question please : do the intel wireless internet connexion run at first install ?

Thank you very much for your informations

---

### Post by ehmdjii on 2007-07-17
> **didobuntu said:**
> 
I just want to know if Alsa recognizes the sound card .. and if not, is it easy to get it working.
 yes, works out of the box.
> 
Other question please : do the intel wireless internet connexion run at first install ?
 no. quite difficult to get it working

---

### Post by MaxAmp on 2007-08-01
> I have a g1s and do the "brak=top" , "modprobe piix" and "exit" thing, but then, the screen goes black, the cd spins for a little time and suddenly, the computer reboots.
Ive tried kubuntu dvd, and a lot of diferent ubuntu versions (alternate feisty, and older stables).

Follow these steps if your screen goes black on an ubuntu install with an ASUS g1s-a1.

At the install screen use these options: 
F4 select "1024x768x32"
F6 type "break=top " at beginning

The screen will go black.  Wait until the CD stops going.
Then type:
modprobe piix
exit 

If you typed it correctly the splash screen will show.
If not then try F4 at VGA instead of 1024x768x32 and you can see what you are typing to but it will go black after that.

At blue screen select "no" for no information and "ok"

If you have a command promt continue.  If your typing on the edge of the screen then reboot and try again.  For some reason you have to reboot once.

Then follow shaders advice:
Type into the command prompt:
sudo nano /etc/X11/xorg.conf

Change the nv to vesa:
From:
Section "Device"
    Identifier
    Driver "nv"

To:
Section "Device"
    Identifier
    Driver "vesa"

After saveing (Ctrl+o then Ctrl+x)
type: startx

---

### Post by yianniscy84 on 2007-08-17
> **MaxAmp said:**
> Follow these steps if your screen goes black on an ubuntu install with an ASUS g1s-a1.

At the install screen use these options: 
F4 select "1024x768x32"
F6 type "break=top " at beginning

The screen will go black.  Wait until the CD stops going.
Then type:
modprobe piix
exit 

If you typed it correctly the splash screen will show.
If not then try F4 at VGA instead of 1024x768x32 and you can see what you are typing to but it will go black after that.

At blue screen select "no" for no information and "ok"

If you have a command promt continue.  If your typing on the edge of the screen then reboot and try again.  For some reason you have to reboot once.

Then follow shaders advice:
Type into the command prompt:
sudo nano /etc/X11/xorg.conf

Change the nv to vesa:
From:
Section "Device"
    Identifier
    Driver "nv"

To:
Section "Device"
    Identifier
    Driver "vesa"

After saveing (Ctrl+o then Ctrl+x)
type: startx

Hi.
I tried to run the liveCD on my ASUS G1s without changing the resolution but i get a black screen with a blinking cursor. If I change the resolution I get just a black screen. Any ideas????
:confused:
Btw where to I write break=top at the beginning before file... or after the file path before boot=casper???

---

### Post by derhanfi on 2007-08-19
you have to press F6 and at the end of the command line, you have to type: "break=top"

---

### Post by yianniscy84 on 2007-08-27
> **derhanfi said:**
> you have to press F6 and at the end of the command line, you have to type: "break=top"

Thanks I just had to wait after the blinking cursor.:)

---

### Post by 1kvng0 on 2007-09-29
> **MaxAmp said:**
> Follow these steps if your screen goes black on an ubuntu install with an ASUS g1s-a1.

At the install screen use these options: 
F4 select "1024x768x32"
F6 type "break=top " at beginning

The screen will go black.  Wait until the CD stops going.
Then type:
modprobe piix
exit 

If you typed it correctly the splash screen will show.
If not then try F4 at VGA instead of 1024x768x32 and you can see what you are typing to but it will go black after that.

At blue screen select "no" for no information and "ok"

If you have a command promt continue.  If your typing on the edge of the screen then reboot and try again.  For some reason you have to reboot once.

Then follow shaders advice:
Type into the command prompt:
sudo nano /etc/X11/xorg.conf

Change the nv to vesa:
From:
Section "Device"
    Identifier
    Driver "nv"

To:
Section "Device"
    Identifier
    Driver "vesa"

After saveing (Ctrl+o then Ctrl+x)
type: startx


Hi! I'm new to Ubuntu (and LINUX) and I've been trying very hard to get Ubuntu onto my G1S. I can do everything that you have said and get the same X Server error. I also put in: 

From:
Section "Device"
    Identifier
    Driver "nv"

To:
Section "Device"
    Identifier
    Driver "vesa"

but my only problem is when I go to save it, it says that the directory does not exist. When I try to change the filename, it doesn't work either. How can I get this modification to save? Thanks and sorry if this has been answered already. I searched the forums regarding the G1S, but I didn't find anything.

---

### Post by drzolo on 2007-09-29
I've got the same laptop Asus G1s. I was having same problem with the /bin/sh when booting, so i decided to try Ubuntu 7.10 Gutsy. I installed and almost everything worked fine. I do recommend installing all the updates right after the install.


Camera works, cpu scaling works, intel wireless works almost right out of the box.

I was having some trouble with 3d acceleration, so i just downloaded drivers off of nvidia.com and installed them. They work great. Although I do have to recompile them each time the kernel is upgraded. Anyone know how this could be done automatically?

Nvidia drivers allow you to overclock your video card by quite a bit. ie vid cpu to from 475 to 650 and memory from 700 to 900+. It does get a bit hot though, so i don't overclock now. :). Ubuntu desktop scales the GPU/Memory to 275/300 Mhz. Windows XP will scale it down to 169/100 Mhz. I'd like to do that in Ubuntu. Saves couple of minutes of power :). I m sure it has to do something with the Compiz/Beryl. 

The scroll on mouse, the "+" and "-" buttons on top of the mouse work right from the install. Although the side arrow buttons don't work. They need a bit of tinkering with.

Hibernation/suspend: i do not use it much, and whenever I did use it, i've had bad experience.

---

### Post by 1kvng0 on 2007-09-29
Thanks for the info. Is this version of Ubuntu stable enough to install? 

This might sound stupid to you, but how do you install Nvidia drivers? I downloaded it from the site, but the directions confuse me. I'm still  a noob. 

I actually tried installing Feisty Fawn onto my desktop and it works. It seems like a good OS. I tried installing beryl and  I am still getting the hang of it. It's cool to have a 3-d desktop

---

### Post by drzolo on 2007-09-30
> **1kvng0 said:**
> Thanks for the info. Is this version of Ubuntu stable enough to install? 

This might sound stupid to you, but how do you install Nvidia drivers? I downloaded it from the site, but the directions confuse me. I'm still  a noob. 

I actually tried installing Feisty Fawn onto my desktop and it works. It seems like a good OS. I tried installing beryl and  I am still getting the hang of it. It's cool to have a 3-d desktop

7.10 is quite stable, I believe official Gutsy is to be released sometime in October, so its in the final stages now.


Envy is one way to install the nvidia drivers.
[http://techrythm.com/index.php/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://techrythm.com/index.php/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

The other way is here:
[http://www.yaroman.net/2007/08/14/howto-install-nvidia-8600gt/](http://www.yaroman.net/2007/08/14/howto-install-nvidia-8600gt/)

Myself i recommend the 2nd approach.

Good luck.

---

### Post by Krischi on 2007-10-01
Gutsy already includes the latest nvidia drivers, which work with the G1S. You just need to install the nvidia packages and/or install them with the display configuration manager.

---

