---
title: "Updated and lost sound."
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by OxR on 2009-07-29
I just updated Ubuntu 9.04 and now I have no sound.

lspci -v shows the sound card.

Here is what was updated:

Upgraded the following packages:
linux-generic (2.6.28.13.17) to 2.6.28.14.19
linux-headers-generic (2.6.28.13.17) to 2.6.28.14.19
linux-image-generic (2.6.28.13.17) to 2.6.28.14.19
linux-libc-dev (2.6.28-13.45) to 2.6.28-14.47
linux-restricted-modules-common (2.6.28-13.17) to 2.6.28-14.19
linux-restricted-modules-generic (2.6.28.13.17) to 2.6.28.14.19

Installed the following packages:
linux-headers-2.6.28-14 (2.6.28-14.47)
linux-headers-2.6.28-14-generic (2.6.28-14.47)
linux-image-2.6.28-14-generic (2.6.28-14.47)
linux-restricted-modules-2.6.28-14-generic (2.6.28-14.19)


Anyone know what would be the problem?

---

### Post by linux_tech on 2009-07-29
check all your settings first to make sure nothing is muted. 
You can temporarily stop pulse audio by typing
```
 sudo killall pulseaudio 
``` in the terminal and see if that makes any change

---

### Post by Zorael on 2009-07-29
hm.
```
$ pulseaudio -K
$ alsamixer
```
If there is only one slider in alsamixer, try starting it with the following instead.
```
$ alsamixer **-Dhw**
```
Make sure nothing is muted; sliders should say 00 and not MM (hit M to toggle). Raise channel volumes up respectably, so nothing is at 0% for some reason. Try adding **-Dhw** here too if you had to earlier, not sure if Pulse could still be rerouting the default ALSA device to itself.
```
$ speaker-test -twav -c2

*$ speaker-test -twav -c2 **-Dhw***
```
If it *still* doesn't work, paste the output of the following.
```
$ aplay -l
$ aplay -L
```
(note case difference)

---

### Post by OxR on 2009-07-29
--I have since fixed this by simply reinstalling ALSA, thanks for the help.--

Alsa mixer has no sliders, it is completely blank.
The speaker-test commands give me A LOT of errors, I will post them in a separate reply below this one.
aplay: device_list:217: no soundcards found...
I am starting to think this is a driver problem.

EDIT:  This error message on these forums is keeping me from posting the log of errors:

[LIST=1]
[*]
[LIST=1]
[*]You have included 312 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again. 

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
[/LIST]
 
[/LIST]
                   [Okay]("http://ubuntuforums.org/showthread.php?p=7697019#")                                                           [LEFT]                     [/LEFT]

---

