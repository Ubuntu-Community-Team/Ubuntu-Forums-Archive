---
title: "Live CD X server failed"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by R_MAC on 2006-02-11
I downloaded the latest Breezy Badger Live CD boot image,
burned it to CD/ISO in W98se.

Live CD boots, goes thru all the screens, incl. graphic logo, hardware detection, etc, After 10 min. or so gets to a coarse blue screen that says "Failed to start X server gui..." etc. and dumps me at a "ubuntu:~$" prompt. 
If I enter "startx" or "sudo startx" (my limit at Unix commands) it cycles thru messages about the X server failing etc and returns to prompt. What now???

As per other threads tried "sudo dpkg-reconfigure xserver-xorg" 
and took all defaults except graphics card=VESA, OS immediately replied with 
"Dummy template for processing unavailable question [false---]... 
if you see this template, you have found a bug- file a report". 
Then entered: "sudo startx", Msgs returned:

"creating new auth file, 
creating new /home/ubuntu/.serverauth .18763, 
creating new /home/ubuntu/.xauthority (2 times), 
giving up, 
xinit:connection failed (errorno 111), 
xinit: no such process (errorno 3),
server error",
-$ prompt (again)

Someone in the new user forum suggested I "look in /var/log/Xorg.0.log (or /var/log/xorg.0.log) to see exactly what is the problem". 
How do I "look in /var/log/Xorg.0.log (or /var/log/xorg.0.log) to see exactly what is the problem" ?? 
HELP!!!
(Please forgive, I am a Linux newbie and know very few Linux commands) 

Gateway "Essential" Desktop
PIII- 450mHz
W98se
256mb ram
nVidia GeForce2 MX/MX400
Sony CPD-100ES 15" monitor
IBM 10gb IDE pri
Seagate 10gb IDE slave
SoundBlaster 128
Network Everywhere ethernet 10/100 card/cat5e 
Linksys DSL  router-firewall-10/100 swt

---

### Post by arckeda on 2006-02-11
xserver driver wrong in termial type
sudo dpkg-reconfigure xserver-xorg
then selsect vesa and if that dont work vega thne after you setup type
startx

---

### Post by R_MAC on 2006-02-11
Tried VESA- see above for results. Explain rest of your response??

---

### Post by arckeda on 2006-02-11
try vega or if that dont work ATI

---

### Post by arckeda on 2006-02-11
well you shold check your graphics driver and who made it and select it, if its not their their may be a bigger problem, i dont know what to tell you other than that.
and if your not in desktop yet, you dont need sudo

---

### Post by R_MAC on 2006-02-11
Video is Nvidia geForce2.

---

### Post by arckeda on 2006-02-11
isnt their a Nvidia driver option, i think i saw it.

---

### Post by R_MAC on 2006-02-11
I believe the 1st boot picked the "nv" graphics option, failed too.
That's why I started in the forums for help-- thanks.

---

### Post by R_MAC on 2006-02-12
SUCCESS!!-- CD boot image was made on CDRW on 1 drive & booted on another.  Once booted from original burner drive, all worked like a charm- went right to desktop and I'm using it now to reply to this thread. Mouse is very ssslllooowww but workslThanks for all who tried to help.

---

