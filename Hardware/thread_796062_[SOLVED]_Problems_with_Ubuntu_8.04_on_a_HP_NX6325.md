---
title: "[SOLVED] Problems with Ubuntu 8.04 on a HP NX6325"
date: 2008-05-16
forum: Hardware
---

### Post by bittenmonkey on 2008-05-16
Hi there, 

I have recently been using Ubuntu as my main OS but since installing it I have been experience a few problems/issues and was wondering if anybody could give some advice?

1) I cannot adjust the brightness of my screen by using the default fn+f9/f10 option. I think this stopped working as soon as I activated the wireless driver. I have tried assigning various shortcuts since to try and get it to work but still cant.

2) I have noticed that when I plug earphones into my laptop that the speakers still play.

3) I cant use the backspace key to navigate (go back) in FireFox, this has never worked under Ubuntu.

Cheers,

Dan

____________
Ubuntu 8.04
Kernel 2.6.24-17
HP NX6325
AMD Turion 64 x2 Mobile TL-60
ATI Radeon Xpress1150
2Gb RAM
80Gb HD

---

### Post by lswest on 2008-05-16
only fix i know (that may work) is for 3)

navigate to about:config in firefox, and then search for ```
browser.backspace_action
``` and change the value to "0" (without the quotes)

about 2): are you running 8.04?  if so pulseaudio (should have) fixed this for you, otherwise there are multiple fixes listed for alsa playback in headphone jacks (sadly, i couldn't find one that worked for my hp dv6545eg but pulseaudio works fine now).

and 1):  are you running compiz?  if you have compizconfig-settings-manager installed, you can set up keyboard shortcuts under the "general" options. (i think it's in the second or third tab, not 100% and i'm at a windows PC atm).

---

### Post by bittenmonkey on 2008-05-16
CHEERS lswest, 

3 is now fixed :) and 2 seems to have sorted itself out.

Dan

---

### Post by lswest on 2008-05-16
glad i could get at least one issue sorted :) (and btw, if you found that useful, you could thank me using that gold medal on the bottom right of my post ;)) </attempt at more thanks> XD

---

### Post by bittenmonkey on 2008-05-16
I was trying to work out how you do that, now I know!

---

### Post by lswest on 2008-05-16
> **bittenmonkey said:**
> I was trying to work out how you do that, now I know!

haha, i'm glad i was able to help :P  And thanks for the thanks ^^

---

### Post by nickdbliss on 2008-06-04
Heythanks for the help dude. i was trying to fix the backspace problem and function key thing. Now lemme give this solution a try.will tell u the result.:)

---

### Post by nickdbliss on 2008-06-04
:confused: ok backspace problem is solved but i am still not able to make function key work. Maybe some other problem.

---

### Post by nickdbliss on 2008-06-08
Solved!! Thanks :popcorn:

---

### Post by Yellow Pasque on 2008-06-08
> I have noticed that when I plug earphones into my laptop that the speakers still play.

Have you solved this? Try: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

You can also try building the latest version of ALSA (1.0.17-rc1) from source: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by bittenmonkey on 2008-06-11
I will try this 2nite and post results, cheers.

---

