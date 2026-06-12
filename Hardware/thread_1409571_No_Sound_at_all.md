---
title: "No Sound at all"
date: 2010-02-17
forum: Hardware
---

### Post by ReedAndrew on 2010-02-17
I have looked through the forms and tried many different things with nothing fixing my problem.  I just recently installed Ubuntu because I didn't want to have to pay for another Windows7 key for a laptop I don't really use. It is an HP Pavilion dv6.  

Codec: IDT 92HD75B3X5
Codec: LSI ID 1040

Can anyone help me solve my problem with my sound all I really use this laptop for is listening to music and surfing the internet once in awhile at work. Please help!

AR

---

### Post by pi/roman on 2010-02-17
You could try installing a backport alsa module. Get your kernel version by typing "uname -r" in a terminal then open up the package manager by pressing alt/f2 then "gksu synaptic".
Then in the search bar type "linux-backports-modules-alsa" then find your kernel version.

---

### Post by ReedAndrew on 2010-02-19
So i did what you said and it looks like it has worked for the most part. I hear the drums when the computer boots.  But now whenever i play music or video's on the internet they play in 2x speed. So there is still no audio coming out of the computer.  Is this just a setting that i need to change?

AR

---

### Post by ReedAndrew on 2010-02-19
So I installed VLC and my music will play through that but when still when I watch Youtube or listen to music using Rythmbox everything is in 2x speed and there is no audio.  Is there anything I can do to change this setting?

---

### Post by ReedAndrew on 2010-02-19
Alright so I solved the problem.  The issue was that pulseaudio was still installed so I ran the command
sudo apt-get remove pulseaudio

restarted the laptop and now rythmbox and everything else is working great!

---

### Post by pi/roman on 2010-02-19
Excellent! Thanx for explaining a solution to your problem so hopefully it will help others.

---

