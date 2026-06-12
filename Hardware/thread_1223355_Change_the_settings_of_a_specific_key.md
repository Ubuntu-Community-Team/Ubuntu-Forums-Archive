---
title: "Change the settings of a specific key?"
date: 2009-07-26
forum: Hardware
---

### Post by OrnithO on 2009-07-26
Hello,
I have a problem with my Acer Aspire Timeline 4810T, there is a small button to lock the touchpad and if I use it it will lock the touchpad but then I can't unlock it, I have to run the following line in a terminal to make it work again.
```
sudo modprobe -r psmouse && sudo modprobe psmouse
```I'm not an expert but I think it unmounts (is it the correct term ?) the touchpad module.:confused:
I tried to find a solution and managed to add a new key shortcut that runs this script:
```
#!/bin/bash
  str=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')
      if [ "$str" = '0' ]; then
          synclient TouchpadOff=1 &&exec 3> >(zenity --notification --listen --window-icon="/usr/share/pixmaps/touchpad.png") && echo "message:Touchpad Off" >&3
      elif [ "$str" = '2' ]; then
          synclient TouchpadOff=0 &&exec 3> >(zenity --notification --listen --window-icon="/usr/share/pixmaps/touchpad.png") && echo "message:Touchpad On" >&3
      elif [ "$str" = '1' ]; then
          synclient TouchpadOff=0 &&exec 3> >(zenity --notification --listen --window-icon="/usr/share/pixmaps/touchpad.png") && echo "message:Touchpad On" >&3
      else
          zenity --info --title="Toggle TouchPad" --text="Couldn't get touchpad status from synclient\nLaunch \"synclient -l\" in terminal to check the error" && exit 1
  fi
  exit 0
```It seems to work with the touchpad lock key as the notification displays correctly but I still cannot unlock the touchpad after... I think that the button still unmount the touchpad module (as I have to mount it again with modprobe) and at the same time execute the script...

So does somebody know how to change the settings of specific key ?

Thanks
Hope you'll understand me, english is not my first language :)

Ps using xev, when I pree the key, I have this:
```
FocusOut event, serial 32, synthetic NO, window 0x6800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x6800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```

---

### Post by 80aless on 2009-10-22
maybe try to remap the key combination. use xev in the terminal to get the keycode, then make your own mapping by modifying the ~/.xmodmap.myown file
```
xmodmap -pke >  ~/.xmodmap.myown
```
make an entry for the xmodmap in autostart (gedit ~/.bashrc)
xmodmap ~/.xmodmap.myown


OR MAYBE associate to that shortcut a combination of you two scripts: 
```
#!/bin/bash
if test -e ~/lock; then
  rm ~/lock
CODE TO UNLOCK
else
  touch ~/lock
CODE TO LOCK
fi
```

---

### Post by OrnithO on 2009-10-23
Thanks, but I heard that the problem is solved in Unbuntu 9.10. So I think I'll wait 5 more days and see how it works. If the problem is still there I'll use what you said.
Thanks again for the answer.

---

### Post by OrnithO on 2009-11-13
So, just a little feedback. It still doesn't work out of the box with 9.10. I found a solution, just add i8042.nomux on your kernel boot options. I explained everything on the [wiki page about  Acer Timline laptops]("https://help.ubuntu.com/community/AspireTimeline/Fixes")

---

### Post by morfeus_cor on 2010-02-18
my solution on acer timeline 4810T
I create in keyboard shorcuts a new key F7 
it run a script with sticky bit key to be as root 

```
#!/bin/bash
# Run as root, of course.
tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
sudo modprobe -r psmouse && sudo modprobe psmouse
```

no password asked no more trouble just one more key 
thanks OrnithO for solution !

---

