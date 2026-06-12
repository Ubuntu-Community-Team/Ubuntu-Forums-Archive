---
title: "No audio from front-panel headphone jack"
date: 2021-01-28
forum: Hardware
---

### Post by johnlbergqvist on 2021-01-28
I have a motherboard with a standard Intel ALC1220 chip, plus a graphics card which has HDMI audio. 

All of a sudden, the audio has stopped coming out of my front panel jack whenever I switch to it in pavucontrol (or the ubuntu sound settings). It's not saying anything's unplugged, and everything I can find (`pacmd list-sinks`, audio meters in pavucontrol etc.) says that audio is playing and sound should be coming out however nothing is. 

 My rear panel audio is fine still (not that I usually have anything plugged in there - Pulseaudio sees this as a seperate device when I plug something in there), as is my HDMI audio. 
I've checked that nothing is muted in alsamixer.
When I dual-boot into Windows, the sound works fine there through the front panel, so it's not a hardware issue. 

Also on Ubuntu, the front panel microphone is recording audio fine - it's just the headphone jack that isn't emitting anything (even though as far as the OS is concerned, it is)

Does anyone have any suggestions?

Update: If I plug some speakers into the rear line out jack, then switch the pulseaudio device to that, I hear sound as expected, however if I then switch pulseaudio's default device to the headphone jack, the audio from the rear speakers gets louder (still nothing from the headphones) - WTF is going on?

---

### Post by johnlbergqvist on 2021-01-28
I've resolved it. I had to disable the "Make front and rear output devices playback two different audio streams simultaneously" in Realtek's control panel on Windows. I rebooted into Ubuntu, and suddenly I can hear from the front panel there again!

---

