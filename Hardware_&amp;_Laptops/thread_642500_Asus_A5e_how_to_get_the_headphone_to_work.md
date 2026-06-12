---
title: "Asus A5e: how to get the headphone to work"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by Garfield123 on 2007-12-16
I installed Ubuntu 7.10 on my Aus A5e. The speakers worked fine, the headphone did not. 
I thought it might be useful to share that this solution:
[http://ubuntuforums.org/showthread.php?t=597575&highlight=asus+headphone](http://ubuntuforums.org/showthread.php?t=597575&highlight=asus+headphone)
  worked for my A5e, even if it was originally posted referring to another laptop.

The steps are (quoting from the post):
Step 1: Open up the Terminal (Applications > Accessories > Terminal)

Step 2: Paste the following line:
Quote:
sudo gedit /etc/modprobe.d/alsa-base
and input your password

Step 3: When the text editor opens, paste this new line at the bottom of the file:
Quote:
options snd-hda-intel model=z71v position_fix=1
Step 4: Save the file and close the editor. You can also close the terminal now and restart your computer.

Step 5: After restarting you can check on the Alsa Mixer (double click on the loudspeaker on the menubar) that now there's a Headphone fader. Just click the small loudspeaker beneath it and raise the fader.

Unlike the other user's experience, on my laptop the Fn keys worked perfectly from the begininng.

Hope this is useful!

---

### Post by Garfield123 on 2007-12-17
Actually, I have just realized that the microphone is not working. The item is shown in the volume control, but the microphone didn't work with the skype test call. If I find a solution I'll post it. In the meanwhile, if any one has any suggestion, it's more than welcome!

---

