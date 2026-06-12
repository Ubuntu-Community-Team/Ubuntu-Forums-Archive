---
title: "No sound after 10.04 lucid upgrade on MSI laptop"
date: 2010-05-24
forum: Hardware
---

### Post by aj_the_first on 2010-05-24
I recently upgraded to 10.04, and I now have no sound.

I have fixed many sound problems before, and I have checked every mute button in every program I can find.  I assure you my system is not muted.
I can watch the bar jump to the music in pulseaudio, but there is no sound.  The bar does not display output when muted, only when there is music playing ad it is not muted.

It does not work when running from liveCD either, so I suspect there is a new open source sound driver that does not work on my machine.
I am using an MSI EX625 laptop.
I really don't know what else to say.
Thanks
AJ

---

### Post by aj_the_first on 2010-05-25
Okay, I do know what to say: can anyone help?  I don't even know where to start after ALSAmixer and pulseaudio settings adjusting didn't work.  I made sure that the output device was correct, nothing was muted, everything was turned up, and I can see the output bar indicating sound in pulse audio jumping to the music...   but nothing comes out the speakers.
This is my media laptop!  please help!

---

### Post by joshzam on 2010-05-25
I had a similar problem with my Acer laptop of the Lucid upgrade. No sound anywhere. I checked in the system Sound preferences and everything looked kosher. I know you say you checked all levels everywhere, but what worked for me was, from the Terminal, I typed alsamixer and noticed that the Speaker volume was set to 0. I upped it to 100 and I've got sound again! Hope this helps. Good luck!

---

### Post by aj_the_first on 2010-05-25
yeah, I already tried that.  It is set to 100.  The mastervolume is shown in red text.  does that matter?

---

### Post by michaelA1330 on 2010-05-25
check you have the right drivers , or make sure they arnt black listed then run a system speaker check in a terminal 

sudo-apt-speakertest 

that should fix it

---

### Post by tito2986 on 2010-06-25
Hey!!!
Firts, sorry for my bad english!!!

I had the same problem with the MSI EX625. I found a solution for the sound (the subwoofer will not work).

Look here: [http://ubuntuforums.org/showthread.php?t=1182556]("http://ubuntuforums.org/showthread.php?t=1182556")

There's the only solution i have found for my MSI

---

### Post by lidex on 2010-06-27
With an upgrade you may be experiencing conflict with leftover config files. Do 'Part A' at pulseaudio link in my sig.

---

