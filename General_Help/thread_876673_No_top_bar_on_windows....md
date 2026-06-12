---
title: "No top bar on windows..."
date: 2008-08-01
forum: General Help
---

### Post by Animeniac on 2008-08-01
Now everytime I use ubuntu, there is no top bar on the windows (the bar with the title, close button, maximize button, etc.). Maybe it is due to the NVIDIA X Server Settings - I ran as root to save my configuration to the X configuration file.

How can I fix this problem?

---

### Post by tuxxy on 2008-08-01
What window manager is this emerald?

---

### Post by plinydogg on 2008-08-01
I had a similar problem. It was easily fixed by switching out of compiz (i.e., back to metacity and then restarting compiz). good luck!

---

### Post by Animeniac on 2008-08-01
I even restarted the computer and there is **still** no top bar on windows.

---

### Post by overdrank on 2008-08-01
> **Animeniac said:**
> Now everytime I use ubuntu, there is no top bar on the windows (the bar with the title, close button, maximize button, etc.). Maybe it is due to the NVIDIA X Server Settings - I ran as root to save my configuration to the X configuration file.

How can I fix this problem?

Oh now you are blaming me lol
are you using compiz. If so you may check in the advance desktop settings that the window decorated is check. and like tuxxy asked you can try the command ```
emerald --replace
```

---

### Post by Animeniac on 2008-08-01
Okay, I was trying to get the Windows Vista Aero theme to work on Windows Vista Home Premium, by following the tutorial videos, especially the ones for Windows Vista Basic, but it never worked. It turned out that I don't have a compatible graphics card for Windows Aero.

Perhaps changing the settings in 'regedit' and 'stpooing' and starting 'uxsms' in the command prompt was the cause of the top bar in the windows in Ubuntu to not show...

---

### Post by Animeniac on 2008-08-01
> **overdrank said:**
> Oh now you are blaming me lol
are you using compiz. If so you may check in the advance desktop settings that the window decorated is check. and like tuxxy asked you can try the command ```
emerald --replace
```

I can't even see the text in the Terminal, nor the animation after I click an icon in the right of the 'System' tab. And I'm not using 'compiz'...

---

### Post by Animeniac on 2008-08-01
I installed emerald. I have used another desktop environment (Xcfe) and ran Terminal on there and put the code 'emerald --replace' and then I got the error '(emerald:8122): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8'. I even typed the code as superuser (su) and I still got this error.

---

### Post by Animeniac on 2008-08-01
I removed both compiz and emerald, and then got the top bar back, as well as the text in Terminal, but no animation after I click an icon on the right of the System tab. Perhaps compiz is needed for the animation.

But seriously, what is compiz for, anyways?

---

### Post by md389 on 2008-08-01
```
metacity --replace
```

```
compiz --replace
```

that generally does the trick for me.

---

### Post by Animeniac on 2008-08-01
Hey. That 'metacity --replace' code worked. Thanks, pal.

---

### Post by Animeniac on 2008-08-01
Everytime I restarted Ubuntu, I STILL get no top bar on windows. I tried compiz --replace, but all I got were a whole bunch of errors:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0185 (rev c1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x2000020 to texture

/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x2000020 to texture

Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

```

I restarted the computer after that there is STILL no top bar on the windows.

I STILL want to know how to fix the error so that next time I can see the top bar on the window and the animation. :cry:

---

### Post by websurrfr on 2008-08-12
I am having this same problem after installing Emerald.  It occurs with any theme I use.  If I open a new program it opens in the top left corner of the screen with no top bar.  The top bar appears if I Alt+click to drag the window around but I'd like it to automatically appear.  

I can't figure out what setting is doing this.  As soon as I stop using Emerald the issue goes away.

edit

Actually it seems the problem isn't that the bar isn't there, it's that when I open a new program the window for that program starts up so high that the bar is there, but it's off screen.  So I guess the solution is to make new windows open lower on the screen but I can't seem to figure out how to do that either.  I also tried moving the top panel to the bottom because that was what was covering the top bar on windows, but when I did that the new windows just opened up even higher so I still couldn't see the top bar.

---

### Post by websurrfr on 2008-08-13
I found a solution to my problem.  I hope this works for others.

System > Preferences > Advanced Desktop Settings

Select Place Windows

Change Placement Mode to Centered

Hit Back and check the box next to Place Windows.

Any new windows you open should now be in the middle of the screen with the top bar visible.

---

