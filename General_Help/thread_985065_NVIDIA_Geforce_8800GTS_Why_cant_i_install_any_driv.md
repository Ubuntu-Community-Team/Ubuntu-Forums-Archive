---
title: "NVIDIA Geforce 8800GTS Why cant i install any driver?"
date: 2008-11-17
forum: General Help
---

### Post by zantetsuken on 2008-11-17
before id start id like to point out im a complete newbie in linux and i have only used it for about a day so please provide step by step instruction and telling me what that step does and what might be wrong.

my current system is an AMD Athlon 64 3500+, MSI K8N Diamond Motherboard 3 Gigs of memory and 2 SATA hard drives, one of those hdds is split up and contains XP and the other partition on the same drive has Ubuntu 8.04 installed. The system is powered by an NVidia geforce 8800GTS 320MB graphics card which is hooked up to a 22inch and a 17 inch screen via two DVI connections if that helps. this configuration works perfectly fine in windows.


My problem arises when i try to install my nvidia drivers, whether i install them from the restricted drivers or whether i use envy or whether i download the drivers straight from the website i seem to get a black screen when i reboot, the system is unresponsive i cannot enter any commands ctrl alt F1 nothing works, i have to restart get into recovery console and make it fix x, to start working i have no clue why i cannot seem to install sucha powerful graphics card. 

I really wanted to try out compiz fusion which seemed really good but now i cant even play a video in ubuntu since i cant install any drivers. can someome please help me out? ive looked all over the net for this and i cant seem to find a place where i can start.

Thanks in advance! any help is hugely appreciated.

---

### Post by zantetsuken on 2008-11-18
bump. anybody?

---

### Post by Gausian on 2008-11-18
did you just install Ubuntu?  If so, did you get all available updates before trying to install the Nvidia driver?

---

### Post by zantetsuken on 2008-11-18
yes i installed ubuntu and then i went to synaptic package thing and i downloaded all the updates something like 206mb worth of updates i did all that and then i think i even went and did program updates just to make sure and den when i installed the driver...even the default restricted driver it just gave me a blank screen...den i did a format and i reinstalled it..and im having the same problems again.

---

### Post by zantetsuken on 2008-11-18
can someone point me in the right direction on what i should do to try and fix this? i cant seem to find any thing that works for me why is this happening? ths graphics card works completely fine in windows yet wen i change over i cant seem to even watch a video it wont do that coloured line thingo test. anybody?

---

### Post by phidia on 2008-11-18
There have been recent changes in the way video is configured in Ubuntu.

It can be frustrating for the helpers here as well as people having the problems.

Then too the latest nvidia drivers may have problems with the latest kernel.

Because you have a 8 series card (there have been reports of problems with 8 & 9 series cards) try [this how to]("http://ubuntuforums.org/showthread.php?t=984198") posted recently by a user of the forums. Let us know how that works please.

---

### Post by fooman on 2008-11-18
you say you have 2 monitors hooked up? ...have you tried using just one?

its sometimes tough enough getting one videocard/one monitor configured....getting 2 configured from the get-go can only make things more difficult.

work on getting one monitor up and running...the second can be added using the nvidia-settings applet after the drivers are installed and working.

---

### Post by zantetsuken on 2008-11-19
i think ur right i havent actually tried it but ill give it a shot with umm the fully functional 22 inch lcd, the 17 is a little dodgy.

---

### Post by zantetsuken on 2008-11-19
it didnt work because it said "this run file is intended for a 64 bit linux operating system you seem to be running x86." and didnt let me install.

is that normal or what?

---

### Post by zantetsuken on 2008-11-19
IT WORKS!! IT LIVES! = lol, just had to upgrade to 8.10, just wanted to ask someone how do i dual screen this now?.

---

### Post by fooman on 2008-11-19
are the nvidia drivers installed?

if so,  first shutdown and connect the second monitor.  reboot, open a terminal and type:

```
gksudo nvidia-settings
```

when it opens, click on "X server display configuration".  you should see the 2 monitors in the "layout" box.  click on the one that says "(disabled)",  then click the "configure" button.  when the box pops up,  click on "separate x screen" then click "ok".

next click on "save to x configuration file"....click "save" (you may see a message that not all settings could be applied...or something similar),  click ok or save.  close the nvidia settings box and restart x by logging out (ctrl-alt-backspace).  log back in and see if that works.

---

### Post by zantetsuken on 2008-11-19
wen i click "save to X configuration file" it says unable to create new X config backup file /etc/x11/xorg.conf.backup.

is this normal?....it duznt seem to enable dual screens..coz it cant remember my settings...

---

### Post by fooman on 2008-11-19
did you use the command:

```
gksudo nvidia-setting
```

to open the applet?

it has to open as root (gksudo) in order to save the settings for the next x session.  

you cannot use the "nvidia x-server settings" from the menu...it will not save the settings.

---

### Post by zantetsuken on 2008-11-19
im typing it in the applet and nothing comes up after i put in my sudo password in that box nothing comes up...its sorta like..just stuck...my cursor shows no circle or anything just standing there.it sorta goes busy wen i type it in for a while...and den back to normal..no activity.

---

### Post by fooman on 2008-11-19
try it without the gk:

```
sudo nvidia-settings
```

---

### Post by zantetsuken on 2008-11-19
i managed to do it but no more compiz settings work?. ok ive not got that Xinerama thing on its got two screens up but half of my 22 inch is black...only half of it has desktop space. wen i enable xinerama thing it makes it complete but i lose desktop effects.

edit; i can move the cursor into the black space but not the windows.


this is the current set up 17inch - 22inch all of 17 inch is fine and bout 75% of 22inch is visible the very right theres just a black bar and and a bit on the bottom.

---

### Post by zantetsuken on 2008-11-19
ive got only one screen enabled atm, the 22inch but my problem is when i restart my resolution becomes low it goes to 1280x1024, so i have to manually reconfigure it to 1920x1080 everytime, how do i make this change permanent?.

---

