---
title: "Logitech mouse in Edgy (was working in Dapper)"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Mopatop on 2006-10-27
Hey

So my Logitech MX700 was working fine in Dapper. After I did the (painful) upgrade to Edgy, my thumb buttons are no longer working. In Dapper, I had followed previous guides in these forums, which resulted in my config files pasted below. This worked fine in Dapper.

xorg.conf:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "6 7"
EndSection
```

(Yes I know the Emulate3Buttons line is wrong, but I like it)

imwheelrc (last bit of):

```
".*"
None, Up, Alt_L|Left
None, Down, F5

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
```

(That does F5 - refresh - for top thumb, back for bottom thumb)

And this is all activated by these two commands:

```
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 10 11" &
exec imwheel -k -b "89" &
```

When I run the imwheel command in a terminal I get this:

```
rob@aranea:~$ INFO: imwheel(pid=16409) killed.
INFO: imwheel started (pid=16495)
Unrecognized wheel action in config. Ignoring action.
Down
Unrecognized wheel action in config. Ignoring action.
Down

[1]+  Done                    imwheel -k -b "89"
rob@aranea:~$
```

Those errors about unrecognised actions never used to appear. Does anyone have any ideas about this please? I use these buttons a lot to do my work. I'm a web developer.

Thanks

-Rob

---

### Post by thebinz on 2006-10-28
I too am having the same problem. Ever since i upgraded to edgy my scroll wheel and back & forward buttons have failed to work. 
Im using the Logitech MX700 also. 

Does your scroll wheel work? If so how can i get mine working. 

I have searched and searched and still i am unble to get this damn thing working on edgy.

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Buttons" "7"
	Option "ZAxisMapping" "6 7"
EndSection
```

---

### Post by JaHeinz on 2006-10-31
Alo, I'd like to interject, a Logi trackman ball mouse here, My problem is similar. The movent of the pointer does work fine, minus the buttons. My KB also, will not work. Both KB, and Mouse/buttons did work for the install. Seems a X config problem, and I will attempt to re configure the install. Login works fine, after that, no KB, or mouse button functionality, the OS works fine, as far as i can tell (when I insert the live cd, the file explorer pops up, the screensaver kicks in...etc), it is purely a input problem, from what it seems.

My Logi is connected via USB, and i have a genaric, standard IBM layout KB, via ps/2 . Edgy the OS version.

I did read a previous thread about a microsquash KB, and the recommendation was to enter console, and reconfig the xserver with >sudo dpkg -reconfigure xserver -xorg<

Im assuming theres something similar to for mouse config....

Anyways, ill try it out myself later, do some more homework on this OS, Im not shure if console will open or not at this point. 
>one quik note, seems some settings did not set. The screensaver was a blak screen, im htinking maybe the input cfg may not have set in completely for xserver.

Id appreciate any help, incase I cannot fix this bug on my own...
Greets!

---

### Post by djf_jeff on 2006-11-20
Hi,

Just change :

exec imwheel -k -b "89" &

to :

exec imwheel -k -b "0 0 8 9" &

And eveything will be fine.

---

### Post by Mopatop on 2006-11-20
> **djf_jeff said:**
> Hi,

Just change :

exec imwheel -k -b "89" &

to :

exec imwheel -k -b "0 0 8 9" &

And eveything will be fine.

Cheers mate, this worked a treat. I did have to change "Down" to "Right" in my imwheelrc, but apart from that everything's groovy!

---

### Post by jpaddison83 on 2006-11-24
I put this elsewhere as well but, I think I've tried about 50 different configurations of xorg.conf, imwheelrc and my startup script, but this is what has finally got my MX510 working on Edgy. Hope it helps...

-- /etc/X11/xorg.conf -- (there are no device options I've left out)
[B]Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
EndSection[/B]

--/home/login/mouse-- (my startup script)
[B]#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7" &
exec imwheel -k -b "6 7 8 9" &
exec $REALSTARTUP[/B]

--/etc/X11/imwheel/imwheelrc-- (default with the following appended at the end)
[B]".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right[/B]

---

### Post by ZenX on 2006-12-12
I have tried many other configurations for X, but none of them seems to work CORRECTLY :D Now, my scroll functions like the side buttons should, which is the back/forward in FireFox.... That's just annoying..

---

### Post by ZenX on 2006-12-13
I don't want to seem like a whiner, but could someone maybe paste their Xorg.conf so I could get my mouse to work? =D

---

### Post by Mopatop on 2006-12-13
You need more than just your xorg.conf. I'll do a quick runthrough of what works for me:

[LIST=1]
[*]Install the "imwheel" and "xmodmap" packages
[*]Edit xorg.conf so that your InputDevice section has the following statements:
```
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "6 7"
```
You could also put "Resolution" "800" in there if you wanted
[*]Execute the following commands when your GUI session starts. I think you do this by modifying your GNOME Session properties. I can't remember as I use Xubuntu.
```
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 10 11" &
exec imwheel -k -b "8 9 0 0" &
```
They might have to be started in that order
[*]Optionally edit /etc/X11/imwheel/imwheelrc or create $HOME/.imwheelrc and adjust to taste. You could probably leave this for now.
[/LIST]
When you've done all that, do the ctrl+alt+backspace trick and pray to $DEITY that it works.

---

### Post by _simon_ on 2006-12-13
Just to add a spanner into the works.

I have an MX700 and don't use xmodmap ;)

The only button that does not work is the cruise up button as it seems to be mapped to both up and back.

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Dev Name" "Logitech USB Receiver"
    Option         "Dev Phys" "0000:00:02.0-1/input0"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option         "Resolution" "800"
EndSection

```

---

### Post by ZenX on 2006-12-13
Darn it, still doesn't work. Here's my start-up programs 
```
update-notifier
beryl-manager
exec imwheel -k -b "8 9 0 0" &
/usr/lib/evolution/2.8/evolution-alarm-notify
gnome-power-manager
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 10 11" &
gnome-volume-manager --sm disable
```

---

### Post by tweedledee on 2006-12-15
> **ZenX said:**
> Darn it, still doesn't work. Here's my start-up programs 
```
update-notifier
beryl-manager
exec imwheel -k -b "8 9 0 0" &
/usr/lib/evolution/2.8/evolution-alarm-notify
gnome-power-manager
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9 10 11" &
gnome-volume-manager --sm disable
```

You might want to look at [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441) as an alternative approach that doesn't make use of imwheel.  It's perhaps a little more work to get up and running, but allows for more explicit control and more options than imwheel, and doesn't involve hacking xorg.conf nearly as much (and hence the risk of losing your login).

---

### Post by ironfistchamp on 2007-01-09
> **_simon_ said:**
> Just to add a spanner into the works.

I have an MX700 and don't use xmodmap ;)

The only button that does not work is the cruise up button as it seems to be mapped to both up and back.

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Dev Name" "Logitech USB Receiver"
    Option         "Dev Phys" "0000:00:02.0-1/input0"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option         "Resolution" "800"
EndSection

```

Perfect. The other methods didn't work for me but this is faultless. Even the cruise buttons work. Thanks so much. The only button that doesn't work is the application switcher but that is dependent on Logitech Software (even in windows) that I never use.

Thanks again

Ironfistchamp

---

### Post by malinkie on 2007-01-18
I'm so glad this forum is here :) I spent most of last night trying to get my MX510 thumb buttons working and failed...

I tried following the Dapper guide to use evdev but it broke my xsession every time.

I'll post how i got mine to work once i get there.

-Mal

---

### Post by boast on 2007-02-28
my scroll wheel is acting like the buttons, and the buttons are acting like the scroll wheel.

edgy + mx510

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option         "Resolution" "800"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by boast on 2007-03-02
ok. nm.

Future reference, this worked for me:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option	   "Protocol" "ExplorerPS/2"
    Option	   "ZAxisMapping" "6 7"
    Option	   "Buttons"  "7"
    Option         "ButtonMapping" "1 2 3 4 5 "
    Option	   "Resolution"   "800"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by mayfer on 2007-03-12
worked like a charm on my mx510,
thanks a lot.

---

### Post by m3shuggah on 2007-03-15
My Logitech MX700 required...

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option	   "Protocol" "ExplorerPS/2"
    Option	   "ZAxisMapping" "4 5"
    Option	   "Buttons"  "7"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option	   "Resolution"   "800"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by bryan.taylor on 2007-03-18
After much hacking about I finally got my Intellimouse Explorer 3.0 to work.  It has 7 buttons, but the side buttons map to 8 and 9.  I did the following:

Modify /etc/X11/xorg.conf
```
Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice"
   Option         "Protocol" "ExplorerPS/2"
   Option         "Buttons" "7"
   Option         "ZAxisMapping" "6 7"
EndSection
```

Modify /etc/X11/imwheel/startup.conf
```
# Set this to "1" to make imwheel start along with your X session.
IMWHEEL_START=1

# Specify the command line parameters to pass to imwheel.
IMWHEEL_PARAMS="--kill --buttons '8 9'"
```

Create /etc/X11/Xsession.d/59xmodmap
```
. /etc/X11/imwheel/startup.conf
if [ "$IMWHEEL_START" = "1" ]; then
        exec xmodmap -e "pointer = 1 2 3 8 9 4 5 6 7" &
fi
```

That's it!

---

### Post by fppl on 2007-08-08
By the way,
Button 6 (I did the imwheel -c to figure this out) is the forward button, and 7 is the back button.

Here's my imwheelrc config for firefox

"^Firefox-bin$"
None,Button7,Alt_L|Left
None,Button6,Alt_L|Right

And my xconf mouse config:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "true"
	Option "Buttons" "7"
	Option "ButtonMapping" "1 2 3 7 6"
EndSection

---

### Post by fppl on 2007-08-08
-- wrong thread - looking at like 10 at once...

---

### Post by Wiebelhaus on 2007-08-10
.....

---

