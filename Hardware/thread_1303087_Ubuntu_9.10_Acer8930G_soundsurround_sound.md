---
title: "Ubuntu 9.10 Acer8930G sound/surround sound"
date: 2009-10-27
forum: Hardware
---

### Post by RiggsUSA on 2009-10-27
Don't no where to start.
I have an Acer 8930G Laptop.
Testing Ubuntu 9.10 32bit
Intel core 2 DUO (2.0GHz) T6400
3GB Ram

There is no stereo sound it is mono, if i move the balance slider left to right it moves the sound front to rear.
if i select 5.1 surround sound will only come out of the LFE (Subwoofer).
Any body got any ideas.

---

### Post by prabath_fun on 2009-10-31
Hi,
   Where I can find this LFE settings....... In Ubuntu9.04 It was available through volume icon. I just tried Ubuntu 9.10, I could not able to find it? Is it, I need to install Alsa / Pulse audio???????

Please update me....

Prabath

---

### Post by RiggsUSA on 2009-10-31
I could never get the sound working right in 9.04. 
But for 9.10 you need right click on the volume (speaker icon next to the time),
click on the hardware tab, at the bottom you should she a drop menu (Settings for selected device:) Profile (mine says alalog stereo duplex) click on it and select (analog Surround 5.1 Output + Analog Stereo Input) then select (Output tab) at the top).

remember i am using acer 8930g this maybe different for each computer.

---

### Post by prabath_fun on 2009-11-01
Hi RiggUSA,
   The way you described, I got in Ubuntu 9.04. But, In ubuntu9.10 I am seeing any such options. Ubuntu 9.10 is not detecting my on-board sound chip RLC-883... Other than this all other features are good in Ubuntu 9.10. I tested, and happy with it. If I get this as well,. Will not think about going back to Ubuntu9.04..

---

### Post by RiggsUSA on 2009-11-01
Sorry but i have no idea, I'm new to Linux, came over to Linux for the server side as i did not want to pay large amounts of money for basic server stuff, I jumped into to linux at the deep end, LOL.
Then after seeing how stable it was I started installing it on all my computers, so yeah im learning, im hoping to get help with my sound problem too.

---

### Post by cwsnyder on 2009-11-08
I also have a Realtek 883 on-motherboard sound system.  Sound worked on the Live CD of Karmic Koala (Ubuntu 9.10), but didn't when I installed.  As a matter of fact, according to the System > Preferences > Sound, I didn't have any recognized hardware!!!

I am stumbling around looking, but I have lost the link right now, but I found a suggestion to add a different user.  According to the thread, a new user has a different set of defaults than the default user in a new setup.  Guess what?  Sound works on the new user.  Now I have to decide if it is worthwhile to dig into what the differences between the different installs are.

---

### Post by darkshadow on 2009-11-08
I have a 8940G and well setting up my sound I came on info that could help you. The newest version of Alsa specifically mentions the 8930G so I recommend updating to it (it is newer then the built in Ubuntu version)

add this to your software sources "ppa:thefirstm/karmic-testing" then add "options snd-hda-intel model=acer-aspire-8930g" to /etc/modprobe.d/options then run update-manager and reboot after it is done

---

### Post by prabath_fun on 2009-11-09
No improvement....
Prabath

---

### Post by RiggsUSA on 2009-11-10
it did not work, channels are still mixed up, only this time i got a high pitched noise from the speakers and when i was adjusting the balance it sounded like the speakers had lose wires. 
And no all hardware on the system is as perfect as can be.

---

### Post by RiggsUSA on 2009-11-21
I ran the Alsa info script and heres the output [http://www.alsa-project.org/db/?f=20d601f0174f8b53f7e7f31381e369768f7df647](http://www.alsa-project.org/db/?f=20d601f0174f8b53f7e7f31381e369768f7df647)

---

### Post by prabath_fun on 2009-12-01
Hi,
 I got 5.1 speaker supports with Ubuntu 9.10 as well.

I followed the following steps and got succeeded.
1. Take backup of /etc/pulse/daemon.conf.
2. Edit /etc/pulse/daemon.conf with text editor.
I used gedit tool triggered from terminal as follows
Sudo gedit /edit/pulse/daemon.conf
3. Scroll down to 
;default-sample-channels=2 
option.
a. Uncomment it. That is, remove “;” symbol at starting.
b. Change 2 to 6 for 5.1 channels / speaker.
4. Open "alsamixer" by typing same in terminal.
5. Verify surround, LFE are not muted and channels for 6.
6. Restart system to take changes get effect.

That’s it. I got it worked. I saw the change in sound card selection in preference from right click on speaker icon as “ALC883 5.1……….”.

7. Further checked the VLC player output also, by setting 5.1 surround supports in there preferences.

I am too happy with Ubuntu9.10 as it works faster than Ubuntu9.04, got all the necessary softwares like office, KDE, Audacity, VLC player, Virtual box, etc., Thanks to canonical / Ubuntu team.

---

