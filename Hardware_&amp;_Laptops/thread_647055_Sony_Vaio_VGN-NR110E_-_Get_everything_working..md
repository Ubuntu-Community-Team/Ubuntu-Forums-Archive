---
title: "Sony Vaio VGN-NR110E - Get everything working."
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by ejw2076 on 2007-12-21
First let me say that I am not a linux expert.  I have been using it for about 7 months and have become addicted to being able to do **anything** I want on my computer.  Since I have not been using it that long I hope that there are people who can help at least point me in the right direction when it comes to completing this.  Now, I am getting tired of having a $400 laptop that isn't being used to its full potential and I would like to make this thread a place where NR110E owners can collaborate to get this laptop working as well as possible.

I am going with a fresh install of Xubuntu 7.10.  The reasons for this is that XFCE is incredibly light-weight, and I intend on using this laptop for J2EE development.  I also prefer the option of installing things later, rather than having them there **if** I need them.

[COLOR="DarkRed"][SIZE="3"]Hardware:[/SIZE][/COLOR]
[SIZE="1"]These values are found by typing [COLOR="DarkGreen"]sudo lshw[/COLOR][/SIZE]

[COLOR="Navy"]Graphics[/COLOR]
product: Mobile GM965/GL960 Integrated Graphics Controller

[COLOR="Blue"]Wireless[/COLOR]
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter

[COLOR="RoyalBlue"]Audio[/COLOR]
product: 82801H (ICH8 Family) HD Audio Controller

Mouse is the Synaptics Touchpad

[COLOR="DarkRed"][SIZE="3"]Problems[/SIZE][/COLOR]

[COLOR="Navy"]Graphics[/COLOR]
-Cannot change backlight.
-OpenGL does not work.  Gears (screensaver) takes 100% cpu. (solved)
-Special Effects do not work in Ubuntu.

[COLOR="Blue"]Wireless[/COLOR]
-Does not work at all without configuring Ndiswrapper (solved)

[COLOR="RoyalBlue"]Audio[/COLOR]
-Ubuntu no audio at all for me.
-Kubuntu worked just fine on one install, then headphone jack only on a second.
-Xubuntu has audio out of both the speakers and headphone jack, but on the same channel.

[COLOR="DeepSkyBlue"]Other[/COLOR]
-Wifi switch is a bitch to get working correctly.  Some guesses have been made as to how to get the wireless turned back on after disabling it, but I think we need a test script of sorts to ensure we know **exactly** what is going on there.  If someone already has this, please post exactly how you ensure your wifi card gets turned back on.

-Wifi LED inside the Wifi switch does not work at all, I'm not sure exactly how we could get this working, but I'd imaging it will include modifying some code buried deep in the system.  I have no problem learning how to do this, as it would teach me quite a bit about linux.

-Mouse acceleration is not working. (solved)

-Shortcut keys work differently depending on distro.  On Ubuntu and Kubuntu the mute and volume keys would result in an output, but not an action.  Xubuntu results in no output.

Here is the current shortcut responses in Xubuntu:

key [COLOR="Navy"]lable[/COLOR] function
fn+f2 [COLOR="Navy"]mute[/COLOR] n/a
fn+f3 [COLOR="Navy"]vol-[/COLOR] n/a
fn+f4 [COLOR="Navy"]vol+[/COLOR] n/a
fn+f5 [COLOR="Navy"]bright-[/COLOR] n/a
fn+f6 [COLOR="Navy"]bright+[/COLOR] n/a
fn+f7 [COLOR="Navy"]vga out[/COLOR] n/a
fn+f10 [COLOR="Navy"]zoom[/COLOR] n/a
fn+f12 [COLOR="Navy"]hibernate[/COLOR] n/a
fn+numlk [COLOR="Navy"]scroll lk[/COLOR] n/a
fn+insert [COLOR="Navy"]pause[/COLOR] n/a
fn+del [COLOR="Navy"]break[/COLOR] n/a
fn+7 [COLOR="Navy"]7[/COLOR] home
fn+8 [COLOR="Navy"]8[/COLOR] up
fn+9 [COLOR="Navy"]9[/COLOR] page up
fn+0 [COLOR="Navy"]/[/COLOR] /
fn+u [COLOR="Navy"]4[/COLOR] left arrow
fn+i [COLOR="Navy"]5[/COLOR] n/a
fn+o [COLOR="Navy"]6[/COLOR] right arrow
fn+p [COLOR="Navy"]*[/COLOR] *
fn+[ [COLOR="Navy"]enter[/COLOR] enter
fn+j [COLOR="Navy"]1[/COLOR] end
fn+k [COLOR="Navy"]2[/COLOR] down arrow
fn+l [COLOR="Navy"]3[/COLOR] page down
fn+m [COLOR="Navy"]0[/COLOR] insert


[SIZE="3"][COLOR="DarkRed"]Solutions:[/COLOR][/SIZE]

-To get OpenGL working you need to run the command:
  [COLOR="DarkGreen"]sudo apt-get install libgl1-mesa-dri [/COLOR]
  Please note that it will ask for the disk to do this, if you do not have access to the installation disk, comment out the cd drives in the /etc/apt/sources.list

-Configure wireless by following [_these_]("http://ubuntuforums.org/showpost.php?p=3868406&postcount=48") instructions.

-I was consistently touching the touchpad while typing, this would cause me to loose focus.  [_This_]("http://ubuntuforums.org/showthread.php?t=271052") fixes it completely.

-[_Here _]("http://ubuntuforums.org/showpost.php?p=2478000&postcount=2")is how I fixed the mouse acceleration problem.  I changed the min and max speeds closer, and slowed the acceleration.  It isn't perfect, but it beats having to pick up my finger to go from one side of the screen to the other.



If you can help with any of the problems listed, please help.  I'm going to try and tackle these piece-by-piece, but please feel free to contribute.  **If you found this thread looking for a solution, PLEASE POST UPDATES HERE WHEN YOU FIND A SOLUTION.  If nothing else, at least post the progress you have made in completing whatever goal you have set**.

---

### Post by chalewa on 2007-12-24
good luck with all of this...


i will see what i can tackle as well, and keep my progress updated in this thread. i have currently been working on figuring out why in the world it takes 8 or 10 times of rebooting to get the wireless back up again. are you experiencing a problem like this or not?


edit: and as far as the mouse thing goes, you just put that entry into your xorg?

---

### Post by philhow on 2008-01-07
I installed 7.10 on my NR110E and the wired network doesn't seem to work. Did you have any trouble with that?

---

### Post by chalewa on 2008-01-08
> **philhow said:**
> I installed 7.10 on my NR110E and the wired network doesn't seem to work. Did you have any trouble with that?



yea, you have to use ndiswrapper...

i wrote a howto a while back here it is [http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)

---

### Post by kompas on 2008-01-16
This thread (ejw2076) has been a genius. Everything is working on my girlfriends VGN-NR110E except desktop effects.

Does anyone have any input or solutions for this?

Thanks very much all -

---

### Post by opteek on 2008-01-23
Compiz desktop effects work for me on fresh 7.1 install AFTER removing the video card from the aiglx blacklist. Otherwise, you need to install xgl, which for me, gave choppy fullscreen video playback.

---

### Post by kayel_justice on 2008-02-05
Hey guys. I'm noob so pleas heave patience..lol...I have a NR110E/S with originally Vista on it and I wiped it clean with 7.10.   Do I have to install new drivers now with the new install? And if so, do I specifically have to use Ubuntu or are other OS Drivers compatible. As you see I need help, I can't wait to start using my new laptop.

Thanks in advance

---

### Post by coquimbo on 2008-02-05
> **opteek said:**
> Compiz desktop effects work for me on fresh 7.1 install AFTER removing the video card from the aiglx blacklist. Otherwise, you need to install xgl, which for me, gave choppy fullscreen video playback.

How do you remove the card from the aiglx blacklist?

---

### Post by drlisacuddy on 2008-03-13
hey, been running Gutsy (GNOME desktop) on my NR110E for a few weeks.
 it's great, most things work out of the box, can't get backlight down or compiz working (don't know how, although I would love to muck in code.)

I have sound working on Ubuntu, the only caveat is that for headphones, you need to mute the volume (right click the volume indicator and check the box next to mute) AND put PCM-2  all the way up.Then you can control the volume for your headphones with the volume indicator in the taskbar (otherwise the speakers will still output sound along with the headphones, which is probably not what you want.) The volume indicator at the top will still show that it's muted, but that's only for your main on-board speakers, and sound should be outputted to your headphones. This is a very strange setup, and it took me a while to figure out what was happening, but it's a solution for people who like to use headphones (because the speakers are kinda bad).

I'm gonna go try to get wireless working and try to blacklist my card for compiz.

~drlisacuddy

---

### Post by drlisacuddy on 2008-03-13
> **coquimbo said:**
> How do you remove the card from the aiglx blacklist?


**SOLUTION**
In the terminal, run:

```
gksudo gedit /usr/bin/compiz
```

(compiz needs to be installed.)

the file will open in gedit, you will need to comment out these lines


```

T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)

```

by putting "#" (without quotes) in front of these two. I did both just to make sure, because I couldn't tell which one was the one in the VAIO (and it doesn't hurt, either.)

Restart X by pushing Ctrl-Alt-Backspace, then log in and enable Compiz.

This will allow Compiz to run on the video card using AIGLX, which is much better than Xgl (Xgl happens to ruin the OpenGL fix for screensavers, btw). This does work, and I don't see any problems (as of now) running compiz.

---

### Post by zman5 on 2008-07-12
Hello forum :)  

I'am new to Linux But i like it. The problem i'am having is the wifi does not work on my sony vaio vgn-nr110e

HAL Device Manager say its a

AR242x 802.11abg Wireless PCI Express Adapter 


I have read that it really is a Atheros 5006 or a 5007

I have tried this [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html") 

And it worked but then after i shut down & booted back up it was no longer working. And reentering it did not do any thing. I'am stuck & dont no what to do at this point :confused:

---

### Post by chalewa on 2008-07-13
yea i have that problem too. 

lots of people have different methods for fixing it, the only one i have found that works 100% of the time is to give it a hard shut down. 

using the menu, and restarting or whatever will cause the wireless to not work. hit the power button to shut it down, and then turn it back on, and see if wireless works.

---

