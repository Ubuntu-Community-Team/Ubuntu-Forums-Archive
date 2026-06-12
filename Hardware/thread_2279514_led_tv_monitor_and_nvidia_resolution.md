---
title: "led tv monitor and nvidia resolution"
date: 2015-05-23
forum: Hardware
---

### Post by howiebinnz on 2015-05-23
hi all, have posted question below in kubuntu forums a few weeks ago but not had any response as yet, can anyone help here?
lspci gives the following for the video card - ```
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)
```
it's a sony monitor 26bx320.


thnx
howard

hi everyone, i am using kubuntu 14.10 and have just decided to upgrade  from an onboard video card to an nvidia graphics card. i have a led tv  connected to computer (not hd) and decided to try loading nvidia driver  on a spare partition using kubuntu. while using the nouvea driver all is  ok, but when I load nvidia driver the text is so tiny it's impossible  to read. can anyone help with setting up the correct refresh/resolution  settings?
thnx in advance.
howard

---

### Post by Vladlenin5000 on 2015-05-23
As a general rule, the correct resolution is the maximum resolution allowed for the output device. As such, it's probably correct now (proper resolution) and incorrect before (lower), ie, exactly the opposite of your perception.
That's the whole point of higher resolutions: smaller pixels. ;)

You can adjust the **Text Scalling**. Read [here]("http://askubuntu.com/questions/314494/ubuntu-appears-very-small-at-1080p-text-almost-undreadable") two suggestions. Follow the answer #2 (not the one accept by the user) for immediate results. If not enough then follow the accepted answer for a finer control.

---

### Post by SeijiSensei on 2015-05-23
In the past I had a problem with NVIDIA cards where the onscreen text was microscopic.  The solution was to edit /etc/X11/xorg.conf to add a "DPI" option like this:
```

Section "Monitor"
    ...
    Option    "DPI"  "100 x 100"
    ...
EndSection

```
Nowadays xorg.conf is deprecated, so I don't know if this still works.  You can give it a shot though like this.

First, reboot and choose the "recovery mode" option from the grub menu.  You'll eventually be offered a menu of choices; pick "root shell" from the list.

Now run the following:
```

mount -o remount,rw /
nvidia-xconfig

```
See if that creates an xorg.conf file in /etc/X11.  If so, add the Options line above to the Monitor section, then reboot.  Any better?

---

### Post by howiebinnz on 2015-05-25
well, sort of solved. i think the post from SeijiSensei pointed me in the right direction. ended up changing the font dpi as suggested (but through system settings - there was no nvidia configuration as SeijiSensei thought). all working well now. thnx for the help.
howard

---

