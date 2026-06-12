---
title: "Mic does not work on Lifebook s7210 laptop"
date: 2012-07-13
forum: Hardware
---

### Post by Pand5461 on 2012-07-13
Hi all!

I'm having a microphone trouble on my Fujitsu-Siemens Lifebook S7210. Neither internal nor external mic appear to work in Xubuntu 12.04. On Ubuntu 10.04 installed before everything worked fine. The audio codec is Realtek ALC262.
So, I couldn't figure out whether Canonical guys have broken hardware compatibility in 12.04 or it's some misconfiguration.
I would be glad to see any helpful suggestions.

---

### Post by jelli32 on 2012-07-14
I am using precise pangolin and I got my internal microphone to work.  Tested it out with a friend and he said he could hear me well. Maybe  this can help you. Here's what I did:

First, open up Mixer (click on the audio button at the top of your  screen). Mixer is where you can adjust the volume for different sources.  If you can see the volume controls for Microphone and Mic Boost, make  sure they're not muted. If you can't see them, click the "Select  Controls" button at the bottom and check the Microphone and Mic Boost  options. Then, increase the volume for both.

Secondly, go to Multimedia and click on PulseAudio Volume Control. Make  sure the volumes for Playback, Recording, and Output Devices are not  muted, and try to increase the volume for each. Go to the Internal  Devices tab and next to where it says "Port," select the source for your  microphone. In my case, I selected "Internal Microphone" because I have  a built-in microphone for my laptop. If you are using an external  microphone, select a different option from the drop-down list. Make sure  the "mute" icon at the top is not selected. Next, go to where it says  "Front Left" and "Front Right" and increase the volumes for your  microphone.

Test it out with a friend or family member during Skype, Google+, or  some other videochatting service and see whether they can hear you. I  set the volumes high initially just to make sure people can hear me.

---

