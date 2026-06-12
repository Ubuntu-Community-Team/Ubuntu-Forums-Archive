---
title: "[SOLVED] Intrepid and Skype"
date: 2008-10-31
forum: General Help
---

### Post by Dyffo on 2008-10-31
Anyone have any experience of Skype ? -I have just upgraded to 8.10 and am having great difficulty  - all was O.K. with Hardy. My  problem is can't get the microphone to work. I can hear everything but the Echo test call reveals that no one can hear me. My sound card is set to Realtek - dvd etc all play O.k.Any help will be much appreciated !!

---

### Post by Dr.Suave on 2008-10-31
I had a quiet microphone problem with 7.10 - it was a pretty simple solution for me, the Alsa Mixer had the microphone muted for some reason...  

I just double clicked the volume control in the taskbar to bring the mixer up, then went into edit > preferences and ticked all the boxes that could have anything to do with my microphone, then more browsable tabs appeared in the mixer, which I went through making everything was turned right up. My microphone was then too sensitive and had to be turned down a bit.

I don't know how things are with the alsa mixer in 8.10 - I'm still procrastinating about upgrading from Gutsy, and I hear some changes have been made, with PulseAudio being involved and all that business, but I hope this works for you.

Wilf

---

### Post by btermeli on 2008-10-31
I did like this,

system> preferences> sound
devices tab, set all devicese to alsa

sounds tab, disable "play system sounds"

open terminal;

sudo apt-get remove pulseaudio

sudo apt-get install esound

and restart, now it works but I still have problem with web camera :( :(

---

### Post by Dyffo on 2008-10-31
> **btermeli said:**
> I did like this,

system> preferences> sound
devices tab, set all devicese to alsa

sounds tab, disable "play system sounds"

open terminal;

sudo apt-get remove pulseaudio

sudo apt-get install esound

and restart, now it works but I still have problem with web camera :( :(
Sure  does work - ALL well now. What is your problem with the Videocam - I had to change mine to a Logitek - works O.K. now

---

### Post by kainalu on 2008-11-01
I have the same audio problem. is there a solution that allows me to keep pulse?

---

### Post by Dyffo on 2008-11-01
> **kainalu said:**
> I have the same audio problem. is there a solution that allows me to keep pulse?
Yes you can keep Pulse. Follow the thread :

[http://ubuntuforums.org/showthread.php?t=965689](http://ubuntuforums.org/showthread.php?t=965689)

It worked for me !! Good Luck

---

### Post by Dyffo on 2008-11-01
> **Dyffo said:**
> Yes you can keep Pulse. Follow the thread :

[http://ubuntuforums.org/showthread.php?t=965689](http://ubuntuforums.org/showthread.php?t=965689)

It worked for me !! Good Luck
SORRY _ THE LINK SHOULD HAVE BEEN :-

[http://ubuntuforums.org/showthread.php?p=6068479](http://ubuntuforums.org/showthread.php?p=6068479)   this should get you out of trouble !!

---

### Post by himanshuprakash on 2009-08-21
Hi Dyffo,
it works for my lenovo Y410.
Thanks a ton.

---

### Post by himanshuprakash on 2009-08-22
Hi Dyffo,
got any solution for vedio confrencing using Skype 2.0 for Linux?

Thanks

---

