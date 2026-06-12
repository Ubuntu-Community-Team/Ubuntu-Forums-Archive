---
title: "New to ubuntu (but love it) a couple questions"
date: 2008-09-29
forum: General Help
---

### Post by tenderdefender on 2008-09-29
Hi, im new to linux (fairly new) .. i havent used it since redhat hurricane 5.0 haha.. anyway this distro is amazingly solid, i was trying linux mint with tons of crashes and failures non stop.. but ubuntu is working flawlessly, its 8.04 i think.

Anyway, my question is, -- when im in a full screen game, like warsow -- how do i ALT+TAB out back to the desktop or minimize it like in windows XP? or is that possible? i was looking on the wiki pedia at keyboard shortcuts and combinations but none of them seemed to do what i needed. 

Also i noticed that when i run 1 application that takes sound (like movie player) my sound in other things cuts out, like a game for instance.. yet in windows XP i can do multiple sound instances (two songs at once, two videos with sound at once, a game and a movie.. or even more) .. i was wondering if theres a way to fix that in ubuntu?

again thanks for all the help, I appreciate your work :KS

---

### Post by Uchiha_madara on 2008-09-29
press ctrl+alt+(Left or right)arrow it is change the workspace(the Desktop) you work on to anther...

---

### Post by tenderdefender on 2008-09-29
> **Uchiha_madara said:**
> press ctrl+alt+(Left or right)arrow it is change the workspace(the Desktop) you work on to anther...


Ah very nice technique, but that doesnt solve my problem, im wondering how to minimize a full screen application "like warsow" so i can multitask at the desktop.

I execute a game, that switches to full screen, now while im in the game, how can i minimize it to the task bar? Sorry for not being more clear in my quesiton, that CNTRL+ALT+arrow works great though for quickly moving from desktop to desktop :) thanks!

---

### Post by mindoms on 2008-09-29
If the application (ie the game) catches the keyboard-events and doesnt pass it to your window-manager then youll be out of liuck, i guess.
but try alt+F9 or look at
System->preferences->keyboard shortcuts
in the Windows-management section. You can also change them there

---

### Post by mindoms on 2008-09-29
and to the sound thing.

This usually happens when Your Soundcard doesnt support hardware-mixing (combining different sounds), and software mixing isn't enabled.
In Ubuntu 8.04 Pulseaudio should be doing this. 

we need more info to fix this. please post the output of the following commands:
```

cat ~/.asoundrc
cat ~/.asoundrc.asoundconf 
aplay -l 
ps -C pulseaudio
ps -C esd
ps -C arts
lsb_release -d

```

---

### Post by tenderdefender on 2008-09-29
> **mindoms said:**
> and to the sound thing.

This usually happens when Your Soundcard doesnt support hardware-mixing (combining different sounds), and software mixing isn't enabled.
In Ubuntu 8.04 Pulseaudio should be doing this. 

we need more info to fix this. please post the output of the following commands:
```

cat ~/.asoundrc
cat ~/.asoundrc.asoundconf 
aplay -l 
ps -C pulseaudio
ps -C esd
ps -C arts
lsb_release -d

```

Well alt+f9 doesnt work, and neither does switching desktops.. there are w few hacks for the full screen thing, but in general i guess it isnt really implemented in any linux distros as i've read, alot of gamers are having this issue. 

as for the audio, heres the g00ds:

```

defender@tendernet:~$ cat ~/.asoundrc
cat: /home/defender/.asoundrc: No such file or directory

defender@tendernet:~$ cat ~/.asoundrc.asoundconf
cat: /home/defender/.asoundrc.asoundconf: No such file or directory

defender@tendernet:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


defender@tendernet:~$ ps -C pulseaudio
  PID TTY          TIME CMD
 6226 ?        00:00:00 pulseaudio

defender@tendernet:~$ ps -C esd
  PID TTY          TIME CMD

defender@tendernet:~$ ps -C arts
  PID TTY          TIME CMD

defender@tendernet:~$ lsb_release -d
Description:	Ubuntu 8.04.1


```

again thank you for assisting me :)

---

### Post by tangibleorange on 2008-09-29
I have a sound card similar to yours. I think the problem is related to pulseaudio. try this:

System -> Preferences -> Sound

And change everything to ALSA. see if that helps.

---

### Post by mindoms on 2008-09-29
> **tangibleorange said:**
> I have a sound card similar to yours. I think the problem is related to pulseaudio. try this:

System -> Preferences -> Sound

And change everything to ALSA. see if that helps.

If that didnt work, then set everything back to pulseaudio and run this in a terminal
```
asoundconf set-pulseaudio
```
I'm not sure if a reboot is necessary.(guess not)

---

### Post by hyper_ch on 2008-09-29
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by tenderdefender on 2008-09-29
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Oh i apologize about that, i'll see if i can edit it here

---

### Post by tenderdefender on 2008-09-29
> **tangibleorange said:**
> I have a sound card similar to yours. I think the problem is related to pulseaudio. try this:

System -> Preferences -> Sound

And change everything to ALSA. see if that helps.

This did have an effect - on the 2nd audio instance that application would instantly freeze (like if i pressed play on the music player, that program would lock up)

---

### Post by tenderdefender on 2008-09-29
> **mindoms said:**
> If that didnt work, then set everything back to pulseaudio and run this in a terminal
```
asoundconf set-pulseaudio
```
I'm not sure if a reboot is necessary.(guess not)

You sir just fixed my problem, i did as you asked and set them all to pulse audio in system > sound, then in terminal I typed

asoundconf set-pulseaudio 

it said nothing to me, but i rebooted the machine. 

now i can watch a movie and play a song!! THANK YOU! 

And thanks to every one else who pitched in to assist *bows* I appreciated it greatly, i may never return to windows yet hahaha :D

---

