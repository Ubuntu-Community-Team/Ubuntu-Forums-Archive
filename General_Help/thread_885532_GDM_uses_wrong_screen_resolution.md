---
title: "GDM uses wrong screen resolution"
date: 2008-08-10
forum: General Help
---

### Post by Aat on 2008-08-10
Today I reinstalled hardy from live-cd, after messing up my original install.

Everything went OK, except for the screen resolution. I changed it to the 1280x800 I want and that worked, except for the gdm-login screen.
The resolution there is now something like 1600x1200, so I can't see a large part of the screen.

According to the gdm-config file, gdm gets its information from xorg.conf.
But that file seems to be ok, since ubuntu works with the correct resolution

Any ideas?

---

### Post by Aat on 2008-08-24
No one knows the solution to this problem?

---

### Post by djhvt on 2008-10-08
Im having the same problem. My desktop is fine, but im missing the whole bottom "options" bar and my login window is off center....any help out there?

---

### Post by Bibek on 2008-10-08
Have you tried this 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
if that doesnt work post your /etc/X11/xorg.conf file here

---

### Post by djhvt on 2008-10-08
well that didnt go as planned, this is what i got:

[HTML]bash: /etc/X11/xorg.conf: Permission denied
[/HTML]

---

### Post by djhvt on 2008-10-08
also Gnome seems to be the only window manager on my system that works properly too. Both Fvwm and Icewm seem to have a screen rez that cuts off a good chuck of the bottom and righthand side....just like the login screen...but Gnome works totally fine

---

### Post by cybrid on 2008-10-08
> **djhvt said:**
> well that didnt go as planned, this is what i got:

[HTML]bash: /etc/X11/xorg.conf: Permission denied
[/HTML]

You sure you put "sudo" before "dpkg-reconfigure -phigh xserver-xorg" ?

Also I didn't know that to change gdm resolution you had to edit xorg.conf... but maybe I'm wrong.

---

### Post by Sycron on 2008-10-08
I just hate the last version of GDM that came with Intrepid Beta. I can't have the proper resolution when starting X with an external monitor.

---

### Post by Bibek on 2008-10-08
This link may be of interest 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216871](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216871)

---

### Post by djhvt on 2008-10-11
i did indeed put sudo in, just to be safe though i did it again. this time i got the follow:

[HTML]aftertwilight@aftertwilight-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for aftertwilight: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081009030500
[/HTML]

after which nothing happens. Not sure if i did something wrong or not. 

for everyone that has tried to help me thus far thanks! Any other help would be greatly appreciated as i would like to use a lighter weight window manager.

---

### Post by djhvt on 2008-10-11
thanks for the link man, it looks like other people are having the same problem and have found a solution....but its all in gearhead speak, could someone maybe boil that down a bit for me. This is why i dont have an account over there i cant understand most of what people are talking about, and dont really have the time to figure it out. The forums here are far more helpful for just the average user.

---

### Post by bodhi.zazen on 2008-10-11
> **djhvt said:**
> i did indeed put sudo in, just to be safe though i did it again. this time i got the follow:

[html]aftertwilight@aftertwilight-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for aftertwilight: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081009030500
[/html]after which nothing happens. Not sure if i did something wrong or not. 

for everyone that has tried to help me thus far thanks! Any other help would be greatly appreciated as i would like to use a lighter weight window manager.

After running that command, you need to log off and back on.

---

### Post by djhvt on 2008-10-12
thanks i didnt realize i needed to log out. Unfortunitly that command didnt seem to help, and may have added to my woes. Now when i turn on my laptop my screen is still off center with the bottom options bar out of view and now i have six vertical lines of distortion at the log-in screen. Note that i only have display issues at the login screen and if i boot into a non-gnome window manager.

Everyone continued help is thanked, you guys rock!:KS

---

### Post by bodhi.zazen on 2008-10-12
> **Sycron said:**
> I just hate the last version of GDM that came with Intrepid. I can't have the proper resolution when starting X with an external monitor.

Well last time I looked Intrepid is still in Beta, so as of yet there is no "GDM that came with Intrepid".

If you want to run beta software that is your choice, but it is inappropriate to treat it as a release and even more inappropriate to complain about it.

Ranting about a beta release makes you look bad and is not the best way to get assistance.

You should either file a bug report or post in the appropriate forums:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by bodhi.zazen on 2008-10-12
> **djhvt said:**
> thanks i didnt realize i needed to log out. Unfortunitly that command didnt seem to help, and may have added to my woes. Now when i turn on my laptop my screen is still off center with the bottom options bar out of view and now i have six vertical lines of distortion at the log-in screen. Note that i only have display issues at the login screen and if i boot into a non-gnome window manager.

Everyone continued help is thanked, you guys rock!:KS


Well it should be easy to fix. If you look at the output of the previous command, it made a backup.

so ...

```
sudo cp /etc/X11/xorg.conf.20081009030500 /etc/X11/xorg.conf
```

and then log of and back in.

Now that we have fixed that snafu, what video card do you have ?

---

### Post by cybrid on 2008-10-13
I know that what I'm going to say does not belong to the thread's theme but, I'm very intrigued with a problem I have. I own a notebook; an Acer Aspire 2020 with an Ati Mobility 9700 128Mb graphics card. I've tried with the Ati propietary driver in versions 8.3 (the one in hardy repositories), 8.6 (the one that envy installs) and 8.9 (downloaded from amd/ati's website and built by me) and whenever I put "fglrx" in the xorg.conf file, gdm loads ok but as the desktop begins to load it ends up freezed before even showing the background. The only driver that seems to "work" is the generic vesa driver (no the "ati" driver doesn't work either). Is that a known problem in hardy?, I don't recall it happening in edgy.

---

### Post by djhvt on 2008-10-16
Ok, so i entered in the command, it asked me for my password and after that no other commands came up. I took this as my cue to log out and log back in, but alas the problem persists. My login screen is off center with the "options" bar out of reach.

Ive never had any display issues with ubuntu on my prevous systems, so this is totally new territory for me. So be sure to put advice in terms of interacting with a total blooming idiot, which is me:KS.

As for my graphic set-up it is a VIA UniChrome9 HC IGP. It is inside my spiffy new gbook from Everex. This is the laptop that come with GOS standard. However i found GOS really buggy and slow with terrible support so i ditched it for Ubuntu proper. Really other than this one issue im completely satisfied.

Again thanks everyone for your continued support, this is really the most supportive community on the web.

---

### Post by bodhi.zazen on 2008-10-16
> **djhvt said:**
> Ok, so i entered in the command, it asked me for my password and after that no other commands came up. I took this as my cue to log out and log back in, but alas the problem persists. My login screen is off center with the "options" bar out of reach.

Ive never had any display issues with ubuntu on my prevous systems, so this is totally new territory for me. So be sure to put advice in terms of interacting with a total blooming idiot, which is me:KS.

As for my graphic set-up it is a VIA UniChrome9 HC IGP. It is inside my spiffy new gbook from Everex. This is the laptop that come with GOS standard. However i found GOS really buggy and slow with terrible support so i ditched it for Ubuntu proper. Really other than this one issue im completely satisfied.

Again thanks everyone for your continued support, this is really the most supportive community on the web.

You can *try* this :

[http://www.tkarena.com/forums/linux-arena/32054-vn896-chrome9-hc-igp-linux-driver-needed.html](http://www.tkarena.com/forums/linux-arena/32054-vn896-chrome9-hc-igp-linux-driver-needed.html)

---

### Post by djhvt on 2008-10-26
Thanks for all the effort folks, but sadly im still in the muck. That said i think i may have stumbled on something that looks promising...but its a bit over my head. I found [this downloadable document]("http://driverscollection.com/?file_cid=3963546853263fb5caac5ac0711") on the VIA website that seems to discribe how to use an alternative driver.Sorry i wasnt able to upload it with this post, it exceeded the size limit...silly pdf! 
Could someone please take a look at it and boil it down a bit for me, and possible let me know if im on the right track?

Again thanks so much you guys

---

