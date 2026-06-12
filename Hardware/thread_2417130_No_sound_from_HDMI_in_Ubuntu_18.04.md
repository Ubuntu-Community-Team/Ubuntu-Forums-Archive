---
title: "No sound from HDMI in Ubuntu 18.04"
date: 2019-04-21
forum: Hardware
---

### Post by alperenaydin on 2019-04-21
I have a HP-Laptop with Windows 10-Ubuntu 18.04 dual boot. I have GeForce GTX 1050 as my graphics card. I like connecting my laptop to my TV. On windows, it works perfectly fine. Both the display and  audio is from the TV. On Ubuntu, only the display works through the TV. The speakers of the laptop is used for the audio. 

Some history in case it is needed: When booting from the USB, the computer would freeze if I tried to go to the settings. The computer would freeze as well when it rebooted. I solved this by adding: "nouveau.modeset=0" after quiet splash . I added it after Ubuntu was installed. Initially both the display and sound did not work. I solved this by changing the driver in "Software and Updates" from X.org X server to nvidia-driver-390. This fixed the issue with the display but not the sound. How would I go about solving this issue?

---

### Post by kryten35 on 2019-04-21
Did you change the sound output in sound settings to nvidia high definition audio controller-digital stereo.?

---

### Post by alperenaydin on 2019-04-21
I should have mentioned this. There is no sound device other than the laptop speakers in the settings: [https://imgur.com/a/QeWSa0J](https://imgur.com/a/QeWSa0J)

---

### Post by kryten35 on 2019-04-21
Is it a very new laptop,you may need a more up to date kernel.My linux rig is running 19.04 with an nvidia gtx950.
I had to install it using the new "install ubuntu -safe graphics" option as like you i got black screen.

I also had to use the other new option during install "install third party software for graphics wifi etc"
This installed the nvidia driver.If ididnt i got black screen on first boot.

So you might want to try 19.04.They have done some work on improving the sound settings.Youl probably know via google that no sound via HDMI is a common problem in linux and theres not one easy solution.I have a soundblaster card
and ive got outputs for hdmi and outputs for the card itself in the sound settings.

---

### Post by vantaianphatran on 2019-04-21
[COLOR=#000000]may be you change your sound setting[/COLOR]

---

