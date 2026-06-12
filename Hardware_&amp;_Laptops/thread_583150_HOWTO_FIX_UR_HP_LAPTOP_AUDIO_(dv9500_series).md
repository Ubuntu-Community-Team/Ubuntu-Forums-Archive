---
title: "HOWTO FIX UR HP LAPTOP AUDIO (dv9500 series)"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by DRAGONPOWER on 2007-10-20
OK after 2 days of testing I have found a fix for the lil' orange audio button all hp laptop users have ... well , on their laptop panel above the keyboard. 

First off download the latest ALSA stuff:

[ALSA Drivers 1.0.15]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")

[ALSA Lib 1.0.15]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2")

[ALSA Utils 1.0.15]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2")

[COLOR=DarkRed][SIZE=5]CHECK VERSION PLZ, U HAVE TO USE 1.0.15!!!!!!!!!![/SIZE][/COLOR]

Once u get these files, make sure u follow the setup next up yes, ONLY CHANGE NUMBERS IN TERMINAL, OK just type in a 5 instead of 4 on this guide:

[UBER GUIDE]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

any questions i be glad to help. 

Piece! :KS

[SIZE=7] REMEMBER TO LOGIN AS ROOT!!![/SIZE]

---

### Post by Thanawho on 2007-10-21
Looks like you got this to work....However I'm having trouble with part of the user guide.

This part is throwing me off. I downloaded all three files to my home folder but I cant get them. Can you explain this code/post the code that you used? (I dont know what the * means either) Where do the downloaded files need to be?

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
**sudo cp ~/downloads/alsa* .**  (Trouble here and cannot continue the rest)
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

I get this error:
cp: omitting directory `/home/webster/downloads/alsa'

I get this error when i try to continue
tar: alsa-driver-1.0.15.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

btw I'm using HP dv6500 with Intel HDA and ALSA 1.0.14.


[B]
UPDATE: I figured out how to run this and did it successfully, Now the blue light is back, but my sound card is not recognized. What now???![/B]

**UPDATE 2: I ran the following commands:**
* sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

and now my sound card is recognized, but the orange light is back on. it says in alsamixer now that i am running 1.0.15, as before it was 1.0.14. WHAT IS GOING ON

---

### Post by DRAGONPOWER on 2007-10-22
Hi. I'm no expert but I will try to explain.

[SIZE="4"]sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* . 
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2[/SIZE]

Erm, third line, copy the whole line into the console. with the * and the dot.

Now this part here, cause me trouble, The install wouldn't let me sudo cp ~/downloads/alsa* because the folder wasn't there. Simply create a folder and add the alsa files, and then run the installation from ur created folder, e.g. sudo cp ~/alsastuff/alsa

I actually had to run root user to fix this because normal user didn't grant me enough privileges.

My advice tu you is to login as root, and retry this with the correct folder names. Download the 3 alsa files, save them in a location, and follow the Ubuntu guide to compile them. This worked for me, blue light, good sound.

---

### Post by Thanawho on 2007-10-22
**FINAL UPDATE**: Problem fixed. Mad props to this guy for finding a way to fix it  here: [http://ubuntuforums.org/showthread.php?t=565873&highlight=sound+problem+hp&page=2]("http://ubuntuforums.org/showthread.php?t=565873&highlight=sound+problem+hp&page=2")

---

