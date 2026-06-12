---
title: "Asus a5e: help on getting the microphone to work with Skype"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by Garfield123 on 2007-12-18
Hi all,

I installed Ubuntu 7.10 on my Asus a5e laptop.

I got the headphones to work ([http://ubuntuforums.org/showthread.php?t=642500](http://ubuntuforums.org/showthread.php?t=642500)) but I can't seem to do the same for the microphone on Skype (the only application for which I'd use the microphone).

The mixer is showing the microphone, and the volume is not nil. I tried:
- changing the sound device on the mixer from intel to OSS
- changing the input device in the mixer from Microphone to "Front" to "Input Device 1"
- changing the input device in the skype options, trying all the 6 options I'm given
- all the combinations of the above

to no avail: when I run the skype test call, no sound whatsoever is recorded, not even hisses or background noises. Any help would be greatly appreciated!

---

### Post by Garfield123 on 2007-12-19
No ideas? :(

---

### Post by wolfvorkian1 on 2007-12-20
> **Garfield123 said:**
> Hi all,

I installed Ubuntu 7.10 on my Asus a5e laptop.

I got the headphones to work ([http://ubuntuforums.org/showthread.php?t=642500](http://ubuntuforums.org/showthread.php?t=642500)) but I can't seem to do the same for the microphone on Skype (the only application for which I'd use the microphone).

The mixer is showing the microphone, and the volume is not nil. I tried:
- changing the sound device on the mixer from intel to OSS
- changing the input device in the mixer from Microphone to "Front" to "Input Device 1"
- changing the input device in the skype options, trying all the 6 options I'm given
- all the combinations of the above

to no avail: when I run the skype test call, no sound whatsoever is recorded, not even hisses or background noises. Any help would be greatly appreciated!

I feel for you because I just went through the same hassle with the microphone.  I spent several hours last night with google and tried numerous techniques and nothing worked. Tried even a suggested xml edit of a configuration file and it didn't help. Skype simply destroyed my edit everytime I  loaded it. 

However I clicked enough buttons and finally got it working fine in 7.04. I'll try and recall what I did. First I played around with alsamixer  and that didn't seem to help much or maybe I just wasn't able to enable all the features ( couldn't figure it out)  but by  chance I opened up the Gnome sound -recorder and clicked 'open volume control' in the file menu. It was via the little recording program that I was able to get Skype working.

Then I went to the edit menu and clicked 'preferences' in the drop down menu. There I found a lot of options to enable that weren't in alsamixer when I brought it up via the terminal or if they were, I couldn't figure out how to find them. I then selected most of the tracks that were available. 

Then in the 'playback' tag, I moved everything to 100%. The next tag to the right is 'recording' and all that is there on mine was 'microphone capture', I moved it to a 100% too. 

Then to 'switches' and clicked 'mic Boost Capture', nothing else and then to 'options', I checked 'rear output' in the line-in-mode section. 

Almost forgot but under the 'file' menu, in the drop down, I clicked 'change devices' and whether I clicked my audio card or it was already checked, I don't know but oss mixer is NOT checked. You might check that too. 

Somehow this made it work.  I'm still not sure how but it works fine now. The secret for me was getting into alsa mixer via the Gnome sound-recorder. Good luck.

---

