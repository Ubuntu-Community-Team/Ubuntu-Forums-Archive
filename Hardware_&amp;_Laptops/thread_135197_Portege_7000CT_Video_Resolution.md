---
title: "Portege 7000CT Video Resolution"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by zerubbabel on 2006-02-23
I installed Kubuntu 5.10 on a Toshiba Portege 7000CT, and the install went fine, but it doesn't seem to recognize the video capability. It's showing a poor image at 640x480 resolution, and doesn't give me the option to switch to the full 800x600 resolution.

The video controller, according to Toshiba is:
NeoMagic (2160) w/128-bit bus
PCI Bus Compatible 32bit 33Mhz
800x600x16.7M @ 85Hz/60Hz

---

### Post by barely hi-fi on 2006-03-12
I'm having EXACTLY the same problem with an otherwise perfect install of UBUNTU 5.10 on my Toshiba Portege 7010CT.  Did you manage to fix it?\\:D/

---

### Post by barely hi-fi on 2006-03-12
update: I've tried the guidance contained in this thread:  [http://ubuntuforums.org/showthread.php?t=142608&highlight=resolution+laptop](http://ubuntuforums.org/showthread.php?t=142608&highlight=resolution+laptop)

All seemed well (800x600 resolution found by the utility) but when it came to amending the screen resolution in the settings menu, the only option there was remained 640x480.  I'm stumped, please help:-k

---

### Post by barely hi-fi on 2006-03-13
Argh!:eek: :mad: 

I'm in the process of following every piece of advice I can find on this subject - I'm now fully up to speed with the **destructive power** of the sudo command and I am currently attempting to recover the GUI for the second time this evening.  All I can say (and I'm really not looking for flames here) is thank GOD (and every other deity) that I have a win xp machine to fall back on to download further help from you guys!  I just wish that it would materialise sometime soon! :rolleyes: 

Again - umbongo seems to detect the capabilities of my old laptop's monitor but doesn't allow me to select it.  Please HELP, I'm really trying hard to be a convert! :-k 

My enthusiasm is failing rapidly and yet my wireless connection with a bit of fiddling was up and running no probs at all - great OS - HELP!!!!!!!!!!!!!!!

---

### Post by zerubbabel on 2006-03-14
No, I never succeeded in getting mine to work either. Still waiting for the magic formula...

---

### Post by da2na on 2006-04-02
Try editing you xorg.conf file:

sudo vi /etc/X11/xorg.conf

Scroll down to the Monitor section and make the following changes:

       HorizSync       31.5-48.5
       VertRefresh     50-90


Scroll down further to the Display sub-section and add "800x600" to the Subsection with your DefaultDepth, should be 24:

       SubSection "Display"
                  Depth              24
                  Modes             "800x600" "640x480"

After you make the above changes, restart your laptop.  Once you log-in, you should be able to go System>Preferences>Screen Resolution and see the new options.

Hope this helps,

-da2na

---

### Post by barely hi-fi on 2006-05-14
I managed to solve this a while ago: unfortunately, I don't have a clue how!  So, I didn't really solve the problem, I just stumbled upon a happy accident!:) If I knew how, I would have posted a solution - honestly!. 

Unfortunately, I've been forced to install a new disk on this laptop: so, these probs have re-emerged.  Unfortunately, the sudo command offered in other threads (and indeed the great advice above from da2na) are no longer useful as I don't have read/write access to /etc/x11/xorg.conf and apparently, xserver.xorg is not installed on this machine (it was before!).

Help please!

---

### Post by barely hi-fi on 2006-05-18
Wow - this worked!!!  and I've stopped doing this: ](*,) 

This might even be a definitive solution...

In my recent install, I seemed to have fewer priviliges than previous installs, and was unable to alter certain files.  The solution was:

- open terminal and type:  sudo nautilus
- enter password

Thereafter I simply followed the great advice offered previously by da2na - Hey presto... I can see dialogue boxes and stuff!

Thanks da2na!

---

