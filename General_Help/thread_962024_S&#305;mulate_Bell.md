---
title: "S&#305;mulate Bell"
date: 2008-10-28
forum: General Help
---

### Post by R2D2! on 2008-10-28
([http://ubuntuforums.org/showthread.php?t=955131](http://ubuntuforums.org/showthread.php?t=955131))
My laptop lacks the aud&#305;ble bell feature. How can I s&#305;mulate &#305;t w&#305;th my speakers?

I have Ubuntu 8.04 Hardy, on a Lenovo laptop.

—Ilhu&#305;temoc &#948;

---

### Post by ciscosurfer on 2008-10-28
```
echo -e '\007\c'

tput bel
```Now here's your challenge: simulate an audible bell changing its pitch/frequency and its duration.  Good luck!

---

### Post by R2D2! on 2008-10-28
Er, that &#567;usts &#8220;sends&#8221; a bell, but &#305;f I don't have the hardware, I won't hear &#305;t.

What I want &#305;s that the bell &#305;s sent to my speakers (at least that &#305;s poss&#305;ble w&#305;th W&#305;ndows, but I don't know how)

&#8212;Ilhu&#305;temoc &#948;

---

### Post by ciscosurfer on 2008-10-28
I guess I'm not following you.  Those commands do send an audible bell to your onboard, built-in pc speakers (the hardware you refered to in your first post, at least that's how I read it).  In any event, an audible bell won't get sent to external speakers.  So what precisely do you mean when you want the bell sent to your speakers?

I noticed you had some trouble with the audio on your lenovo about 3 weeks back in this post ([http://ubuntuforums.org/showthread.php?t=939434)]("http://ubuntuforums.org/showthread.php?t=939434%29...have") Are you trying to send a system bell that normally goes to your onboard pc speakers (typically located on your motherboard) to your external speakers?  If that's the case, I'm not sure how to assist you further, though I'm sure some of the programmers on the forums can assist you in redirecting it to your audio card if that's what the original intent was.  But for good measure, let's check to see if you've somehow turned off the pcspkr module that controls your onboard speaker(s) by running this command```
lsmod | grep pcspkr
```If you get a line returned like for example```
pcspkr                 10624  0
```then your pcspkr module is on/okay.  If not, let's turn it back on```
sudo modprobe pcspkr
```If you are using gnome-terminal, check to make sure under Edit > Profile Preferences the Terminal bell option is checked on.> ... but &#305;f I don't have the hardware, I won't hear &#305;tI've never come across any pc, desktop or laptop, that doesn't have onboard speakers.  If we're talking about your external speakers, are your mixer channels muted?

---

### Post by Sam on 2008-10-28
There is this: [http://www.carcosa.net/jason/software/beep/](http://www.carcosa.net/jason/software/beep/)

> This is a kernel module that lets you replace the speaker beep with a userspace daemon that can perform the action of your choice, such as playing a sampled sound.

However I never tried it myself...

---

### Post by R2D2! on 2008-10-28
lsmod | grep pcspkr returns the follow&#305;ng:
```
pcspkr                  4224  0
```
but I can't hear anyth&#305;ng sent to my PC speaker.

I have a v&#305;sual bell, but that gets annoy&#305;ng after a wh&#305;le.

When I was &#305;n W&#305;ndows V&#305;sta, the bell was sent to external speakers, but I don't get anyth&#305;ng here...

---

### Post by R2D2! on 2008-11-22
OK, I found &#305;n gconf the opt&#305;on /desktop/gnome/peripherals/keyboard/bell_custom_file , and I l&#305;nked a WAV f&#305;le there; but that does noth&#305;ng. I've checked bell_mode to be “custom”, and I've rebooted, but &#305;t doesn't work. What can I do??

—Ilhu&#305;temoc &#948;

---

