---
title: "Gutsy And laptop sound cards"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by fedex1993 on 2007-10-18
okay ever sence i download intalled gutsy which was today now i cant seem to get my sound properties or even the sound working. I have a toshiba a135-4357 laptop please help thanks

---

### Post by geetarobob on 2007-10-18
I have a Toshiba A-135 S4477 and experienced the same issue upon Gutsy install

I used: sudo gedit /etc/modprobe.d/alsa-base

and then once the file opens add: 

options snd-hda-intel position_fix=1 model=3stack

 after this you will be blessed with sound unfortunately so will the people near you because the sound will play over your pc speakers and headphones. I have searched as many forums i could find and still have not found a fix for this I feel like i have tried everything. Hopefully someone reading this can help.

:confused:

---

### Post by bloodyserb on 2007-10-18
Hey, after trying a bunch of other fixes, that one did it for me too!  Now if only someone can find a way around the headphone problem that's just as simple.

---

### Post by dare dukes on 2007-10-19
Thank you, thank you.  I installed Feisty on my Toshiba A135 and lost sound.  Upgraded to Gutsy yesterday, and your fix gave me sound again.  Sure, the headphone issue is a vague annoyance, but rarely an issue for me.  Thanks!

---

### Post by senken12 on 2007-10-19
I did that, still doesn't work on my Toshiba A100

---

### Post by ceaseoleo on 2007-10-19
"No volume control GStreamer plugins and/or devices found." .. I'm receiving this message after upgrade :(

---

### Post by bloodyserb on 2007-10-19
After enabling all the restricted formats my sound has now stopped working.  Unfortunately there are no errors to search on, it's just not there anymore.  That line that fixed it above is still there.  Any ideas?

---

### Post by fumoffu on 2007-10-20
Mmmk, I have a Toshiba Satellite A105. I had no sound, but got it working perfectly by using the fix provided here, only with a small change:
 options snd-hda-intel position_fix=1 model=auto

Sound works fine through Headphones and does not come through speakers at the same time. Let me know if this works for you guys :) 

-Gutsy Rules

---

### Post by jackietheblade on 2007-10-23
Hey guys. First time poster, but have been scouring the forums for months looking for an audio fix for my sisters computer and this looks like the closest thing so far. So here's where were at:

She has a Toshiba A130 updated to Gutsy. Looks to be a Realtek Sound card (is that what everyone elses Toshiba's are running here?). We tried the fix and it doesn't seem to have worked, but this was my first time editing system files so we may have missed something. 

I had her run gedit which opened the file. Then, she just added the fix:

options snd-hda-intel position_fix=1 model=auto (direct copy and paste to avoid mistakes)

to the bottom of the file...saved and closed. Restarted the computer and got a long error as well as a life preserver on the menu bar at the top. And she is still unable to "unmute" her audio. 

Any ideas? I appreciate any help guys. She is a new user...moved her straight from Vista to Ubuntu. She loves it, but now if we could just get the audio working, it would be perfect!

---

### Post by crazyforpurple on 2007-10-24
I ahve a toshiba satellite A135-S7404 and today I got my sound working!! below is a list of what i did, I actually got the info from this link:

[http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)

but below is specificatlly what I did:

hope this helps xxx

love lucy xxx


1. after installing ubuntu gutsy i had no sound and no sound cards were detected.
2. when i tried the command "cat /proc/asound/cards" it would just say no soundcards installed
3. i couldnt even find these files....
"Remove ~/.asoundrc and ~/.asoundrc.asoundconf."

let alone remove them! so i went on to the next step:

4. i then went onto your next step:
"Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot."

to do this i did the following:

go to system, administration, synaptic package manager,
type in your password
in synaptic package manager, go to settings, repositories

under the "ubuntu software" tab I checked on each entry under "downloadable from the internet" and unchecked the cd/dvd option.

then under the "updates" tab I checked everything including the gutsy backports.
close the repositories box and then click reload in the synaptic package manager.

5. I don't think its necessary at this time but I restarted my laptop for good measure at this point.

6. I then went back into the synaptic package manager and ran a search for backports

7. I also went to applications, accessories, terminal and ran the following command
uname -r to find the details of my kernal.

it came back with 2.6.22-14-generic

8. In the synaptic package manager I had many options from my search and I wasnt sure which one I should use... I narrowed it down to

linux-backports-modules (which in the info said "Generic Linux backported drivers.")
and
linux-backports-modules-gene-2.6.22.14.21 (which in the info said "Backported drivers for generic kernel image")

I'm not quite sure why, but I clicked on the latter on and marked it for install. I then clicked "apply" and once it was all done I restarted the laptop and on restart I had sound!!!!!!


This may not be worth noting but when I use the term "restart" I actually shut down and then start up the laptop as using the "restart" option on mine means that it hangs before the log in screen.

---

### Post by fedex1993 on 2007-10-24
i got my sound working from the second post only problem is my front sound port and mic dont work :(

---

### Post by svenerikjensen on 2007-10-25
No change for me at all. Got a VIA soundcard of some type on my Fujitsu-Siemens laptop (2 types are shown actually, 1 for alsa and 1 for oss, whatever that means). Everything looks allright, except there's not any sound from the speakers. Haven't tried with headphones yet. Appearently VIA says that the ALSA driver doesn't work, so I need to figure out how to compile the new drivers from them and stuff. Can I use drivers made for Feisty Fawn on Gutsy? No drivers are out yet for Gutsy as far as I can tell.

---

### Post by Smiley-Man on 2007-10-25
Success.

Toshiba Satellite Pro A100

Used:-

sudo gedit /etc/modprobe.d/alsa-base

And added

options snd-hda-intel position_fix=1 model=auto

Sorted and thanks. =D>

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

### Post by flar on 2007-10-25
Sound on my Acer 5570 laptop's hda-intel  worked, but works much better with the latest alsa driver.  Out of the box I had to unmute surround, and the surround mixer controlled the volume.   With the latest alsa driver, volume is controlled by the proper front mixer, meaning that the laptop's function keys now control the sound perfectly.  Also with the latest alsa driver, the headphone jack sense works.

---

### Post by wford002 on 2007-10-26
Thanks, I was skeptical that I would ever get sound, and there was so many things to install, but it worked! very happy, now I just need to figure out how to mute the speakers when headphones are in.

Also for reference for other people wondering if this will work; I have an intel 82801 G (ICH7 family) sound card.

---

### Post by jackietheblade on 2007-10-26
Thanks to Lucy for the fix! 

Don't know if this will work for anyone else, but here's what my sister did on her Toshiba A130:

Open Terminal. Type this: **cat /proc/asound/cards** and hit enter

Response came back showing HDA Intel Audio. Sound works. 

It was VERY simple but again, can't promise it will be that easy for everyone.

---

### Post by One World on 2008-05-03
Did not worrk for me but thanks for the effort Twizler.

```

sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

```

```

 wget http://www.iki.fi/kuparine/comp/d630/d630alsa.sh
--14:57:25--  http://www.iki.fi/kuparine/comp/d630/d630alsa.sh
           => `d630alsa.sh'
Resolving www.iki.fi... 212.16.100.1, 212.16.100.2
Connecting to www.iki.fi|212.16.100.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.piuha.net/~martti/comp/d630/d630alsa.sh [following]
--14:57:25--  http://www.piuha.net/~martti/comp/d630/d630alsa.sh
           => `d630alsa.sh'
Resolving www.piuha.net... 193.234.218.130
Connecting to www.piuha.net|193.234.218.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://users.piuha.net/martti/comp/d630/d630alsa.sh [following]
--14:57:25--  http://users.piuha.net/martti/comp/d630/d630alsa.sh
           => `d630alsa.sh'
Resolving users.piuha.net... 193.234.218.130
Reusing existing connection to www.piuha.net:80.
HTTP request sent, awaiting response... 404 Not Found
14:57:26 ERROR 404: Not Found.

```

---

