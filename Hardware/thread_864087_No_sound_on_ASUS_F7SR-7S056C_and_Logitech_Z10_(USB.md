---
title: "No sound on ASUS F7SR-7S056C and Logitech Z10 (USB) speakers"
date: 2008-07-19
forum: Hardware
---

### Post by iosifidis on 2008-07-19
Hello,

I just made a fresh installation to a friend's laptop ASUS F7SR-7S056C. He has Logitech Z-10 (on USB) speakers. I installed all restricted extras.

We run an mp3 and mpg file. There's no sound to both files (although there's video playing). I unpluged the speakers and I tried with the ones that has the laptop. I had max volume, it didn't play sound.

The speakers didn't follow his commands. Although we tried to min the volume (to mute) it didn't go all the distance. The sign on the computer was like mute though but not the sign on the speakers.

Strange thing was that I listen the first sound (drums) while the computer opens. 

What to I do?

---

### Post by ulipispirus on 2008-07-19
Hello,
You have to probably add this to Your /etc/modprobe.conf:

          options snd-hda-intel model=lenovo

Then restart computer.

Do not forget to umute sound by alsamixer.
If You will hear noise from speakers know that reason is input microphone canal which is ON, turn it OFF.


By.

---

### Post by iosifidis on 2008-07-20
Thanks. Problem solved.

---

