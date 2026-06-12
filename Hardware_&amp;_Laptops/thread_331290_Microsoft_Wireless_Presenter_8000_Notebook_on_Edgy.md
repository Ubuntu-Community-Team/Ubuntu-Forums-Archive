---
title: "Microsoft Wireless Presenter 8000 Notebook on Edgy"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by widemos on 2007-01-04
Hi, I've managed to make this mouse run in Edgy quite easily, it's a bluetooth mouse, but when I switch to "presentation" mode, only volume up and down keys are recognized, not the others.

How can I extract the codes mouse sends to the laptop and how can I make Ubuntu understand them?

Thanks.

---

### Post by moriarty44 on 2007-09-25
Hi!

I've Ubuntu 7.04 on my laptop and I've just bought a Presenter 8000. Everything works great but the presentation mode. If you've found a solution to this problem I'll appreciate your help, please.

Thank you :)

---

### Post by widemos on 2007-09-26
I'm still stuck with the same issue, the mouse works very well in gutsy (also did in feisty) but without presentation features. Sorry.

---

### Post by delbene on 2007-09-27
I have the same problem.
Using xev I noticed that when the mouse is in presentation mode only the volume buttons generate some events. The other ones are mute.

---

### Post by widemos on 2007-09-27
Yep, I think it's a problem of the underlying bluetooth subsystem, but I'm not sure.

We should better find another mouse.

---

### Post by delbene on 2007-09-27
But this one was a gift! ;)

---

### Post by tonyric on 2007-11-12
I got my presenter 8000 working with the following button maps on Gutsy:

Tilt Left (Browser/KDE Back)
Tilt Right (Browser/KDE Forward)
Thumb Left (Left keyboard button)
Thumb Right (Right keyboard button)
 

    sudo apt-get install xbindkeys xvkbd xmacro

I added the following to ~/.xbindkeysrc

     
    "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
      b:7
    "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
      b:6
    "/usr/X11R6/bin/xvkbd -xsendevent -text "\\[Right]""
      b:10
    "/usr/X11R6/bin/xvkbd -xsendevent -text "\\[Left]""
      b:9

Then I set xbindkeys to start on KDE login by creating a link to is in ~/.kde/Autostart 

I also created another mouse config in /etc/X11/xorg.conf

      Section "InputDevice"
      Identifier "Microsoft 8000"
      Driver "evdev"
      Option "Device" "/dev/input/event7"
      Option     "Buttons"         "9"
      Option     "ZAxisMapping"    "4 5 6 7"
      Option     "Emulate3Buttons" "false"
      Option       "WHEELRelativeAxisButtons" "4 5"
      Option       "DIALRelativeAxisButtons" "6 7"
      Option "SendCoreEvents" "true"
    EndSection

Then I added the following line to the Serverlayout section of xorg.conf

     Inputdevice     "Microsoft 8000" "SendCoreEvents"

---

### Post by rootneg on 2008-07-11
I just purchased one of these mice (it was a steal too! only $25 for the store demo one, no box)

I've got the buttons working properly, but I keep having issues with making and keeping a connection.

Unless I push the recessed button on the bottom; it's invisible to my computer. After a long period of inactivity, it will loose association and I will have to push the button and manually reconnect. Very inconvenient.

Any clues?

---

### Post by yannmonclair on 2008-07-16
I just receive my Microsoft Wireless Presenter 8000 today. I tried tonyric's modifications, but it made the mouse stop working properly. The mouse would only go up or down (no left or right), and the next/previous were mapped on the mouse clicks.

rootneg, did you get the whole mouse supported ? Or even just a limited functionality ? Would you mind sharing more details on your setup. I'm speaking at a conference in late august, and I would love to be able to use this mouse with my eeePC, running ubuntu.

Cheers,

Yann

---

