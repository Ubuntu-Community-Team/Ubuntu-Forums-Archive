---
title: "Hard Drive issues"
date: 2010-07-13
forum: Hardware
---

### Post by tangerine0469 on 2010-07-13
Hi,
    i am at a loss here. i have a laptop:

Hp Pavilion Entertainment PC
Intel Core 2 Duo
4 Gigs Ram
HD\DVD Burner
dual Hard drives
250g ( Boot )
120g ( Storage )

i have had 2 seperate installations of Xubuntu (9.10 and 10.04 both x86) at 2 different times (not dual booted) plus a live USB with 4gig Persistance which i am currently using to post. both installations have for inexplicable reasons just stopped working. no new software has been installed that would conflict with their runnings nor has there been any physical damage to the laptop.

i have 2 problems here:

1) why do the installations keep failing
2) i can see the two hard drives in gparted but not in any file explorer. if i go into exaile music player and try to add music i know is there on the drives  they finally show up in /media but i can not copy anything from them to recover the data, i have tried with a new hard drive and a few external ones including a few usb thumb drives. and every time i try i get a "permision denied " 

any help would be greatly appreciated! if this keeps up i may consider nuking the drive and going back to windows.

---

### Post by AltomineUK on 2010-07-14
Hello :D

This might be slightly off topic but what made you chose Xubuntu over a regular distro?

---

### Post by tangerine0469 on 2010-07-14
i just wanted to try the desktop environment and the opportunity presented itself. i have tried all of them except for xubuntu until now. my favorite is kubuntu so far

---

### Post by AltomineUK on 2010-07-14
Ok..... it's just that I can see your laptop is more than capable of running the standard Desktop Edition of 10.04 so I was a bit curious as to why you had picked Xubuntu which is aimed at lesser PCs.
 As for desktop environments you can pick and install any that you like once you install the 10.04 LTS. I have tried Kubuntu.......quite nice place to work in. But I found that a bit too fiddly for me..... I like the simplicity of GNOME.

Have you tried installing Ubuntu 10.04 LTS and then change your desktop environment? It might have less failures during installations and you get choices about what desktop environment you would like to work in.

The last time I used Xubuntu, the tap-to-click function wasn't working for my netbook even though I enabled it, so I went for the full version.

---

### Post by tangerine0469 on 2010-07-14
i was actually going to try that tonight. i am going to try desperately to get my files off. the videos and music i can stand to loose i just need the word doc's. i already have 10.04 LTS installed on my 16g Thumb drive with 4gig persistance as before. it seems to be a flawless install as i have tested it on a couple of my work machines.

---

### Post by Jose Catre-Vandis on 2010-07-14
> **AltomineUK said:**
> Hello :D

This might be slightly off topic but what made you chose Xubuntu over a regular distro?

Grrr... :) Xubuntu is a regular distro !! ( In my eyes anyway) and many people prefer the xfce desktop to the standard gnome/kde. It can be just as good, if not "better" on current hardware. It may well be that xubuntu was the cause of the problem, but unlikely.

At what point does the installation/boot fail? Grub / Boot to login / after login? Have you tried recovery mode? I take it that the usb stick boots OK?

---

### Post by mr clark25 on 2010-07-14
ok, back to the thread owner's topic...

did you try to install from a cd or your usb drive?


what is the smart status of your hard drives?
(you must boot into ubuntu 10.04 and go to system>administration>disk utility, select your drive and it will diplay the smart status)

if you tried to install from a cd, it could be that your cd drive is failing. you can check this by using a known good ubuntu disk and "checking it for errors" if it reports any, (or a different number of corrupted files each time) you cd drive is bad.

if its your usb drive your installing from (it sounds like it is), it could still be several things. i would check te smart status of the drives if this was/is the case.



i had similar problems installing ubuntu 8.04 on my dell latitude and installing it on a netserver -i know these problems can be very frustrating.

---

### Post by tangerine0469 on 2010-07-14
> **Jose Catre-Vandis said:**
> Grrr... :) Xubuntu is a regular distro !! ( In my eyes anyway) and many people prefer the xfce desktop to the standard gnome/kde. It can be just as good, if not "better" on current hardware. It may well be that xubuntu was the cause of the problem, but unlikely.

At what point does the installation/boot fail? Grub / Boot to login / after login? Have you tried recovery mode? I take it that the usb stick boots OK?

it fails at the login screen but this only happens afer a few months of use. i type my password and the screen goes blank for a second and then the mouse shows activity and poof its back to the login screen.

---

### Post by tangerine0469 on 2010-07-14
> **mr clark25 said:**
> ok, back to the thread owner's topic...

did you try to install from a cd or your usb drive?


what is the smart status of your hard drives?
(you must boot into ubuntu 10.04 and go to system>administration>disk utility, select your drive and it will diplay the smart status)

if you tried to install from a cd, it could be that your cd drive is failing. you can check this by using a known good ubuntu disk and "checking it for errors" if it reports any, (or a different number of corrupted files each time) you cd drive is bad.

if its your usb drive your installing from (it sounds like it is), it could still be several things. i would check te smart status of the drives if this was/is the case.



i had similar problems installing ubuntu 8.04 on my dell latitude and installing it on a netserver -i know these problems can be very frustrating.


1) i have installed from both of them for the latest two installs, the pen drive being the later

2)i cannot get past the login screen at this point when booting from the hard drive. how do i check the smart drive status if i can't log in via the install. 

i now have in my possession two usb drives one has the original 9.10 xubuntu and the other one has the new ubuntu 10.04 LTS which i will use to try recove and ultimately nuke and repave the os

---

### Post by AltomineUK on 2010-07-14
> **Jose Catre-Vandis said:**
> Grrr... :) Xubuntu is a regular distro !! ( In my eyes anyway) and many people prefer the xfce desktop to the standard gnome/kde. It can be just as good, if not "better" on current hardware. It may well be that xubuntu was the cause of the problem, but unlikely.

At what point does the installation/boot fail? Grub / Boot to login / after login? Have you tried recovery mode? I take it that the usb stick boots OK?

Hehehe....

---

### Post by mr clark25 on 2010-07-14
> **tangerine0469 said:**
> 1)how do i check the smart drive status if i can't log in via the install. 

i *think* you can do it in a live environment...

---

### Post by tangerine0469 on 2010-07-14
> **mr clark25 said:**
> i *think* you can do it in a live environment...

How? i have a a working Ubuntu pen drive and i can wait to perform Armageddon on the hard drive for another day or so, what do you need from me?

---

### Post by tangerine0469 on 2010-07-14
Ohh and FYI i was able to change ownership of the entire drive to the live session and copy my files so this install is open to a few more days of experimentation.

---

### Post by sundays211 on 2010-07-14
if it crashes after the login screen, then this may be a problem with the x-server. what is your video card?

---

### Post by mr clark25 on 2010-07-14
> **mr clark25 said:**
> you must boot into ubuntu 10.04 and go to system>administration>disk utility, select your drive and it will diplay the smart status.

did you try this?

---

### Post by tangerine0469 on 2010-07-29
OK, sorry to have wasted your time but the hard drive died completely. that was my issue apparently.

---

