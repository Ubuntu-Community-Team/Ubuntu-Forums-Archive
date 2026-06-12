---
title: "extra mouse buttons (back button) in intrepid"
date: 2008-11-02
forum: General Help
---

### Post by AtrejuT on 2008-11-02
Hello All,

I have a Microsoft IntelliMouse Optical, 5 buttons + scroll wheel. In the olden days of hardy I could get the extra buttons to work (in particularly the 'back' button on the side of the mouse) by editing xorg.conf. The result looked something like this:
```

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier  "Configured Mouse"
#       Driver      "evdev"
#       Option      "CorePointer"
#       Option      "Device" "/dev/input/event2"
#       Option      "Protocol" "ExplorerPS/2"
#       Option      "ZAxisMapping" "4 5"
#        Option          "Buttons"       "7"
#       Option      "ButtonMapping" "1 2 3 6 7"
#EndSection

```

Now that doesn't work anymore, and I dearly miss this back button functionality. (the mouse wheel and middle click work fine btw)
Apparently in intrepid you have to edit some .fdi-files for HAL to get this working, but I can't figure out what I really have to do, and somehow I don't understand the wiki page... I'm also somewhat reluctant to install imwheel and all that; I never needed it before, and as I said the wheel itself works fine.
So, if anyone has any hints as to how to get this to work, I'd be most grateful...

thanks!

atreju

---

### Post by wgrant on 2008-11-02
See [the documentation on extra mouse buttons](https://help.ubuntu.com/community/ManyButtonsMouseHowto), to which I just added a section button mapping.

---

### Post by IT-Joker on 2008-11-02
I'm be interested in answer for this one too.

> **wgrant said:**
> See [the documentation on extra mouse buttons](https://help.ubuntu.com/community/ManyButtonsMouseHowto), to which I just added a section button mapping.

However, that documentation is for the previous versions. Now the most part of xorg.conf is commented out with a message that we should use HAL instead.
My searching on how to do it in HAL yielded these results:
1. Few docs/howtos on the subject. 
Basically I found: [https://wiki.ubuntu.com/X/Config#Input](https://wiki.ubuntu.com/X/Config#Input) Configuration with HAL for general information
and this one [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) explains how to set up a Logitech mouse. 
2. The second link contains a sentence: "Currently the button mapping described above is being ignored by HAL."
...so from that it seems that the "old way" of mapping buttons in the mouse configuration doesn't work in 8.10.
It suggest to use xmodmap as a workaround.
3. Using the informations grom the above links I tried to create some config file that I thought would work for my mouse, but the only result was that the scroll wheel stopped working too.

---

### Post by AtrejuT on 2008-11-03
Thanks for the help, but unfortunately this doesn't seem to work for me...
Running xinput I get
```

xinput set-button-map "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" 1 2 3 6 7
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  29 (X_SetDeviceButtonMapping)
  Value in failed request:  0x6
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

where I took the 1 2 3 6 7 - in analogy to my old xorg.conf. Using xmodmap gives a similar result. Any further ideas for this?

thanks!

---

### Post by IT-Joker on 2008-11-03
> **AtrejuT said:**
> Thanks for the help, but unfortunately this doesn't seem to work for me...
Running xinput I get
```

xinput set-button-map "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" 1 2 3 6 7
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  29 (X_SetDeviceButtonMapping)
  Value in failed request:  0x6
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

where I took the 1 2 3 6 7 - in analogy to my old xorg.conf. Using xmodmap gives a similar result. Any further ideas for this?

thanks!
I've read somewhere that somehow (weird as it might seem) the buttons labelled 6 and 7 before are labelled 8 and 9 in Intrepid.
It's just a guess, but you might try it.

---

### Post by bnce on 2008-11-03
> **wgrant said:**
> See [the documentation on extra mouse buttons](https://help.ubuntu.com/community/ManyButtonsMouseHowto), to which I just added a section button mapping.

I'm also trying to get the two extra buttons working. I can't get the xinput method working either, using the button mappings from my old xorg.conf or any other combinations I tried.

I read through the fdi file stuff but have no idea what to put in the xml. 

Is there any way of fixing the mouse without having to code xml or imwheel files? or an option somewhere to use the old xorg.conf way of doing things?

---

### Post by IT-Joker on 2008-11-03
Yay!
I was experimenting with xinput and I got the side buttons of my Intellimouse Optical working!

I don't really see too much into it, it's just trial-and-error method ;) So maybe someone with better info would be able to improve the command.

Anyway, this worked for me:
xinput set-button-map "*ImExPS/2 Generic Explorer Mouse*" 1 2 3 4 5 9 8 **6** **7**

You must replace the *ImExPS/2 Generic Explorer Mouse* with your mouse identifier (mine is like this for MS Intellimouse Optical plugged into the PS/2 port. When it's plugged to the USB port, it's like Microsoft Microsoft 5 button mouse with IntelliEye(TM) ... or something like that).

It seems that 6 and 7 are the side buttons of the mouse while positions 8 and 9 mark mapping of the the back/forward buttons.

Also, I found that to avoid the "BadValue" error, you must use the the full row of numbers... ie if you map 9 positions (you have to because the forward/back are positions 8 and 9), you have to use all the numbers from 1 to 9. That's why I used 8 and 9 in the command even though my mouse only has 7 buttons.

Right, now I have a command that works.
How do I make it work permanently, ie without having to type the command every time?

---

### Post by AtrejuT on 2008-11-04
that works for me too! excellent, and many thanks!

the quick and dirty workaround to get it to always work is adding it to gnome-session so it is started along with gnome. but that solution sounds extremely ugly to me ;-)

---

### Post by fanish2009 on 2008-11-28
Good afternoon,
After reviewing all the steps and threads in the forum I came up with my own personal mouse.fdi for the Intellimouse Optical 1.0A:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
[INDENT]  <device>
    [INDENT]<match key="info.capabilities" contains="input.mouse">
        [INDENT]<merge key="input.x11_driver" type="string">mouse</merge>
        <merge key="input.x11_options.Emulate3Buttons" type="string">no</merge>
        <merge key="input.x11_options.Buttons" type="integer">7</merge>
        <merge key="input.x11_options.ButtonMapping" type="integer">1 2 3 8 9</merge>[/INDENT]
    </match>[/INDENT]
  </device>
[/INDENT]</deviceinfo>

Now my back and forward buttons work correctly in Firefox 3.0.4!

Just copy the above XML code, and paste it into a root owned file in the /etc/hal/fdi/policy/mouse.fdi file.

---

### Post by finger51 on 2008-12-03
No luck with that xml for me. still trying to get it fixed. Using a 
"Microsoft Microsoft IntelliMouse? Explorer"

I google it everyday hoping someone found a hack. No luck yet.

---

### Post by gatoraviator on 2008-12-06
IT-Joker

Thanks for the help.  I tried your method and it worked beautifully for me.  Added it to my startup programs in sessions and now a problem that has vexed me since my upgrade is fixed.

Many thanks.

---

### Post by dimamali on 2008-12-16
> **IT-Joker said:**
> Yay!
I was experimenting with xinput and I got the side buttons of my Intellimouse Optical working!

I don't really see too much into it, it's just trial-and-error method ;) So maybe someone with better info would be able to improve the command.

Anyway, this worked for me:
xinput set-button-map "*ImExPS/2 Generic Explorer Mouse*" 1 2 3 4 5 9 8 **6** **7**

You must replace the *ImExPS/2 Generic Explorer Mouse* with your mouse identifier (mine is like this for MS Intellimouse Optical plugged into the PS/2 port. When it's plugged to the USB port, it's like Microsoft Microsoft 5 button mouse with IntelliEye(TM) ... or something like that).

It seems that 6 and 7 are the side buttons of the mouse while positions 8 and 9 mark mapping of the the back/forward buttons.

Also, I found that to avoid the "BadValue" error, you must use the the full row of numbers... ie if you map 9 positions (you have to because the forward/back are positions 8 and 9), you have to use all the numbers from 1 to 9. That's why I used 8 and 9 in the command even though my mouse only has 7 buttons.

Right, now I have a command that works.
How do I make it work permanently, ie without having to type the command every time?
Yes! It definately works for me!
That's why i love Unix. There is always an answer :-p
Keep up the good work guys!
:-D

---

### Post by webbdawg on 2008-12-20
I have to say for something so basic as a mouse in the year of 2008 almost 2009 it sure seems that the Linux family of programmers would have this worked out so you don't have to go through these hacks.I thought the whole point of USB was so the devices could talk to the OS.

When will the Computer Industry start making smart systems both hardware and software.

---

### Post by PratterFak on 2009-12-13
> **webbdawg said:**
> I have to say for something so basic as a mouse in the year of 2008 almost 2009 it sure seems that the Linux family of programmers would have this worked out so you don't have to go through these hacks.I thought the whole point of USB was so the devices could talk to the OS.

When will the Computer Industry start making smart systems both hardware and software.

I agree!

I also have the Microsoft 5-Button Mouse with IntelliEye, but I like to use my right side button as [copy] and left side button as [paste] with my wheel click as [enter]. I'm not even sure if all the above will help me with that. Does the above enable you to configure the mouse with a GUI or do I need to do something else- command wise? Thanks.

---

