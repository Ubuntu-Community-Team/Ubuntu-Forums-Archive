---
title: "Screen resolution"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by Gundjah on 2005-09-08
For some reason HH does not offer me better resolution than 1024*768. The card is Matrox G200, W2K and Mandrake 10 can both do 1152*864 / 24bir / 75Hz.

Is there something I can try to get this up a bit?

---

### Post by kkvenkit on 2005-09-08
Look in */etc/X11/xorg.conf* for the phrase *Section "Screen"*. Inside that stanza you'll see resolutions defined at various colour depths. Set the *DefaultDepth* to what you want and adjust the corresponding list of resolutions. 

Note that with the wrong values you can wreck your monitor

---

### Post by Gundjah on 2005-09-10
[QUOTE=kkvenkit]Look in */etc/X11/xorg.conf* for the phrase *Section "Screen"*. Inside that stanza you'll see resolutions defined at various colour depths. Set the *DefaultDepth* to what you want and adjust the corresponding list of resolutions. 

Note that with the wrong values you can wreck your monitor[/QUOTE]
 Yap, thanks.

Unfortunately 1024*768 is the max in xorg.conf. I added 1152*864 and rebooted, but X wouldn't start, so I had to remove. Just now I'm again running Mandrake 10 with that reso w/o any problems.

I installed yesterday HH to another oldie, which has on-board Cirrus Logic. On that one I got the option to choose the desired reso during installation. What am I missing now?

---

### Post by tseliot on 2005-09-10
Find the supported refresh rates (Horizontal and Vertical refresh) in the manual of your monitor. Or find it in google.

Type sudo gedit /etc/X11/xorg.conf ("kate" instead of "gedit" if you use kde)

Add the desired resolution

scroll down the file until you find "Section "Monitor""

and put the rates in these lines in red according to the refresh rates supported by your monitor:



Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[COLOR=Red]HorizSync 28-49
VertRefresh 43-72[/COLOR]
EndSection

Save and exit


Then log out and log in.

Try to select the resolution you want

[COLOR=Red]OR[/COLOR]

CTRL+ALT+F1

sudo /etc/init.d/gdm stop (kdm if you use kde)

sudo dpkg-reconfigure xserver-xorg

it will ask you several things(if you don't know the answer just press Enter):

Tell it to autodetect the card and then select the driver you use (nv, nvidia, ati,etc. you can see it in xorg.conf).

It will ask you (I don't remember when) you desired resolutions:

select the one you need and press the spacebar to enable it (press Enter when you've finished)

When it comes to the refresh rate question select "advanced" and put the values of your monitor (horizontal and vertical refresh)

sudo /etc/init.d/gdm start

---

### Post by Gundjah on 2005-09-10
Thanks, tseliot  :) 

I'll dump this for now and try that if I don't get the resolution choice during setup. 

Another funky one is that I don't get any sound out of this thing - actually that I haven't managed to do with any distro so far... the sound doesn't work on the other oldie either. On this one I have some ancient ISA Soundblaster, the other one has an on-board SB compatible. Where should I look to get thouse running?

There are a couple others on this forum with the same problems. Maybe these (at least this reso thing) should be made sticky? Or put it in FAQ?

---

### Post by tseliot on 2005-09-10
[QUOTE=Gundjah]Thanks, tseliot  :) 

I'll dump this for now and try that if I don't get the resolution choice during setup. 

Another funky one is that I don't get any sound out of this thing - actually that I haven't managed to do with any distro so far... the sound doesn't work on the other oldie either. On this one I have some ancient ISA Soundblaster, the other one has an on-board SB compatible. Where should I look to get thouse running?

There are a couple others on this forum with the same problems. Maybe these (at least this reso thing) should be made sticky? Or put it in FAQ?[/QUOTE]
There is a good HOWTO about the resolution. I could write mine though.
There is one for setting the sound too.

However if you want something that works out of the box wait for Ubuntu Breezy's stable release, which is due on the 13th of October (if I'm not wrong). It's really amazing.

---

### Post by mailmaldi on 2005-09-10
yea the editing of xorg.conf is simple enuff...just get the monitor specs from ur monitors site & just put in ur options in the default section....

if 1152 is not displayed then try removing all otehr resolutions 800X600, 1024X768 from that section & only keep ur 1152 settign there...

the horiz & vert scan usually automatically sets the best ref rate so no problem there...

i resolved the same problem of mine easily enough...but my main most painful problem is that theres no sound on my system..(intel 915GAV motherboard)....

i compiled new kernel (2.6.13) & installed latest alsa & then sound worked but the kernel ran so unstably on my system that i had to delete it....

on the shipped kernel 2.6.10-5 now....wondering wat to do to make my sound work....

---

### Post by X5-655 on 2005-09-10
1280x1024 is the max in my xorg file, yet it's only allowing me to do 832x624..  yet in Windows I can easily do 1280x1024..

Its an ATI Rage Pro AGP 2X chip..  onboard..

---

### Post by Gundjah on 2005-09-11
[QUOTE=X5-655]1280x1024 is the max in my xorg file, yet it's only allowing me to do 832x624..  yet in Windows I can easily do 1280x1024..

Its an ATI Rage Pro AGP 2X chip..  onboard..[/QUOTE]

I think you have the same problem as me, the monitor refresh rates in xorg.conf are wrong. What puzzles me is that with the other oldie I get a choice during installation, this one (marginally newer...) I don't. Which is pretty odd, as with basically any other distro I've used to get higher resolution with better refresh rates than with Windows. 

I just tested with the other one, and I can do 1280*1024 and the other monitor isn't supposed to support that... but it seems to do nicely enough, even without the flickering you get with refresh rates below 75Hz :???: 

Next stable due in October? Rats, I gotta get busy with distributing these 50 Hoarys I just received a couple of weeks ago. :D

I'm anxious enough to try... is the sound thing already corrected in the unstable? Worth trying?

---

### Post by tseliot on 2005-09-11
[QUOTE=Gundjah]What puzzles me is that with the other oldie I get a choice during installation, this one (marginally newer...) I don't. Which is pretty odd, as with basically any other distro I've used to get higher resolution with better refresh rates than with Windows.[/QUOTE]
During the installation of Ubuntu 64 bit the installer asks you which resolutions would you like to use. This doesn't happen in Ubuntu 32bit. I don't know why.

---

### Post by Gundjah on 2005-09-11
[QUOTE=tseliot]During the installation of Ubuntu 64 bit the installer asks you which resolutions would you like to use. This doesn't happen in Ubuntu 32bit. I don't know why.[/QUOTE]

... on PII 300 it asks for resolution, on PII 400 it doesn't, installing from the same CD???

---

### Post by nkrust on 2005-09-12
[QUOTE=Gundjah]For some reason HH does not offer me better resolution than 1024*768. The card is Matrox G200, W2K and Mandrake 10 can both do 1152*864 / 24bir / 75Hz.

Is there something I can try to get this up a bit?[/QUOTE]

1.first go to tty1 press[ctrl+Alt+F1]

2.on the prompt for login enter ur login/passwd.

3.run the command : sudo dpkg-reconfigure xserver-xorg

it will bring up a simple gui sort of thing that u get when u install ubuntu at first.
just follow the guidelines and it will be fine.

4. at one stage it will ask for the HorizSync and VertRefresh, consult ur monitor manual and enter the values.(be careful with what u enter as ur monitor life is going to depend on it)

5.next it asks for the depth, choose 24, if u want 24 bit.

6.write the changes.

7.press [ctrl+Alt+F7] to bring up the GDM and press [ctrl+Alt+backspace] to restart X server.

8.if the xserver doesnt start by default, press [ctrl+Alt+F1] and type sudo startx.

9.go to GDM if it still doesn't start go back to tty1 and check out the error message. also check the log file at /var...(check the path in the error msg, i dont remember).

10.in all probability it should be the horiz and vert rates, in that case enter:
sudo vi /etc/X11/xorg.conf to manually edit the conf file(be carefull). press esc+i to go to insert mode.

11.find section "Monitor", there u will find HorizRate and VertRefresh values keep altering the ranges and try starting the X, after a bit of trial and error u will get ur resolution and depth.

wish u al the best.

(from my experience in configuring the X).

---

