---
title: "Installed Ubuntu Hardy for a friend"
date: 2008-07-21
forum: General Help
---

### Post by djxcon on 2008-07-21
I have recently installed Ubuntu Hardy for a friend.  The computer is a Dell with pretty decent stats that I don’t need to get into.  I installed all the software that he would need from my home using my monitor, keyboard and mouse. 

When I brought the new box over to his place and hooked up his very outdated monitor, outdated keyboard, and outdated mouse, things were not nearly as pretty as I had them using my peripherals.  This is not shocking at all and I knew I would have to do some tweaking.  The Dell CRT monitor was not recognized at all so I chose a ViewSonic driver that I thought would work and it helped for the most part.  I was finally able to get 1280 X 1024 resolution.  The mouse was not a problem.

The problem is the really old Dell Quietkey keyboard.  It works but sometimes when you press the keys, they never register.  For example, if I press the letter e 10 times, there is a good chance that I will onle see 4 of them on the screen.  Other times I might get 10 out of 10.  The same thing happens on other keys.  

I tried to switch out the keyboard to an even older one (only spare he had) but the problem still occurred.  Has anyone seen this before?  Will an updated keyboard resolve his type of issue or do I have something else going on here.

Additional info: Nvidia video card with restricted driver installed and working.

Please share your thoughts.

---

### Post by vjkeito on 2008-07-21
have you tried reconfiguring xorg?  remember to make a backup first! (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup)

sudo dpkg-reconfigure -phigh xserver-xorg

or

sudo dpkg-reconfigure xserver-xorg



with regards to your monitor, if you know it works at certain resolutions and you have the correct drivers for your graphics card installed that support those resolutions then you add those resolutions manually to your xorg.conf if they are not already there.  you may want to check that the HorizSync and VertRefresh for your monitor are correct too.  Ubuntu doesn't always auto-detect these correctly but you can use a program called ddcprobe to check what it should be, install that using

sudo apt-get install xresprobe

the run it using

sudo ddcprobe | less

you are wanting a specific part of the information shown (monitorrange) you can get to this quickly with this command

sudo ddcprobe | grep monitorrange

it will return some values 

"monitorrange: **-%%, 60-75"

the **-%% in the example above will be the HorizSync and the 60-75 would be the VertRefresh

these can then be added to your xorg.conf

**[[COLOR="Red"]for more info please read this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate+howto")**

---

### Post by djxcon on 2008-07-21
I was a little hesitant to go that route since xorg was auto configured by the restricted driver, but I had planned to go this route if a new keyboard does not work.  Unfortunately, I will not be able to try the new keyboard for about three weeks.  Thanks for the suggestion and let me know if you have any other ideas!

---

### Post by vjkeito on 2008-07-21
As far as I know that should help with your troubles getting your monitor setup correctly.  

is the keyboard usb/bluetooth etc?

---

### Post by djxcon on 2008-07-21
Forgot to thank you for the monitor tip..I'll have to try that.  The keyboard and mouse are PS2.

---

### Post by ajgreeny on 2008-07-21
Don't forget that there is also an auto-configuration utility in Hardy, which takes advantage of the newer xorg 7.3.  Start up using the recovery mode (second down in grub menu) and when you get to the options part, choose "xfix".  As I understand it, this goes through the same procedures as when you install, detecting the monitor, etc etc, so should give the best for the hardware, assuming it is recognised.

---

### Post by djxcon on 2008-07-21
Thanks, I was unaware of this feature.  I have had the thought of reinstalling in the back of my mind as a last resort approach but this is definitely a better alternative.

---

### Post by Potatoj316 on 2008-07-21
It could be the keyboard that isnt working.  Is it USB or PS/2?

---

### Post by djxcon on 2008-07-21
It's PS2 and very old.  I tried an even older keyboard that is also PS2 and it had the same problem.  This leads me to believe that it's not the keyboard since the chance of having two different keyboards with the same problem is slim...unless there is a problem with old keyboards in general when using a Linux system.  These keyboards look to be from the early 90's or late 80's.

---

### Post by vjkeito on 2008-07-21
> **djxcon said:**
> Forgot to thank you for the monitor tip..I'll have to try that.  The keyboard and mouse are PS2.


no worries, hopefully these tips will help you out

peace

---

### Post by Potatoj316 on 2008-07-21
Maybe its the PS/2 controller thats giving you problems.  Ive used 10+ year old keyboards without problems before.  Maybe you could just tell your friend to buy a new keyboard.

---

