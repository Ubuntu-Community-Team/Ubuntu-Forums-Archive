---
title: "ESC key registers as XF86AudioPlay"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by montag451 on 2006-07-17
Recently my ESC key on my laptop started registering as a multimedia key.

I've run xev to diagnose and xkeycaps to see if I could use it to fix the problem. If I click on the ESC key in xkeycaps and select restore to default, the ESC key registers correctly. However, when I reboot, something is remapping it to XF86AudioPlay.

I tried using xkeycaps to create an xmodmap file that would remap the ESC key to its correct value. That didn't work, so I made an xmodmap file that totally remapped the keyboard to its correct settings. Even though this is loading up on startup, ESC still registers as XF86AudioPlay.

I assume there's some rogue xmodmap file that's remapping the ESC key, but I can't locate it and I'm not quite sure where to look. All the files I get when I do a search for "xmodmap" are defaults for different languages.

Anyone have any suggestions?

**Edit:** This problem is on an Acer TravelMate 8204 with a p104 keyboard.

---

### Post by mscman on 2006-07-17
What software (if any) have you installed recently? Any multimedia software? This could be remapping your ESC key due to some configuration settings in the software. The other thing you could do would be the same as my fix to end the SHIFT+BACKSPACE nightmare that would kill X when I installed Compiz: create a small one line script that issues the modmap command to remap the ESC key and add that to your startup applications in System -> Preferences -> Sessions.

---

### Post by montag451 on 2006-07-18
I did try your latter suggestion already but generated the file through xkeycaps; I haven't tried manually yet. To the former, I recently installed mplayer and xine while working on getting proprietary formats and DVDs to work.

---

### Post by montag451 on 2006-07-18
I recently tried to fix the problem by running xmodmap at startup. Here's what I've got.

Under System->Sessions in the Startup Programs tab, I have the following line:
```
xmodmap ~/.xmodmap-lucca
```

The file itself contains the following text:
```
keycode 0x09 = Escape
```

This hasn't fixed the problem so far.  Any insight out there?

---

### Post by montag451 on 2006-07-20
Bump and update.

I did not mention earlier: If I go to System->Preferences->Keyboard Shortcuts and type ESC for one of the entries, I get XF86AudioPlay. If I try again, I get XF86AudioNext. If I try again, it tries to use 0x09. I noticed that 0x09 corrosponds to the Escape value and since this is bound to something else, this might explain why ESC never registers.

However, this leads to another problem: Why isn't the ESC button disabling items in the Keyboard Shortcuts programs?

Any insight into any of these problems would be greatly appreciated.

---

### Post by Echow on 2006-08-20
major bump. I am having exactly the same problem. How it works is:
I boot up, open keyboard shortcuts, try to set any shortcut, and it works first time. However, subsequent attempts to set the shortcut with the same key involved (doesn't matter if i add alt/ctrl) the key becomes xf86audioplay, and then begins to alternate between 0x0*something* and xf86audioplay. This also renders the key useless. However, if i set my keyboard layout to somethin different, then all my keys are reset again.

Hope someone can solve this strange problem.
Ed

---

### Post by elyk on 2007-03-05
I've got a similar problem, only it's my home key that's been mapped as xf86audioplay. I think this started when I tried to map fn+home as audio play in the keyboard shortcuts dialog, but it didn't recognize the function key and recorded the shortcut as just home. Where does the keyboard shortcuts utility store its config files? I'd like to try deleting them and see what it does.

---

