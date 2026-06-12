---
title: "Audio Stuttering New Install Ubuntu 16.04"
date: 2017-10-29
forum: Hardware
---

### Post by moose1207 on 2017-10-29
First, My Specs. 
  Ubuntu 16.04 Kernel 4.10

  Home built PC :

  ASUS Maximus VI Extreme with Nvidia GTX970 for Video/Audio over HDMI 16GB RAM


  OK, So I recently decided I was fed up with MS with all of its  updates and crap being randomly installed and wanted a change of OS. I am very new to linux so forgive me if there is some simple things I may have overlooked.  I  first installed OpenSuse Leap 42.3 and have now switched to Ubuntu  because of the issues I am still having, which is stuttering audio  (switching distros didn't fix my problem). Anyways I do get  audio output whether I use aplay, system sounds or something like  youtube  but it stutters really bad. I have been googling until my  fingers bled and attempted many of the fixes everyone else with this  problem has used. I have adjusted the udev tsched=0 to and it didn't  work. I have tried putting

  *options snd-hda-intel vid=8086 pid=8ca0 snoop=0

  *options snd-hda-intel position_fix=1

  at the end of the alsa-base.conf file and that hasn't worked either. I  also tried changing to default msec settings from 4100 to 4800. With  all of this mucking about I got a pretty good crash course in the linux  file system and using the terminal lol. I'm not sure where to go from  here, if someone could help me out that would be awesome. One weird thing I noticed, If I try to  play a youtube video the sound stutters and so does the video. after a  few seconds the video will get the loading circle and eventually stop  working all together, however if I slide the volume up and down really  fast constantly the audio and video stutter get much less but still  stutters a bit and the audio obviously goes up and down. Hopefully this  helps point to the right direction.

---

### Post by Autodave on 2017-10-29
Did you install any driver for the Nvidia card? If so, where did you get it from?

If you haven't installed one yet, go to Settings -> Additional Drivers and install whatever one it recommends.

---

### Post by moose1207 on 2017-10-29
I already  installed the Nvidia drivers  by following this link [http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux](http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux) and now my graphics settings work but still the issue with the audio.

---

### Post by moose1207 on 2017-10-29
Also just to be clear I installed the "nvidia-384" ppa, not the one shown in the tutorial.

---

### Post by Autodave on 2017-10-29
What are you using for the sound: a seperate audio cord or is it going through the HDMI cable?

---

### Post by moose1207 on 2017-10-29
My pc is generally for gaming but I also use it to maintain my Unraid Server, So I have this pc outputting to a receiver that is connected to my TV. I use the HDMI for outputting video and 5.1 channel audio to the reciever.

---

