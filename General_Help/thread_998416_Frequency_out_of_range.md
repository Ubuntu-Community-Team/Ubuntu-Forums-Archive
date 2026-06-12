---
title: "Frequency out of range"
date: 2008-11-30
forum: General Help
---

### Post by ItsKiNgY on 2008-11-30
Hey, so i have installed ubuntu using wubi and it seemed to go without a hitch and i think it has, the only problem being i cant see whats going on as when it loads my monitor gives me a message saying 'frequency out of range'. I'd guess i have to change the display settings before ubuntu loads or whilst it is loading its just i am completely new to other operating systems and don't know how to go about it. i was wondering if someone could help me :D

---

### Post by Swagman on 2008-11-30
Your optimum resolution should of been detected on initial installation.

Ok.. Without asking you to go edit xorg.conf .. Cuz you probably don't know what that is.. Lets try Recovery.

Reboot. when the grub countdown starts press esc.
select recovery
It will do its thing and you end up at a box with a few options.

Select the bottom one.. X server
It should reset your screen mode. then when it's done that select reboot.

Hopefully that will have sorted it.

---

### Post by ItsKiNgY on 2008-11-30
i tried what you said and i got a message saying something about a cusotmized file, I think i should mention that i have installed this on a slave hard drive could this be causing it?

---

### Post by workingvincent on 2008-12-01
The possibility is big, you may change it to suit.

---

### Post by Swagman on 2008-12-01
You haven't said what graphics card your using. I will assume Ati because nVidia just seem to work !!

Try entering this at the prompt

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by ItsKiNgY on 2008-12-01
Okay it sort of works no i just cant have the high graphics set as it needs a driver and when i install it i loose the picture as the frequency is out of range i also cant change any of the resoloution settings as when i open up the resoloution settings all the fields are there only there blank and there is nothing to change? is it like booting in ubuntu's version of safe mode or something. I have no idea, Thanks alot for help and suggestions thoe :D

NOTE: My graphics card is an ATI Raedon xpress 200

I have also tried what you told me to do Swagman and i got this message, i cant work out if it was a success or not XD, i wrote what you said in the shell prompt in recovery mode and got..

xserver-xorg post inst warnin: overwriting possibly-customised configuration file: backup in etc/x11/xorg.conf.20081201121542

But still resoloution is all dodgey and as far as i can tell it is only loading in recovery mode.

---

### Post by Swagman on 2008-12-01
Congrats at getting a screen !!

Yes you are running in a kind of "safe mode".

Out of Frequency nearly always means you are pumping out a resolution your **MONITOR** can't handle.

So... What monitor have you got and what can it handle ?

[edit]

Oh..  HOW are you installing the graphics driver ?

---

### Post by ItsKiNgY on 2008-12-01
So i have a Gateway FPD1960 TFT LCD Monitor, And i click on apearance and then click on the visual effects tab then when i check the extra radio it tells me i need to install ATI/AMD proprietary FGLRX graphics driver, however i now dont think this is the problem as if i try to load in normal ubuntu it doesn't display it says frequency out of range so it is resoloution settings isn't it? as im guessing recovery mode like xp's safe mode sets the resoloution to something most monitors can handle i could live with being in recovery mode but it just looks so ugly XD

---

### Post by Swagman on 2008-12-01
Okey Cokey

You probably haven't activated propriety drivers.

Go into... System > Adminstration > Hardware drivers

You will see something akin to this...

oops.. I've just noticed I've deactivated mine with that last command I gave you  (I tested it out on mine) lol

[IMG]http://i261.photobucket.com/albums/ii45/Outcast_Aussie/hardwarescreeny.jpg[/IMG]

Just select the newest driver and click activate... You will need to reboot soon after

---

### Post by Swagman on 2008-12-01
You know whats scary ?

He hasn't come back yet !!

Whats the bets that gave him his original problem back.

---

### Post by ItsKiNgY on 2008-12-01
okay I'm back XD and it did give me my origional problem even when trying to get on in revcovery mode i got nothing, so i had to use xfix and then i could get a display, any other ideas? when it loads i can see the ubuntu loading screen with teh nice orange loader bar then it says frequency out of range for about 15 seconds then i get an image but it is just an underscore '_' in the top left corner then after about 2 seconds i get my beloved frequency out of range sign back.

EDIT

when i used xfix it has deactivated the driver that i activated.

---

### Post by ago on 2008-12-02
I suggest asking in the dedicated video forum: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

If you run lspci, you can have a description of your video hardware and then search the forum for the appropriate settings

---

