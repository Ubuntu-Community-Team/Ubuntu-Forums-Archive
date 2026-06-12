---
title: "[SOLVED] Nvidia setting for TWINVIEW does not stick after restart"
date: 2008-10-30
forum: Hardware
---

### Post by ptgood on 2008-10-30
--Ubuntu 8.10 64BIT
--Nvidia driver 177.80
--SERVER VERSION NUMBER 11.0
--SERVER VENDOR VERSION 1.5.2 (10502000)
--NV-CONTROL VERSION 1.17

After setting and applying the changes for a dual screen TWIN VIEW, everything works fine.

When pressing the button: "SAVE TO X CONFIGURATION FILE", the "Nvidia X server setting window" shuts down.

After restart everything is again as default.

WHY??!?!?!?!?!?!?

---

### Post by teaker1s on 2008-10-30
have you hit the save xserver configuration tab, without this you'll find that changes will not stick in xorg.conf.

---

### Post by TobiO on 2008-11-01
Same Problem: Every time I hit the "save configuration" nvidia-settings exits.

Error in Syslog:
```
Nov  1 11:43:49 tobias-desktop kernel: [ 2438.526674] nvidia-settings[7757]: segfault at 10 ip 0000000000463b1c sp 00007fff550d4670 error 4 in nvidia-settings[400000+9e000]

```

Nothing new is written in xorg.conf.

---

### Post by spiderweb on 2008-11-01
I also have this problem, and as a complete newbie have no idea how to fix it. I am using Ubuntu 8.10 32-bit edition and my graphics card is a GeForce 8400M GS.

---

### Post by Dilligaf on 2008-11-01
Run  sudo nvidia-xconfig  after backing up xorg.conf. This will write a new xorg.conf that nvidia-settings likes.

Mike

---

### Post by ptgood on 2008-11-01
So, like this worked for me:

[LIST]sudo nvidia-xconfig
[/LIST]

[LIST]
Run again the NVIDIA X server settings, and press the button **SAVE TO X CONFIGURATION FILE**
[/LIST]

[LIST]
[*]This message appeared: **Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.**
[/LIST]

[LIST]
[*]Press the button **SAVE TO X CONFIGURATION FILE** again
[/LIST]

[LIST]
[*]Press the button **SHOW PREVIEW**
[/LIST] 

[LIST]
[*]Copy the content of the preview file
[/LIST]

[LIST]
[*]Manually paste onto the /etc/X11/**xorg.conf** file
[/LIST]

After restarting everything was set as before!!
Ciao

---

### Post by PapaGigas on 2008-11-03
> **ptgood said:**
> So, like this worked for me:

[LIST]sudo nvidia-xconfig
[/LIST]

[LIST]
Run again the NVIDIA X server settings, and press the button **SAVE TO X CONFIGURATION FILE**
[/LIST]

[LIST]
[*]This message appeared: **Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.**
[/LIST]

[LIST]
[*]Press the button **SAVE TO X CONFIGURATION FILE** again
[/LIST]

[LIST]
[*]Press the button **SHOW PREVIEW**
[/LIST] 

[LIST]
[*]Copy the content of the preview file
[/LIST]

[LIST]
[*]Manually paste onto the /etc/X11/**xorg.conf** file
[/LIST]

After restarting everything was set as before!!
Ciao

I have a better method (i think, lol):

alt + f2 > sudo su > run in terminal > run

password > enter

nvidia-xconfig > enter

nvidia-settings > enter

nvidia x server > x server display configuration > "edit settings"

save to x configuration file > merge with existing file > save

quit > quit

ctrl + alt + backspace (or reboot if u need 2)


Hope it works 4 u as well... ;)

---

### Post by joel.whitney on 2008-11-06
Just wanted to chime in:

I had the exact problem described above, and this method fixed it perfectly.

I must admit that I don't understand why this is the case (I'm very new to Ubuntu), but I thank you all the same!

---

### Post by godvalve on 2008-11-07
**My good God!!!** Getting twinView to work was like pulling $#@!'n teeth! At first I was getting this completely random message about "Failed to set MetaMode (1) ... blah, blah" and then once I made it work (seemingly at random), I couldn't get the configuration to save to the xconf file. PapaGigas method was the key to getting this whole mess to save permanently (once twinview is already working).

Caution to other users: if you are dealing with similar issues to myself and you use PapaGigas method, you will be informed by the system the first time you type "nvidia-settings" that there was a problem with your existing xconfig file and that a backup couldn't be made. The final line of this message is that a new file has been created. Type "nvidia-settings" again and follow the rest of PapaGigas instructions and everything will work well for you. It did for me.

Thank you PapaGigas.

---

