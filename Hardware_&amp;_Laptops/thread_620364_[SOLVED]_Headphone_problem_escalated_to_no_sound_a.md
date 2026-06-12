---
title: "[SOLVED] Headphone problem escalated to no sound at all"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by potatu on 2007-11-22
Hi,

I recently installed Ubuntu 7.10 on my Asus F3Jp laptop, and was pleasantly surprised. Everything seemed to work out of the box.

However, that would turn out to be wrong. Although sound worked fine both out of the speakers (albeit a bit low) and the headphones, the speakers would not mute when I plugged in the headphones. tried searching high and wide for a fix, but to no avail. 

Came over this thread:
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

Tried to install the drivers as the thread outlines, but this did not work. In fact, nothing changed. Until I rebooted. Now there's no sound at all, and I get the error message "No volume control GStreamer plugins and/or devices found"

Since I am a complete and utter noob regarding linux, any suggestions as to how I can get the sound back would be greatly appreciated.

---

### Post by Tweenk on 2007-11-22
1. Remove the drivers (or reinstall the system) to get back the sound as it were before you installed the drivers. They are probably unnecessary. Judging from the content of the thread you mentioned, the quickest solution would be to reinstall Ubuntu from scratch while backing up your data.
2. The problem you had before is solved by enabling the Headphone Jack Sense in the Volume Control:
- Right click on the speaker in the upper panel and select "Open Volume Control".
- Select Edit -> Preferences from the menu.
- A list with checkboxes will appear. Check the Headphone Jack Sense item.
- Click Close. A new tab will appear in the volume control panel, called Switches. Select this tab and check "Headphone Jack Sense".
- You shouldn't hear any sound from the speakers when you plug in the headphones now.
3. Another one-time solution is to mute the Master channel and adjust the Headphone channel to the desired volume. If it's not shown, check its checkbox in the list mentioned before.

---

### Post by potatu on 2007-11-22
Thank you for your reply. I will likely reinstall later, as you suggested. Tidier that way.

On account of the headphone issue, I've seen that solution several places. However, there was no checkbox with "headphone sense". The only thing I could get was a headphone-checkbox in switches, but this only enabled/disaled the headphone jack. There was no headphone channel I could adjust either. 

I'll reinstall tonight, hoping to see some further ideas on the headphone problem:)

EDIT: Allright. Back up, same problem this time. Any idea is appreciated.

---

### Post by potatu on 2007-11-23
Okay, doin' the old bump.

The machine is an Asus F3Jp laptop, using the HDA Intel driver. If that helps, please speak up!

---

### Post by potatu on 2007-11-24
Bumpedy-bump.

---

### Post by jcsteele on 2007-11-24
Try looking at [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

and also my notebook (toshiba) has a similar problem.....might help.

my page located at [http://ww2.coastal.edu/jcsteele/gutsy-S4134.html](http://ww2.coastal.edu/jcsteele/gutsy-S4134.html)

//jcs

---

### Post by potatu on 2007-11-25
Thank you for what appears to be an excellent response. I will try the different methods outlined, something's gotta work.

---

### Post by potatu on 2007-11-28
After intense experimentation back and forth, quite a few reboots and frustration I got it working. 

It was so simple as to add the model "lenovo" as an option in the alsa-base file. Trivial.

---

