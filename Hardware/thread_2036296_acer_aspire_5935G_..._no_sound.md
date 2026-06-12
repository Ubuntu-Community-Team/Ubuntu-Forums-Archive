---
title: "acer aspire 5935G ... no sound?"
date: 2012-08-01
forum: Hardware
---

### Post by xeaze on 2012-08-01
Hey guys im new to ubuntu etc but im really enjoying it much better then windows. The only problem i am having is i have no sound on my acer aspire 5935G :( i have searched the forum and havent came up with alot, i have seen other people with acer having same problem.
Could one of you guys point me in right direction to get it working please?
* also sorry im using latest version of ubuntu 12.04 LTS *
Thanks leigh

---

### Post by ajgreeny on 2012-08-01
Start by looking in pulseaudio volume control which you will find using the dash and searching.  Check that nothing is either muted or set too low.

You might also want to run alsamixer in terminal and check that the levels of outputs are not set too low or muted in that as well.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

If you don't already know it, here's a screenshot to show you what to expect.

---

### Post by xeaze on 2012-08-01
hey and thanks for such a fast reply i tryed both i neither worked :( i first tryed alsamixer in terminal, i adjusted everything to max and was not sure what was muted and none muted so tryed both with MM and also 00. Then as you said i downloaded and tryed pulseaudio volume control which showed it was muted change that also but still no sound? 
I have included to screenshots if they can give any clue to why not working. (thanks for any help and sorry im new to all this )
Leigh

---

### Post by ajgreeny on 2012-08-02
Your alsamixer shows almost everything muted (MM at the bottom) but as you say ypu tried both with and without, that is obviously not the answer.

The pulseaudi volume control is more difficult to comment on as you show the Playback tab only, and with the **Built-in analogue audio stereo **option.  Try clicking on that option and choose another output if there is one.  Also try the Output Devices tab, and play around with that, trying all the options available to you, which may eventually get you some sound output.

---

