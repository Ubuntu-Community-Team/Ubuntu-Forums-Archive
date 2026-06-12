---
title: "volume control: No volume control GStreamer plugins and/or devices found"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by ranfr on 2007-09-05
Hello,

After one of the recent updates I was requested to restart my system ("system restart required") ever since, I have no volume control at all and my soundcard is not recognised anymore. i'm using dell xps m1210 laptop with soundblaster audigy card. I tried to reinstall alsa, with support for the card but without any success ](*,)]. I googled around but found no solution. This is almost certainly a software issue, not limited only to dell - a colleague of mine has the same problem with thinkpad.

i'm using ubuntu 7.04 

Any help will bw appreciated.

Ran.

---

### Post by jam1n on 2007-09-05
just so you know the exact same thing happened to me. updated and after the restart my sound does not work. i dont know how to fix it.

---

### Post by srt4play on 2007-09-06
Was one of the recent updates for the kernel?  

Can you try booting a previous kernel to see if that brings sound back?

---

### Post by jam1n on 2007-09-06
what do you want me to  try? booting from the disk? i do know that sound works on windows when i boot into it.

---

### Post by thepunisher on 2007-09-07
Same problem here guys - did an update on the kernel yesterday and my sound is gone. I get the same error you stated above. I tried recovery mode (Im really new to ubuntu) but my sound is still not working.

If you have any suggestions on how to fix this let me know!

---

### Post by thepunisher on 2007-09-07
Loaded back into 2.6.20-15-generic and sound is back!

---

### Post by jam1n on 2007-09-07
i dont know how to do the reload into an earlier kernel.

---

### Post by sahra on 2007-09-10
I've managed to solve this problem on my computer after many hours trying to fix it!  (Well, mostly -- see below.)

I suggest avoiding the Comprehensive Sound Problem Guide as this resulted in a few random yet annoying changes on my computer, like the font type and size being changed in my Firefox, without actually getting sound working.

However, following the instructions on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) made it work.  It seemed that the big difference was compiling it with my specific driver.  Lists of drivers for soundcards can be found at [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main).

Now my problem is that whilst sound works, I have to manually unmute surround sound in alsamixer after each reboot in order to hear anything.  I've posted a query about that at [http://ubuntuforums.org/showthread.php?p=3341577](http://ubuntuforums.org/showthread.php?p=3341577), so if anyone experiences that and figures out a solution, please let me know!

---

### Post by bilbopingouin on 2007-09-11
Hi!

I had the same problem. After an update that I did yesterday, I restarted and no sound. Exactly the same problem.

I also "solved" it by going back to the 2.6.20-15 version of the kernel.

For those who don't know how to do it (I just learned from a friend), please have a look in /boot, and there you will find a couple of files, and among those, some files with the kernel version. If you have some 2.6.20-15 there, this means that most likely (depending on your configuration) you can choose to boot on it at startup (e.g. with grub).

In my case it was not.  So I used synaptic and searched for the files installed for the kernel 2.6.20-16. And installed the same for the previous. Then I rebooted and chose in grub to boot on the previous one.

Still it is not a solution. And sahra may be going to the real solution (but I didn't like the remaining bug ;-) ).

---

### Post by dxxvi on 2007-10-21
My situation is a little different. I installed a new Gutsy. The volume control works well in the user created when I did the installation. Then I created another user with useradd and the volume control doesn't work there.

---

### Post by twizler on 2007-10-25
,-O 
      O(_)) Ubuntu GUSTY 7.1
       `-O  
H[COLOR="DarkGreen"]OW TO FIX[/COLOR]
 [COLOR="Red"]No volume control GStreamer plugins and/or devices found.[/COLOR]


___[COLOR="DarkGreen"]_THIS WORKS!!___[/COLOR]
I had to do this on all our new DELL computers at work.
_____THE FIX_____________
TONS Dell desktops and laptops have an Intel on board integrated card that is not supported by default in Gusty 7.1.
Intel Corporation 82801H (ICH8 Family) HD Audio Controller integrated sound.
This is geared for dell laptops and Desktops plus others brands like hp/gateway: On Gusty 7.1.
Verify you have an Intel Sound card
--WARNING---DO NOT run script ./d630alsa.sh at the end of how to  step 4.  unless you hv 
the exact model Intel Corporation 82801H (ICH8 Family) HD Audio Controller 
integrated sound.   

1. open Terminal
applications --> accessories --> Terminal  

lspci -v | grep Audio

*make sure the A-in Audio is capitalized. 
Should look like: 
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
((((((If U dont have the above card U may want to search for a fix for the card listed in your Audio)))))))
______________________________

2. open-->system --> Admin. --> Synaptic Package Manager-

Search for --ALSA --
Install the list below- 

       gnome-alsamixer
	gstreamer0.10-alsa
	gamix
	libpt-plugins-alsa
	linux-sound-base
	asoundconf-gtk
	gom 
Install all appps that start with alsa: in Synaptic
(quite a few like 15 apps)
	alsa-firmware-loaders
	alsa-playerXXXXXfoo *** keep going down the list:
______________________

3. In terminal

sudo apt-get install libncurses5-dev
sudo apt-get install linux-backports-modules-generic

__REBOOT____ 
SOUND :) Upon reboot [CENTER]Your sound Should be working!!!! 
       
________________BONUS___
[COLOR="Red"]If still no sound is working and you have the intel card go to step 4 
WARNING _____ONLY DO step 4. if you have Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
_______you have rebooted and still your Intel card didn't work *(mainly on DELL machines) 

Step 4. Script For Intel Corporation 82801H (ICH8 Family) HD Audio Controller
(Special Thanks to Martti Kuparinen who wrote this compile from source Auto "magic" script to do everything) 
[COLOR="Red"]
4.WARNING _ INTEL CARD ONLY[/COLOR]
	A.  IN Fire Fox open site 
     [http://users.piuha.net/martti/comp/d630/d630alsa.sh](http://users.piuha.net/martti/comp/d630/d630alsa.sh)
      Download installer 
__________________      

      B. In Terminal:

            sh ./d630alsa.sh
__________
   =compiling ALSA:
___________  Press ENTER a few times... because this is compiling source.
_______________-Once it is done Reboot ___________ 

SOUND :)[/COLOR]

---

### Post by xehpuk on 2007-11-04
I had same thing as dxxvi. In my system it worked for 3 users but not for 2.
Under "Users and groups" there is properties for each use, the 2 users 
were not allowed to use audio...

---

### Post by The_Great_Beast on 2007-11-08
Thanks [this worked]("http://ubuntuforums.org/showpost.php?p=3633314&postcount=11") great!

---

### Post by nafetski on 2007-11-10
I.  LOVE.  YOU.

If you are ever in Tampa I want to buy you a drink.  You have saved me so much time.

---

### Post by ramka001 on 2007-11-14
Dude,

Brilliant work.

---

### Post by Fred_S on 2007-11-16
I see someone got their problem fixed, wondering if someone could help me.

I have:
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev3)
My computer is a acer aspire 5720Z or ZG.

Even tho the model wasnt exactly the same i tried this out but it didnt work.

Help much appreciated.

---

### Post by KGT on 2007-11-17
twizler this worked great!! you rock! :guitar:
thank you for the solution :)

> **twizler said:**
> ,-O 
      O(_)) Ubuntu GUSTY 7.1
       `-O  
H[COLOR="DarkGreen"]OW TO FIX[/COLOR]
 [COLOR="Red"]No volume control GStreamer plugins and/or devices found.[/COLOR]


___[COLOR="DarkGreen"]_THIS WORKS!!___[/COLOR]
I had to do this on all our new DELL computers at work.
_____THE FIX_____________
TONS Dell desktops and laptops have an Intel on board integrated card that is not supported by default in Gusty 7.1.
Intel Corporation 82801H (ICH8 Family) HD Audio Controller integrated sound.
This is geared for dell laptops and Desktops plus others brands like hp/gateway: On Gusty 7.1.
Verify you have an Intel Sound card
--WARNING---DO NOT run script ./d630alsa.sh at the end of how to  step 4.  unless you hv 
the exact model Intel Corporation 82801H (ICH8 Family) HD Audio Controller 
integrated sound.   

open-->system --> Admin. --> Synaptic Package Manager-

Search for --ALSA --
Install the list below- 

       gnome-alsamixer
	gstreamer0.10-alsa
	gamix
	libpt-plugins-alsa
	linux-sound-base
	asoundconf-gtk
	gom 
Install all appps that start with alsa: in Synaptic
(quite a few like 15 apps)
	alsa-firmware-loaders
	alsa-playerXXXXXfoo *** keep going down the list:
______________________

In terminal

sudo apt-get install libncurses5-dev
sudo apt-get install linux-backports-modules-generic

__REBOOT____ 
SOUND :) Upon reboot [CENTER]Your sound Should be working!!!! 
       


---

### Post by fmontealegre on 2007-12-22
Hi guys I'm new in Ubuntu and I just installed Gupsy 7.10. I have the same problem for a Dell Inspiron 1520, I already  try the solution of twisler but I god this 
$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libncurses5-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libncurses5-dev has no installation candidate

so what's de source I should use? 

PLS help!!!

---

### Post by fmontealegre on 2007-12-23
Hi again guys, IT WORKS!! IT WORKS!! 
I changed mi sources.list as it says in _[http://users.piuha.net/martti/comp/ubuntu/en/install.html](http://users.piuha.net/martti/comp/ubuntu/en/install.html)_ and it works

TNX a lot!!!

---

### Post by kwalsh on 2008-06-23
This is very much appreciated and works a treat. Great work.

---

### Post by ayeshap on 2008-06-23
i tried everything from twizler's post and it still isnt working. i dont know if i'm doing something wrong or if its just my laptop.
i have a dell inspiron 1525 and i just upgraded from ubuntu 7.10 to 8.04 and now the volume control isnt working.
is there some way to go back to 7.10 since nothing is working for me to fix this problem? i got the same thing as fmontealegre

$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libncurses5-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libncurses5-dev has no installation candidate

i don't understand these codes at all and i have no idea what it means to change my sources list or what to change it to.

PLEASE HELP!!

---

### Post by MarmiteMonkey on 2008-07-07
ayeshap, I hope you're not still stuck without any solution after two weeks. If you are, however, read on.

I had what seems to have been the same problem as you. I received a brand new Dell Inspiron 1525 laptop today, with Ubuntu Gutsy 7.10 preloaded. Sound worked fine out of the box. I then promptly installed Hardy 8.04, and the sound broke. Twizler's solution didn't help. This, however, worked like magic:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

I also installed the new modem driver for 8.04 (as mentioned on that page), just in case I might ever need it. Then I opened up Synaptic, went into File > History to get a list of all the packages that I had installed when following Twizler's solution, then located all of those packages and did a "Mark for Complete Removal" on all of them.

Who would have thought that the lost sound would be due to a **modem driver**?

---

### Post by ayeshap on 2008-07-07
the thing is i tried this site also and it didnt work.
however my sound does work now but it required me to change the default kernel from 2.6.24-18-generic to 2.6.24-16 generic.
i have no idea why nothing i tried on 2.6.24-18-generic worked 

i actually dont even know what difference it makes between which kernel i boot in tho...

---

