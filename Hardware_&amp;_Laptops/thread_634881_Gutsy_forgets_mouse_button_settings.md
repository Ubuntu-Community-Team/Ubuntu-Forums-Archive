---
title: "Gutsy forgets mouse button settings"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by leona on 2007-12-08
Hi.

I have a standard 3 button optical mouse, PS/2 Type, I've RSI in my right wrist so use my mouse with my  left hand and set it up as such in the mouse settings.

Every now and again, Ubuntu will forget this when I boot and I have to go back to the menu and set it again, When I go into the menu though, the "left handed" option is set, but its just not being apply, so I click to the right hand then back to left hand option and its ok again, until the next time.

The only thing that is non standard in my setup is that I use a KVM to control 2 pc's and a laptop. I don't know if this is upsetting it, but if I switch pc's it doesn't forget the setting, so I can't see that being the issue, but thought I'd mention it.

Is there a script I could run on start up or something to 'ensure' it starts in left handed mode?

Thanks.

---

### Post by Yellow Pasque on 2007-12-08
Hi Leona.

0. In terminal, make sure you have the gconf tools. So:
```
sudo apt-get install gconf2 gconf2-common
```

1. Go to Systems -> Preferences -> Sessions. 
2. You should be greeted with the startup tab, choose it if not. 
3. Click the Add Button.
4. Choose a name for the program (I used "Southpaw" :P) and put it in the name field.
Now, the magic:
5. Put this in the command field:
```
gconftool-2 --set "/desktop/gnome/peripherals/mouse/left_handed" --type Boolean "True"
```
6. Click OK.
7. Make sure your new program (whatever you named it) has a check next to it to enable it.
8. Close that window and get on with your life.

---

### Post by leona on 2007-12-08
Thanks so much, that's excellent.

---

### Post by leona on 2007-12-15
Has been ok for a few days now, but today it started with the mouse buttons in the wrong order again, :(

---

### Post by Yellow Pasque on 2007-12-18
Sorry it didn't work :\  The only thing I can think of is that the X settings are interfering with the Gnome settings.

The next time you log in and find your mouse right-handed, open up /var/log/Xorg.0.log (with gedit) and look for the section where it configures your mouse. It's usually towards the end of the file and looks like this:
```
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
```

So post that and maybe it will give us a clue.

---

