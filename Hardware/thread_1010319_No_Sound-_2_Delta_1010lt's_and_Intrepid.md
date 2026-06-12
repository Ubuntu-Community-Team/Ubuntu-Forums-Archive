---
title: "No Sound- 2 Delta 1010lt's and Intrepid"
date: 2008-12-13
forum: Hardware
---

### Post by shedt on 2008-12-13
Hello,

I have two Delta 1010lt's installed plus there is the on-board from the motherboard.

I have no clue how to get sound working. I've tried selecting different devices but it's still not working.

Should I disable the on-board in the bios?

Do I need to follow the instructions for opensound here:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I'm really lost. Thank you for reading.


Edit-

Well I followed the instructions on that page. It seemed to detect both delta 1010lt's but now there is only on-board showing for the oss mixer. 

Any suggestions?

---

### Post by BananaFish on 2008-12-13
> **shedt said:**
> 

I have two Delta 1010lt's installed plus there is the on-board from the motherboard.

I have no clue how to get sound working.

Any suggestions?

Hi, I had no sound when I first installed intrepid, I have a Delta 1010 (not lt - presume problem is with both...?), I don't use onboard sound though.

I found this solution and everything has been fine since:

[http://ubuntuforums.org/showthread.php?t=963914&highlight=pulseaudio+audiophile](http://ubuntuforums.org/showthread.php?t=963914&highlight=pulseaudio+audiophile)

Basically involves removing PulseAudio which seems to comflict with Delta 1010s, make sure you read through the whole thread, as far as I remember I got my solution by using a combination of the different suggestions, but it was a while back, there is some bit about not being able to log back in to your system if you do it wrong, make sure you follow all the whoile thing before making changes

good luck, let me know if you need any more info

---

### Post by shedt on 2008-12-13
Thank you, I know I had to stop/remove alsa. I will check through it. I know it is working, when I do a test with oss I hear sound when it gets to output 1/2.

I guess I need to figure out how to re-map it to first. I changed a config file and put the on-board on the bottom, it changed it's order in the ossmixer, but Ubuntu as far as i can tell is still trying to use the on-board. Except the gnome volume thing. It says something about the gstreamer not working blah blah.

No volume control plugin found.

---

