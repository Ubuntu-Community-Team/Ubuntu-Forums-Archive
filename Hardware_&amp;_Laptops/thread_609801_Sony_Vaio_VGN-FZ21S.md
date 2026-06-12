---
title: "Sony Vaio VGN-FZ21S"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by AlanR8 on 2007-11-11
Just bought the above and took GREAT delight creating rescue discs (Vista Home) then installing Gutsy (Kubuntu)!

Core 2 Duo
2 Gigs RAM
200 Gig HD
Blu Ray/CD/DVD
Nvidia GeForce 8600M

Generally everything went well. The FN keys were not recognised but the Jog wheel was and works perfectly in Amarok to skip between tracks, stop, pause play etc. It also controls the volume.

The built in Bluetooth is giving me some issues. The icon remains greyed out and I can't pair to my phone. 

The other thing is the headphone socket is not recognised, neither is the built in mike and Motion Eye camera.

I can live with these inconveniences for now, but are there any fixes, tips etc you can point me to?

---

### Post by pascalc on 2007-11-12
I have almost the same model, VGN-FZ21S (your model without the blueray disk)

Things that do not work:
- mic and earset
- suspend to ram / suspend to disk
- brightness control via the gnome applet or keys (you can use the nvidia settings for that but it's not convenient)
- fn keys do not work except for mute, but the nvidia settings panel should allows switching to a beamer
- webcam

Things that work:
- SD card slots
- screen switched off when closing the lid

---

### Post by AlanR8 on 2007-11-13
Not using Ubuntu, using KUbuntu. Any thoughts or tips around the original post?

---

### Post by paraglider on 2008-01-04
Just got the same laptop, and since windows vista doesn´t inspire much confidence I´m dying to set up a dual boot with ubuntu or kubuntu. I have absolutly no experience using linux OS so forgive me if I ask stupid stuff!

I´d really apreciate a hand with a few questions I have before I go about messing with my HD.

:confused: what hard drive partitions should I do? I have a 200GB HD but at the moment its apparently got 136 GB free (20GB seem to be windows (?), i think it has a hidden partition of 10GB for the system recovery and total size stated of C:/ is 176GB - 14GB unaccounted for)

Basicly i´d like to do as little as posible in Vista, except maybe some photo and video editing in the future since it came with photoshop and premiere...

:confused: what goes better for this laptop, ubuntu or kubuntu? 

:confused: anything special I should consider during install. (all i know is from going through the online ubuntu guide)

Any luck with those f- keys, mic, cam, bluetooth...?

Happy new year and thanks in advance!

---

### Post by AlanR8 on 2008-01-04
Hi paraglider and a Happy New Year!

There's a hidden partition that has the recovery data so you can put your Vaio back to "out of the box" condition. First thing I did was found the Sony Recovery item on the Vista Start Menu and burnt the rescue discs, 2 DVDs! Next thing I did was install Kubuntu and used the whole of the hard disc!

Your choice of Kubuntu/Ubuntu...what ever floats your boat! Personally I like Kubuntu, and KDE4 is just round the corner, about 6 days away from launch.

The built in blue tooth has not been picked up. Despite "seeing" a blue tooth IP address, I've not got it to connect. The Motion Eye camera is a "known issue" and still not fixed, plenty about this elsewhere in these forums. 

The thing that annoys me more than anything is the fact I can't get sound from the head phone jack and plugging headphones in does not mute the speakers. The sound mixer shows HDA Intel but only shows a Master and PCM channel. If anyone can help me out with this one I'd appreciate it! The volume toggle wheel works, odd!

Finally, when installing, I'd recommend you have an internet connection live, saves problems later. I installed from the Live CD so activated the wireless in that session (password required). If using the alternative installation CD, text based, I've always used a wired connection.

Finally, it looks like my CD/DVD has failed, six weeks old huh......what can I say.

---

### Post by sojusnik on 2008-01-06
Hi,

Can you say something about the fan and how it sounds/acts with Ubuntu 7.10.
The next days I want to buy a Sony Vaio VGN-FZ21E and I'm hoping that the build-in fan is silent.

---

### Post by AlanR8 on 2008-01-06
The fan has been fine..no problems

---

### Post by sojusnik on 2008-01-06
Is it running on Idle or small office activities like browsing the web or using open office?

---

### Post by AlanR8 on 2008-01-06
It's running now very quietly whilst browsing and doing other stuff

---

### Post by sojusnik on 2008-01-06
Is it running constantly or even stops from time to time?

---

### Post by AlanR8 on 2008-01-06
Does stop. Key is it doesn't get hot

---

### Post by PokeParadox on 2008-01-29
Sorry to thread bump, but can someone please help.
I have a Sony Vaio VGN-FZ21S also and the main problem I have is that typing on the keyboard disabled the mouse for about one second. Does anyone know what would cause this behaviour and how to stop it?

Also my touch pad has somehow stopped working...

Finally I can't seem to get any bluetooth devices to connect to the laptop.

Please if anyone has any answer, I'd appreciate help!:KS

---

### Post by AlanR8 on 2008-01-29
I can't think of anything that would give your keyboard and track pad issues as I've not encountered them. (Don't forget I'm running Kubuntu not Ubuntu). Maybe someone else can pitch in with that one.

The Bluetooth is still an issue on my machine. Looking at System/Info Centre the device appears under USB devices as a Broadcom BCM2046 Device. Under Device Config in the Bluetooth application it appears and gives a MAC address and says it's connectable. That's the end of the good news though as I can't give the adapter a name, it just won't let me and I can't get the adapter paired or recognised.

Can someone offer any help on this?

The GOOD news is that I managed to get the headphone jack and mic to work! Yipee. After searching this forum I came up with this solution below, the fix for the sound is at the end of the quoted text am I give full credit to the author who's name I forgot to copy when I pasted the article into a word processing document. Sorry

> Sony Sound

I have a sony vaio fz21m runnung Gutsy (7.10) some problems did came up, but they are all fixed now.

after fresh installation do these things in the following order.

in [sofware sources] click these:

[Ubuntu Sofware]
x (main)
x (universe)
x (restricted)
x (multiverse)

[Updates]
x (gutsy-security)
x (gutsy updates)
(gutsy-proposed)
x (gutsy-backports) (this one you need later to enable the headphones-jack.

update system with Update Manager
and reboot.

install Envy, get it from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
envy will not be able to install without you enabling the tings in [software sources].

use envy to install the proper nvidia drivers.

Now for the audio-jack problem (sound refuses to come out trough the headphones-jack.)

Edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add this in the bottom of it

options snd-hda-intel model=vaio

then do this:

sudo apt-get install linux-backports-modules-$(uname -r)


do these things and enjoy your fz21m

---

### Post by PokeParadox on 2008-02-01
OK a little update.

I'm typing this on a completely fresh install of Gutsy and right now the keyboard is working fine and not cutting off the mouse when I type! :guitar:

So now begs the question, what on earth did I install previously that caused this behavior...?

Needless to say I'm going to tread very carefully as I setup software and download packages, because I really could do without that keyboard problem again!

---

### Post by ganxo on 2008-03-04
can you control the brightness of your monitor?

---

