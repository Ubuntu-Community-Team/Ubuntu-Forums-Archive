---
title: "ASUS Eee PC 1005HA Touchpad Disable/Re-enable script?"
date: 2014-05-22
forum: Hardware
---

### Post by tmcclelland472 on 2014-05-22
I saw this somewhere, and now I can't find it now that I need it. It's driving me crazy that my buttons for it don't work. Can someone please lead me to the script? I think it might have been a thread on here, but I don't remember.

---

### Post by sudodus on 2014-05-22
Do you want Touchpad-Indicator? There are several tutorials on the internet. It may take some time until it works for the newest version of Xubuntu.

Otherwise you can check this wiki page

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

-o-

Instead of Touchpad-Indicator you can add the following function to .bashrc and use the alias TT to toggle the touchpad on/off from a terminal window.

```
alias TT='touchpad-toggle'

###

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT
```

---

### Post by tmcclelland472 on 2014-05-22
> **sudodus said:**
> Do you want Touchpad-Indicator? There are several tutorials on the internet. It may take some time until it works for the newest version of Xubuntu.

Otherwise you can check this wiki page

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

-o-

Instead of Touchpad-Indicator you can add the following function to .bashrc and use the alias TT to toggle the touchpad on/off from a terminal window.

```
alias TT='touchpad-toggle'

###

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT
```

I used Touchpad-Indicator and it was okay. I remembered a little bit more about this script. You could put it in your Home folder and stuff like that.

---

### Post by tmcclelland472 on 2014-05-22
Anything guys? Kinda depending on you...

---

### Post by sudodus on 2014-05-23
> **tmcclelland472 said:**
> I used Touchpad-Indicator and it was okay. I remembered a little bit more about this script. You could put it in your Home folder and stuff like that.

> **tmcclelland472 said:**
> Anything guys? Kinda depending on you...

I don't understand what you want.

- Do you want Touchpad-Indicator, and it does not work in a new version of Ubuntu?

- Do you want something else? In that case please describe it with more details :-) What is it supposed to do?

---

### Post by tmcclelland472 on 2014-05-23
> **sudodus said:**
> I don't understand what you want.

- Do you want Touchpad-Indicator, and it does not work in a new version of Ubuntu?

- Do you want something else? In that case please describe it with more details :-) What is it supposed to do?
I don't want Touchpad-Indicator, since once I disable my touchpad I have to reboot or find a mouse to re-enable the touchpad.

I want something else. I remember it being a script that you saved in your Home folder and then you would go into the keyboard settings (where you can change the hotkeys) and then you make the script the command.

Do you know what I mean (I know it's probably worded terribly)?

---

### Post by sudodus on 2014-05-23
You *can* use Touchpad-indicator to re-enable the touchpad without a mouse

- do it from a terminal window
- do it via the default hotkey combination or make an own hotkey combination.

I'm sorry but I don't know the script you want. I hope it will ring a bell for someone else who is reading your thread ...

You can also search the internet with a suitable search phrase and quickly browse through some of the links. Maybe you will recognize it at one of those links.

---

### Post by tmcclelland472 on 2014-05-23
> **sudodus said:**
> You *can* use Touchpad-indicator to re-enable the touchpad without a mouse

- do it from a terminal window
- do it via the default hotkey combination or make an own hotkey combination.

I'm sorry but I don't know the script you want. I hope it will ring a bell for someone else who is reading your thread ...

You can also search the internet with a suitable search phrase and quickly browse through some of the links. Maybe you will recognize it at one of those links.

That stinks. Thanks for the help though. I really appreciate it.

---

### Post by jeremy31 on 2014-05-23
I know what you mean but not at my computer right now.  I did something similar for brightness control


This page has a few different scripts and some info on how to bind the script to a keypress
[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

---

### Post by jeremy31 on 2014-05-23
copy this into a text editor and save it to your home folder as touchpadtoggle 
> [COLOR=#333333][FONT=UbuntuMono]# toggle synaptic touchpad on/off[/FONT][/COLOR]
# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi [COLOR=#333333][FONT=UbuntuMono]exit 0[/FONT][/COLOR]

after saving to your home folder, open terminal and use > chmod +x touchpadtoggle

I have to reboot into ubuntu and will return for the rest, if you want to see if it works, in terminal type > ./touchpadtoggle and see if it works

Go into settings in Ubuntu and select keyboard and click on the shortcuts tab, click on the "+" at the bottom of the window to add a shortcut, you can name it toggletouchpad or whatever you want but the command has to be > ./touchpadtoggle once you click apply, it will show your new shortcut as disabled.  Click on disabled and press whatever key or key combo that you want to use but I would suggest something like CTRL+F1 as the FN+ options are usually taken or won't register for shortcuts

The script in this post was actually one from [https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

---

