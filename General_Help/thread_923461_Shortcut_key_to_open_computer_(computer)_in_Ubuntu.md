---
title: "Shortcut key to open computer (computer:///) in Ubuntu"
date: 2008-09-18
forum: General Help
---

### Post by netlaptop on 2008-09-18
I have been using Windoze for years. Now I switch to Ubuntu and I really love it. It runs so quickly.

As my habit, I love using shortcut keys in Window. And I like using shortcut key Window + E to open My Computer in Window.

So I would like to use this shortcut key Window + E or something like that to open Computer (computer:///) in Ubuntu. I have searched around on the Internet but no luck. 

Please tell me how we use any shortcut key to open Computer (computer:///) in Ubuntu. Is it possible?

Thank you in advance!

---

### Post by pedro3005 on 2008-09-18
do you run compiz? if you do, you can go to the compiz settings (System > Advanced Desktop Effects Settings), then go to General Options. On the tab Commands, click Commands to expand and type nautilus computer://  on command line 0. Then click Key Bindings to expand, then click the Disabled button on Run command 0, Then mark Enabled, click Grab Key Combination and press Windows+E (or whatever shortcut you'd like).. Its then set.. You can also use those commands to a lot more options, they're great.:)

---

### Post by rbc on 2008-09-18
Try installing xbindkeys and xbindkeys-config from synaptic. I have not figured out how the Windows key is recognized in Ubuntu, so use Alt+e to open Computer. Bind it to whatever shortcut keys you want, and the command to open Computer is:
nautilus --no-desktop computer:

---

### Post by Titan8990 on 2008-09-18
Windows key in Ubuntu is referred to as the "Super" key (atleast in Compiz).

---

### Post by rbc on 2008-09-18
Thanks Titan. I tried Super and Super L, because that's how System-->Preferences-->Keyboard Shortcuts recognizes it, but that didn't work. The OP got me interested in this again, and I did end up finding the answer. Using xbindkeys-config, you can click the Get Key button, then the Windows key (or whatever other key), and xbindkeys fills the info in for you (how it sees the key). Then I added "+e" to the end of that, and voila, Windows + e opens Computer

---

### Post by netlaptop on 2008-09-19
Thank you very much much much!

It is great! Luv Ubuntu community.

Cheer!

---

### Post by nklatt on 2008-10-21
In case anyone else comes to this thread looking for this, unlike running Nautilus from the shell (which defaults to ~, the home folder) I have to pass in the URI (e.g., ~ :) in order for the browser to come up from the Compiz keybinding.

---

### Post by wensveen on 2008-11-03
Thanks nklat, that was very useful! I couldn't figure out why my keybinding stopped working. Now it works again.
Thanks

---

### Post by Mega_Mike on 2008-11-03
> **nklatt said:**
> In case anyone else comes to this thread looking for this, unlike running Nautilus from the shell (which defaults to ~, the home folder) I have to pass in the URI (e.g., ~ :) in order for the browser to come up from the Compiz keybinding.

This was my only "bug" when I upgraded to Intrepid from Hardy.  I had to change the command to **nautilus --no-desktop ~** to get it to launch from the compiz key bindings.

Thanks a ton for figuring this out!

---

### Post by smdali on 2011-01-02
[SIZE=3]To create a shortcut key for My Computer in Ubuntu:

open **system > preferences > keyboard shortcuts**.

click Add button, now dialog box will opens and write as

Name:** Computer**
Command: **nautilus computer://**

then click apply button.

then click on corresponding to computer row shortcut, it will shows as NEW KEYS.then

press** window key+E** on keyboard

and close dialog box...Enjoy[/SIZE]

---

