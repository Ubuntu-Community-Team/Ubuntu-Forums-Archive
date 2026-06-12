---
title: "HP 6830s Audio Problems"
date: 2008-12-31
forum: Hardware
---

### Post by lukariellen on 2008-12-31
I've just removed Vista and installed Ubuntu.....but after installation no sound at all from my laptop.....i've checked old posts but still i can not hear any sound from my front speakers. Any help?:confused:](*,)

---

### Post by tornadof3 on 2008-12-31
I have a HP 6735s which also had problems with sound when I first installed. This was solved by adding the line

```
options snd-hda-intel model=laptop
```

to the bottom of the file /etc/modprobe.d/alsa-base (create it if it does not exist) and then rebooting. Might work for you?

---

### Post by lukariellen on 2008-12-31
No action..... i've tried with:
luca@luca-laptop:~$ options snd-hda-intel model=laptop
bash: options: command not found
luca@luca-laptop:~$ options snd-hda-intel model=laptop hp 6830s
bash: options: command not found...
other suggests??:confused::confused::confused::confused::confused::confused:

---

### Post by tornadof3 on 2008-12-31
OK, you need to actually edit a file, so, from a command line, type:
```

sudo gedit /etc/modprobe.d/alsa-base
```

this should ask for your password, then open up an editor window with a file called "alsa-base" open. It may be blank, or it may have some text in. At the very bottom, add a new line and put

```
options snd-hda-intel model=laptop

```
there. Save this file, and then close & reboot. See if that helps?

---

### Post by lukariellen on 2008-12-31
......:confused:...now i can hear at 100% volume only noise....at lower volumes distorced music.......any suggest to solve it? happy new year!!!:popcorn:

---

### Post by lukariellen on 2009-01-02
[SIZE=1][SIZE=1][SIZE=1] This is the situation once running alsamixer...

Card: HDA Intel                                                              &#9474;
&#9474; Chip: Analog Devices AD1984A                                                 &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Front                                                                  &#9474;

      &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;                  &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;                    &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;   &#9484;&#9472;&#9472;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;    &#9474;OO&#9474;   &#9474;OO&#9474; &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                     &#9474;OO&#9474;              &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;   &#9492;&#9472;&#9472;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                   &#9492;&#9472;&#9472;&#9496;              &#9474;
&#9474;  100<>100          100<>100          100<>100  100<>100 100<>100 100<>100   &#9474;
&#9474;   Master  Headphon    PCM   < Front  >Front Mi  Front Mi   Line   Line Boo   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
were headphone-front are 00 but i can not increase both of them....audio is only working with usb speakers..any suggetsions????:confused:](*,):confused::confused:

[/SIZE][/SIZE][/SIZE]

---

### Post by linux_tech on 2009-01-02
Try installing and running Gnome-alsamixer 
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```
first check all settings, make sure nothing is muted
then try adjusting settings

---

### Post by lukariellen on 2009-01-02
Everything is ON but.........:
** (gnome-alsamixer:7273): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:7273): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:7273): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:7273): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:7273): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:7273): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:7273): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Input Source"!

any IDEA?:confused:

---

### Post by SanctusDiavolus on 2009-06-29
hi i am new here 


can anyone tell me how to fix the same problem....?????

i have followed the same suggestions and i got the same results......

so any other idea????

---

