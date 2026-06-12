---
title: "touch pad recognised as ps/2 generic mouse on Dell N5030"
date: 2010-12-04
forum: Hardware
---

### Post by Flauwrens on 2010-12-04
Hello

I have just bought a new Dell Inspiron 5030 laptop. I immediately installed ubuntu 10.10 alongside my windows 7 and everything worked perfectly, except for the touch pad.
The touch pad is recognised as a ps/2 generic mouse, so I can't scroll,  disable clicking through tapping, etc.

```
flauwrens@lautop:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M               id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]

```I googled the problem and found a lot of bug reports on it and people having the same problem but I never found a solution.

Thanks in advance

---

### Post by Flauwrens on 2010-12-05
Bump

---

### Post by Flauwrens on 2010-12-07
Bump

---

### Post by Flauwrens on 2010-12-09
Bump

---

### Post by Flauwrens on 2010-12-10
Bump

---

### Post by Flauwrens on 2010-12-11
Bump

---

### Post by Flauwrens on 2010-12-12
Bump

---

### Post by Flauwrens on 2010-12-14
Bump

---

### Post by sf_basilix on 2010-12-15
My laptop has always recognized the touch pad (mouse pad) on my dell e6510 laptop as a ps/2, however only recently (in fact, since the latest patch update yesterday) my pad no longer works correctly. I was at least able to use it, albeit not the scrolling, but now when I touch the mouse pad, the mouse just jumps all over the screen.

Have no idea what's changed in the last patch update but it's now rendered my laptop virtually useless.

---

### Post by topgun98 on 2011-02-27
I'm having the same problem as Flauwrens.

Dell N5030, with the same xinput output, and touchpad scrolling doesn't work at all.

I found a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/678103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/678103)

Does anyone know of a workaround?

I'd be willing to pay someone if they can help me.

---

### Post by NikoC on 2011-03-21
Same problem on a new dell E6510 running Ubuntu 10.10 64-bit. I have been looking for over a week now, but so far, no solution...

---

### Post by NikoC on 2011-03-23
Apparently there has been some success when applying [this]("https://patchwork.kernel.org/patch/118834/") kernel patch... 

Since I'm no expert on the matter and don' really know how to patch, I think I'll wait until a definitive fix is released.

---

### Post by amorphinator on 2011-04-07
I have kind of a solution for this issue.

The problem is that Dell Inspiron N5030 has Alps Touchpad instead of Synaptics which they use in most laptops and the alps driver is not very good.

I have written a script in bash that gets the xinput id and disables or enables your touchpad depending in what status it is at the moment.

You can download the script from the following URL:

[http://www.emarketbg.com/scripts/touchpad.sh](http://www.emarketbg.com/scripts/touchpad.sh)

Steps to take to bind it to your touchpad button.

1. Copy the file in your /bin directory and give it 755 permissions.

2. Run from console the following command:

gnome-keybinding-properties

or open System/Preferences/Keyboard Shortcuts

3. Click the Add button on the window that has opened

4. On the small window that just opened write the following:

Name: Touchpad
Command: /bin/touchpad.sh

and click the Apply button.

5. Your custom shortcut will appear at the bottom of the list, right-click in the Shortcut column to bind a new key to that shortcut and press the touchpad key on your laptop's keyboard.

6. Close the Keyboard Shortcuts window and enjoy the script.

If you have any questions you can write me at [email]amorphis@emarketbg.com[/email]

Please note it is my first public script and it may not be the best solution for the touchpad problem but it is some solution.

Tested on Dell INSPIRON N5030 with Ubuntu 10.10

Enjoy

---

### Post by NikoC on 2011-04-12
Just installed Natty Narwhal today to give it try and touchpad is recognized with this new release! Vertical and horizonal scrolling work out of the box...

So just hold on a couple of more days and you an upgrade to 11.04!

---

### Post by raghukr on 2011-05-03
Dell N5030, Natty 11.04 is recognizing the touchpad, but touchpad tab is still missing in the mouse properties. Also changes made to touchpad in gconf does not have any effect.

---

### Post by aeronutt on 2011-05-03
> **raghukr said:**
> Dell N5030, Natty 11.04 is recognizing the touchpad, but touchpad tab is still missing in the mouse properties. Also changes made to touchpad in gconf does not have any effect.

+1, same state of affairs for me. Dell Vostro.

---

### Post by CapnCaffeine on 2011-05-10
Thanks for the script. Works great on my system to toggle the Touchpad. I modified one section that gives an onscreen notification of the Touchpad status:

.
.
.
#once we get the device status depending on the status we set it the other way arround
        if [ "$getstatus" == "1" ]; then
        newstatus="0"
	zenity --info --text="Touchpad OFF" --timeout 1
        else
        newstatus="1"
	zenity --info --text="Touchpad ON" --timeout 1
        fi
`xinput set-prop $devid "Device Enabled" $newstatus`
.
.
.
I chose zenity instead of notify-send to have a lockout of 1 second.

CapnCaffeine

---

### Post by jura12 on 2011-05-24
You can speed up your ALPS touchpad by this way. Type this code in yourfile.sh, make executable and add it to user autoload.
```

xinput list-props "ImPS/2 ALPS GlidePoint" | grep Velocity
xinput set-prop "ImPS/2 ALPS GlidePoint" "Device Accel Velocity Scaling" 100
xinput list-props "ImPS/2 ALPS GlidePoint" | grep Velocity

```This was tested on ubuntu 11.04 dell inspiron n5030
I am sorry for my english.

---

### Post by tturrisi on 2011-07-14
Anybody have a solution yet to get scrolling working? (don't want to change kernels)

---

### Post by putt1ck on 2011-08-15
Kubuntu 11.04 enabling the script for toggling the mouse, having download, copied and reset permissions as per instructions:

In System Settings go to Shortcuts and Gestures.

Select Custom Shortcuts then use the button (showing as Edit with a dropdown icon) at the bottom to select New > Global Shortcut > Command/URL. 

Rename as suits, then use the Trigger tab to select the key (I used F6 because I don't use it for anything else and I wanted a single key for speed, choose a key or combination that suits you).

In the Action tab enter the command /bin/touchpad.sh

This allows amorphinator's excellent (thanks :) ) script to toggle the touchpad off/on in KDE - note if you have opted for the combined touchpad and stick setup on your laptop the script toggles the whole mouse system off/on, reflecting the issue with Alps' lack of cooperation in not providing the specs of the hardware.

This was for a Dell E5420, will probably work for all E-series as well as others with the same Alps hardware.

---

### Post by MarjaE on 2011-08-17
I have a hotkey to turn the touchpad off. But for some reason the computer keeps turning the touchpad back on after a while, which kinda defeats the purpose...

---

