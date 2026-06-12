---
title: "dmesg output"
date: 2008-08-22
forum: General Help
---

### Post by waitcursor on 2008-08-22
Hello All,

I'm new to ubuntu and need some information about my DMESG output, can someone help me with the errors, can I fix them?

Thanks for your assistance.
Waitcursor

---

### Post by qstraza on 2008-08-22
Your fn keys on your vaio doesnt work?

---

### Post by waitcursor on 2008-08-22
ideed I have a VAIO FZ11E, according to forum messages I've red that the brightness/zoom/fn F12/ don't work, so I stopped looking for a solution.
Are these those error messages that are outputted in the dmesg file?
thanks and regards

---

### Post by qstraza on 2008-08-22
well same here, i have vaio myself, and i did not succeed in setting up the drivers. 
But i have a workaround for brightness. Install smartdimmer, oh this only works if you have nvidia. Do you have it?  If you have, i can explain it to you

---

### Post by waitcursor on 2008-08-22
yes I have nvidia, :-)

---

### Post by qstraza on 2008-08-22
so,
```
sudo apt-get install smartdimmer
```

Since you use gnome and i use kde, cant really tell you where to set this up, but you will find it.

Add a shortcut for win_key+F5 and win_key+F6, you cant use FN key, but try it, maybe it works in Gnome but i doubt it.

These shortcuts in kde are in System settings -> accessibility -> input action, if this helps you find it in gnome.

Set a winkey+F5 so it executes 
```
smartdimmer -d
```

and winkey+F6
```
smartdimmer -i
```

Thats it, you are able to change brightness :p kinda ;)

I also added winkey+F7 which changes from the darkest to the brightness and vise versa. If you like this idea, heres a script:
```
 
#!/bin/bash
var=`/usr/bin/smartdimmer -g | awk '{print $3}'`

if [ $var = 21 ]; then
    smartdimmer -s 3
else
    smartdimmer -s 21

```

save it to some file, chmod +x the file, and set winkey+F7 to execute it...

Hope this helps.

About other fn keys, volume up and down and mute should work out of the box, at least mine do (kubuntu 8.04), other fn keys are useless...

---

### Post by waitcursor on 2008-08-22
> **qstraza said:**
> so,
```
sudo apt-get install smartdimmer
```

Since you use gnome and i use kde, cant really tell you where to set this up, but you will find it.

Add a shortcut for win_key+F5 and win_key+F6, you cant use FN key, but try it, maybe it works in Gnome but i doubt it.

These shortcuts in kde are in System settings -> accessibility -> input action, if this helps you find it in gnome. Cannot find this in Gnome, should I install this??

Set a winkey+F5 so it executes 
```
smartdimmer -d
```

and winkey+F6
```
smartdimmer -i
```

Thats it, you are able to change brightness :p kinda ;)

I also added winkey+F7 which changes from the darkest to the brightness and vise versa. If you like this idea, heres a script:
```
 
#!/bin/bash
var=`/usr/bin/smartdimmer -g | awk '{print $3}'`

if [ $var = 21 ]; then
    smartdimmer -s 3
else
    smartdimmer -s 21

```

save it to some file, chmod +x the file, and set winkey+F7 to execute it...

Hope this helps.

About other fn keys, volume up and down and mute should work out of the box, at least mine do (kubuntu 8.04), other fn keys are useless...

BTW are you able t use suspend and hibernate? I saw a threat about this but adding vaio yp HDA didn't solved this for me.

Anyway thanks for your assistance.

---

### Post by qstraza on 2008-08-22
I can suspend to disk or ram, but not via fn keys, but via power manager

---

### Post by waitcursor on 2008-08-22
> **qstraza said:**
> I can suspend to disk or ram, but not via fn keys, but via power manager

This is what I ment (mean), I can get to where the screen goes black, but I still see a cursor blinking in my left upper screen cornder, also the led stays green, power button doesn't work anymore, so I have to hard reboot.

But you're smartdimmer tools looks promising, only issue is that I cannot find the keymap tool in gnome menus.

Anybody here who can point me out in the right direction?

---

### Post by qstraza on 2008-08-22
Smartdimmer is only for brightness it does not efect suspend feature. Well my notebook reboots faster as it does suspend to disk. Suspend to ram uses power to power up the ram, so i dont like it...

So i dont really tell you about suspend thing...

Hope you find key bindings in gnome ;)

---

### Post by meditatingfrog on 2009-08-02
> **qstraza said:**
> I can suspend to disk or ram, but not via fn keys, but via power manager

I have a Toshiba Satellite.  We might be able to help each other out.  I can suspend to ram using the function-f3 key on my laptop (shortcut keys for suspend), but not the hibernate (suspend to disk) shortcut keys.

I'm not sure what controls Ubuntu's ability to use these function keys.  I've looked in System->Preferences->Keyboard Shortcuts (there is only a place for a shortcut for suspend, mine says disabled), and System->Preferences->Keyboard.  In System->Preferences->Keyboard I changed the layout to the only Toshiba keyboard layout that existed, but it didn't seem to change anything.  Maybe I need to find out where I can create my own keyboard layout specifically for my laptop.

I'm getting this idea that Ubuntu is meant to be customized at this stage in the game by the individual user because there aren't enough people using it, troubleshooting it, and working on it.

---

