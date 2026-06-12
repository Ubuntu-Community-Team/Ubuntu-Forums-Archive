---
title: "Drivers for Microsoft keyboard"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by EYALf on 2007-12-04
I have microsoft wireless mouse and keboard, I cant get it to work in Ubuntu.

Please help, Im new to ubuntu - from today.

---

### Post by Friek on 2007-12-06
If they're not working at all, I am wondering how you managed to finish the installation ;)
I have a microsoft 4000 keyboard (not a wireless one though) and it's working like a charm.
Do you mean they're not working at all, or some special buttons (like the zoom button on the keyboard) aren't working? On my 4k keyboard, those features (useless, as far as i'm concerned) don't work.

---

### Post by sinbad2699 on 2007-12-06
yea the same wit me - i have an ergo 4k 2 and the special only buttons that work on it are the play/pause, volume and calculator buttons. Everything else either seems to not work at all or not work right. I'm sure that's only cos Ubuntu doesnt no the ASCII code for those buttons, so it doesnt do anything

---

### Post by pointfivezero on 2007-12-06
It is possible to see which buttons are registered with the xserver by running (in a terminal window) the command "xev".

The import bit to watch out for is (for example, when I press the play/pause button on my keyboard):

```

KeyRelease event, serial 29, synthetic NO, window 0x4400001,
    root 0x1a5, subw 0x0, time 2982603133, (175,29), root:(772,60),
    state 0x10, keycode 162 (keysym 0x1008ff31, XF86AudioPause), same_screen YES

```

Notice the part that says:
```

keycode 162 (keysym 0x1008ff31, XF86AudioPause)

```


Test all of you multimedia keys this way (NOTE: some may cause your system to hibernate, start mail or webbrowser etc...) and note which ones work for which keys... 

If all the multimedia keys are registered then you can create hotkey associations in the appropriate application...

Otherwise more drastic action needs to be taken... please let me know and post your registered keys and their keysym by way of reply.

Cheers

---

### Post by tehnad on 2008-03-02
> **Friek said:**
> If they're not working at all, I am wondering how you managed to finish the installation ;)


Probably the same as I did, by plugging in another keyboard until I get the drivers to work since mine isn't working out of the box either.

---

### Post by freerick on 2008-04-06
I just acquired a Microsoft 4000 ergo keyboard (wired) and the following keys special keys are registered and working (on Kubuntu 7.10):

- Multimedia keys (mute, play/pause, volume)
- Calculator (opens Calculator)
- Mail (opens new message with KMail Composer)

All other standard keys seem to be working fine, including print screen, num/scroll lock, pg up/down, etc)

The keyboard also has an F-Lock key; when F-Lock is disabled, xev is showing different keycodes, but nothing happens when F-Mode is not engaged. This is very promising, as it looks like I can easily bind these keys to custom actions using the KDE control center.

To my slight disappointment, these other special keys are not registered:

- Zoom
- Back/Forward
- My Favorites
- Shortcuts 1 - 5

**If anyone knows how to configure the other unregistered special keys (I care especially about the Zoom key, as I would like to use it for scrolling through documents), please let me know. Thanks!**


Overall, I find this keyboard to be very ergonomic and comfortable to use. The keys are very responsive, but not overly sensitive. The ergonomic design takes a bit of getting used to, but it feels *much* more natural.

---

### Post by rhvkl on 2008-05-14
hello,

I have the same problem as freerick, but using LinuxMint 4.0 Daryna. Is there anything a "new-to-linux" can do to fix this issue?

---

### Post by dvwade on 2008-06-03
I am trying Ubuntu 8 with the MS Ergo 4000 keyboard.

The at character which is usually invoked by pressing Shift-2 instead produces ".

Any suggestions as to how to deal with this.

It looks like the question mark character is having a problem as well. It produces a É. Likely there are other problems. I dont go looking for them. I just ran across an apostrophe problem.

I should quit trying more keys I guess.

---

