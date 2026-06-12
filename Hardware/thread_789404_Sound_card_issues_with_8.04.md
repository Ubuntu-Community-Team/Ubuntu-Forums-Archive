---
title: "Sound card issues with 8.04"
date: 2008-05-10
forum: Hardware
---

### Post by UnderRedMountain on 2008-05-10
Ever since upgrading to 8.04, I've been having issues with my sound card. Sound quality is pretty bad, but I think that may have more to do with my new motherboard than anything. The real problem I'm having is when I have two audio programs open at once, which ever program I open first is the only one that I can use. If I open banshee first, then I don't get sound out of firefox, etc.

It's getting old, and I haven't got the slightest idea how to fix it. I don't know how to find out what sound card I have...
Haha I'm pretty lost, any help would be greatly appreciated.

Thanks,
Joe

---

### Post by Xi0N on 2008-05-18
I have exactly the same problem.
My sound card is a C-Media CMI8738 that was working perfectly in the previous releases of Ubuntu.
My problem is exactly the same, and it happens everytime i watch some videos on youtube..... after closing the page, the sound all along the system gets blocked... and even i open amarok, or whatever sound app, i dont get any output.
This problem gets on my nerves because i have to restart many times during the day because of it.

Any help????

---

### Post by ukch on 2008-06-26
Just a shot in the dark, as I'm not entirely sure how these things work nowadays, but years ago when I used to have similar problems these could be fixed by restarting esd. Have you tried that? It should be as simple as starting a terminal and typing 'esd'.

---

### Post by Odrodzona-Sarmacja on 2008-06-27
I had issues like that myself. Configuring all my players and programs to use ALSA only sound driver fixed my sound issues. Also wine on my C-Media device on my Xubuntu was doing very badly on other sound devices but ALSA.
However it may be as well some codec conflict issue.
Good luck with figuring it out :)

---

### Post by Nepherte on 2008-06-27
This is a known issue of PulseAudio. It blocks access to the sound card for the second, third, ... application that uses sound. You can fix this following this tutorial: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Odrodzona-Sarmacja on 2008-06-27
So Totem player is using PulseAudio sound driver? And that is causing all these sound problems on Ubuntu/Xubuntu? Not wonder I got rid off of Totem and its gstream codecs faster then thunder. Almost instinctive reaction like to a bug bite :D

---

### Post by Xi0N on 2008-07-01
> **Nepherte said:**
> This is a known issue of PulseAudio. It blocks access to the sound card for the second, third, ... application that uses sound. You can fix this following this tutorial: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Works perfectly for me...

thanks!!!

---

