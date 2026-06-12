---
title: "How Do I Configure Mic On Asus Laptop On Ubuntu 10.04 x64"
date: 2010-08-30
forum: Hardware
---

### Post by hayhursm on 2010-08-30
[SIZE=2]I noticed my built-in mic on my Asus F3KA-A1 laptop was not working correctly with Skype; the test call sounded ok but my voice was broken and distorted if I called someone.  I don't think it's related to Skype because if I went to Ubuntu's "Sound Preferences" and then selected the "Input" tab I could view the "Input level" bar graph for the mic.  When I spoke, the "Input level" graph was very sporadic and out of sync with my voice.  It was all over the place and even had a delay although my voice was at a consistent level and speed.  I decided to compare these patterns to my Logitech USB webcam which has a built in mic on my desktop PC.  The "Input level" on that setup was right in sync with my voice so this leads me to believe it's something to do with the PulseAudio setup on my laptop.  Also, I plugged in a different mic to the auxiliary port on the laptop and the problem still exists.  Has anyone experienced this before?[/SIZE]

---

### Post by sam-bo on 2010-08-30
I have a dv9000 and the internal webcam is not functional.  Since skype  is defaulted through /dev/video1 and not changeable, my usb webcam  deosnt appear in skype.  However, cheese and webcam studio both use the  usb cam.  how do I go about booting the internal webcam off of  /dev/video0? I would like for the usb cam to be on "/dev/video0" instead of the internal webcam.  any leads?

thanks,

sam-bo

---

### Post by hayhursm on 2010-08-31
> **sam-bo said:**
> I have a dv9000 and the internal webcam is not functional. Since skype is defaulted through /dev/video1 and not changeable, my usb webcam deosnt appear in skype. However, cheese and webcam studio both use the usb cam. how do I go about booting the internal webcam off of /dev/video1?
 
thanks,
 
sam-bo
 
My webcam works just fine, and it is internal on my laptop.  Does Skype have a .config you can edit?  Also, does your built-in mic work with Skype?  If so, could you give me any pointers?

---

### Post by Dave158 on 2010-08-31
If the test call was okay, then most likely it was either your internet connection. The test call is on your local machine so it won't break up. But if your internet connection or your partner's is weak, then most likely it will drop or breakup.

---

### Post by hayhursm on 2010-09-01
> **Dave158 said:**
> If the test call was okay, then most likely it was either your internet connection. The test call is on your local machine so it won't break up. But if your internet connection or your partner's is weak, then most likely it will drop or breakup.
 
 
[SIZE=2]I thought the same thing so I tried Skype on my wife's laptop (which uses WiFi) and the call went through just fine.  I still think the "Input level" graph for the mic is telling me something else is wrong but I don't know what.  The graph on my wife's HP laptop responded very well to my voice, so again I think this is a good indication of where I need to begin on my Asus laptop.[/SIZE]

---

### Post by sam-bo on 2010-09-03
I have edited the text above.  I had posted "/dev/video1"........which is not accurate.  I actually need to remove the internal cam from "/dev/video0" so that my usb webcam will work in skype.

---

### Post by sam-bo on 2010-09-04
Originally Posted by **sam-bo** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9786831#post9786831") 				
 				[I]I have a dv9000 and the internal  webcam is not functional. Since skype is defaulted through "/dev/video0"  and not changeable, my usb webcam deosnt appear in skype. However,  cheese and webcam studio both use the usb cam. how do I go about booting  the internal webcam off of /dev/video0 to be able to une skype with the usb webcam?
 
thanks,
 
sam-bo[/I]

---

### Post by hayhursm on 2010-09-07
> **sam-bo said:**
> Originally Posted by **sam-bo**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9786831#post9786831")                 
                *I have a dv9000 and the internal webcam is not functional. Since skype is defaulted through "/dev/video0" and not changeable, my usb webcam deosnt appear in skype. However, cheese and webcam studio both use the usb cam. how do I go about booting the internal webcam off of /dev/video0 to be able to une skype with the usb webcam?*
 
*thanks,*
 
*sam-bo*
 
 
Is it possible you could create a **symbolic link** between the two devices?

---

### Post by hayhursm on 2010-10-01
> **hayhursm said:**
> [SIZE=2]I noticed my built-in mic on my Asus F3KA-A1 laptop was not working correctly with Skype; the test call sounded ok but my voice was broken and distorted if I called someone.  I don't think it's related to Skype because if I went to Ubuntu's "Sound Preferences" and then selected the "Input" tab I could view the "Input level" bar graph for the mic.  When I spoke, the "Input level" graph was very sporadic and out of sync with my voice.  It was all over the place and even had a delay although my voice was at a consistent level and speed.  I decided to compare these patterns to my Logitech USB webcam which has a built in mic on my desktop PC.  The "Input level" on that setup was right in sync with my voice so this leads me to believe it's something to do with the PulseAudio setup on my laptop.  Also, I plugged in a different mic to the auxiliary port on the laptop and the problem still exists.  Has anyone experienced this before?[/SIZE]

I lost my job on Monday and now since I have plenty of free time I decided to revisit this problem.  For those of you struggling with getting your microphone to work with Skype, your culprit might be PulseAudio.  I decided to do an "sudo apt-get purge pulseaudio* and to my surprise the microphone worked crystal clear with Skype.  Purging PulseAudio unlocked additional choices under "Options" "Sound Devices" in Skype as well.  My question is, why was PulseAudio even neccessary, is it better than ALSA?  I lost my volume control applet on the taskbar after the purge so is there a way to get PulseAudio and ALSA to work in harmony?

---

### Post by hayhursm on 2010-10-03
> **hayhursm said:**
> i lost my job on monday and now since i have plenty of free time i decided to revisit this problem.  For those of you struggling with getting your microphone to work with skype, your culprit might be pulseaudio.  I decided to do an "sudo apt-get purge pulseaudio* and to my surprise the microphone worked crystal clear with skype.  Purging pulseaudio unlocked additional choices under "options" "sound devices" in skype as well.  My question is, why was pulseaudio even neccessary, is it better than alsa?  I lost my volume control applet on the taskbar after the purge so is there a way to get pulseaudio and alsa to work in harmony?


bump

---

### Post by hayhursm on 2010-10-07
Bump

---

