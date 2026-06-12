---
title: "Two finger scrolling option disabled/grayed out"
date: 2010-08-23
forum: Hardware
---

### Post by pedrosanta on 2010-08-23
Hi all.

I have Ubuntu 10.04 installed on my HP Pavilion dv3-2150ep and I really miss the two finger scrolling feature. I'm pretty sure I have a synaptics touchpad and I have this on Windows 7 working.

I tried to enable this on the System > Preferences > Mouse settings but the two finger scrolling option it's disabled/grayed out.

Any thoughts on how can I enable it or how can I check my touchpad model/information?

Thanks in advance. Cheers.

---

### Post by heuristicist on 2010-08-27
I have the same problem on a Dell Studio 15 (1558). A workaround can be found [here]("http://ubuntuforums.org/showpost.php?p=9303160&postcount=7"). I set up a script with those contents and have it run at boot, and the script also includes some other touchpad settings (e.g. set two fingers to middle click instead of right click). Unfortunately there are still some times (I can't figure out when) that the GNOME mouse configuration tool overrides the settings and I lose two-finger scroll and I have to run the script again. But it works, more or less. Hopefully this will be fixed, but there hasn't been much activity on this [(seemingly) related bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/476866").

---

### Post by vedster on 2011-01-17
After many, many hours of googling and trial and error, I found a solution that works.

1. Open up a terminal
2. Type the following codes in
```
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
```

Please note that I am using a HP-DM41050CA with a PS/2 Synaptics Touchpad. Two finger scrolling works great, horizontal and vertical. Also, unlike Windows I can go diagonally and freely in any direction, which i think is absolutely amazing.

NOTE: This code will stop working after reboot, so open gedit and paste the code above into it. Then save the file with any name as a (.run) file in your home directory. Assuming you are using 10.04 Ubuntu, go to System>Preferences>Startup Applications and add that (.run) file to the list.

Hope this helps! It's the only thing that works for me.

---

### Post by Lebuin on 2011-01-24
Installing the attachment given in reply #116 on [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191") solved this problem for me (without any workarounds). After installing and rebooting, I was able to check the two-finger scrolling box. (Also, two finger tapping for a right click works automatically).
Hope it works for you too.

---

### Post by herrBua on 2011-01-26
@Vedster worked like a charm :] I didn't know it was possible to play with synclient like that :]

@Lebuin that one didn't work for me :S I don't really know why, but it didn't work :S

May I suggest that if you're going to spend some time playing with the manual:

```
man synaptics
```

It really helps and you get to check all the features available.

---

