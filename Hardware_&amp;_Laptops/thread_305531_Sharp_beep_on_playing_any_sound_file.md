---
title: "Sharp beep on playing any sound file"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by Sukarn on 2006-11-23
I am getting a sharp beep-like sound from my speakers/headphones, whenever I play an mp3 file or an avi file (the only 2 kinds of media files I currently have on my system). The beep is also present when I click on test on any of the options in System->Preferences->Sound.

I do not know much about the sound card (its an integrated sound). I recently bought this motherboard. The board is Asus A8V-VM. If there is something I can do to detect the board, please tell me, so I can give further information about the issue. The system being used is ubuntu edgy amd64.

---

### Post by yanewby on 2006-11-24
I have (or should I say had) the same problem as you where a high pitched tone was played at the same time as any other sound.

I can take no credit for this answer as I simply followed the instructions here:
[http://ubuntuforums.org/archive/index.php/t-260352.html]("http://ubuntuforums.org/archive/index.php/t-260352.html")

In summary, type sudo gedit /etc/modprobe.d/alsa-base in a terminal (and type in your password as we are using sudo).

This will open up gedit with the file (/etc/modprobe.d/alsa-base) open in it.  Simply add the following line at the bottom (where there may be some other lines beginning with "options"), don't delete anything else just add this line:

options snd-hda-intel position_fix=1 model=3stack

Reboot your computer and hopefully the high pitched tone will have gone, it worked for me!

---

### Post by Sukarn on 2006-11-24
Thanks a lot. This fix fixed the issue.

---

