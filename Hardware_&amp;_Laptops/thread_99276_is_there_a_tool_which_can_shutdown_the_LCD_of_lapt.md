---
title: "is there a tool which can shutdown the LCD of laptop?"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by meishiwanwan on 2005-12-05
i sometime wanna shutdown the LCD,just listening to the audio.is there anybody can 
tell me a tool which can resolve it?:rolleyes:

---

### Post by m0biu5 on 2005-12-05
I suppose that depends on what type of laptop you have. When I want to just listen to music I shut my lid. You can also check for a function button to turn it off.

---

### Post by er-ku on 2005-12-05
Well, on my iBook, I can just dim the light until it turns off. No additional software is needed.

On an Acer, however, dimming the light to zero resulted in computer turning off, if I remember correctly...

That depends on a model of your laptop most probably.

---

### Post by 23meg on 2005-12-05
Try this command ```
xset dpms off 
```

---

### Post by meishiwanwan on 2005-12-05
Unfortunately,my laptop of BENQ don't support the way you said.in windows i used to shutdown it  by the power-manager after one minute without doing anything.is there a tool like the power-manager which is in windows?

---

### Post by greenway on 2005-12-05
On my thinkpad (as well as on Toshiba/Futjitsu if I remember correctly) there's a key combo which you can use to switch between your laptop's screen and display port for using external monitors, so using this key without a external monitor equals turning of your screen all together. Guess it depends on your laptop brand and model...

---

### Post by meishiwanwan on 2005-12-05
[QUOTE=23meg]Try this command ```
xset dpms off 
```[/QUOTE]
thank you ,i tried the command.but the result is ```
yaoming@ubuntu:~$ xset dpms off
xset:  unknown option off

usage:  xset [-display host:dpy] option ...
    To turn bell off:
        -b                b off               b 0
    To set bell volume, pitch and duration:
         b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
        -bc
    To enable bug compatibility mode:
        bc
    To turn keyclick off:
        -c                c off               c 0
    To set keyclick volume:
         c [0-100]        c on
    To control Energy Star (DPMS) features:
        -dpms      Energy Star features off
        +dpms      Energy Star features on
         dpms [standby [suspend [off]]]
              force standby
              force suspend
              force off
              force on
              (also implicitly enables DPMS features)
              a timeout value of zero disables the mode
    To set the font path:
         fp= path[,path...]
    To restore the default font path:
         fp default
    To have the server reread font databases:
         fp rehash
    To remove elements from font path:
        -fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
        +fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
        -led [1-32]         led off
         led [1-32]         led on
    To set mouse acceleration and threshold:
         m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
         p pixel_value color_name
    To turn auto-repeat off or on:
        -r [keycode]        r off
         r [keycode]        r on
         r rate [delay [rate]]
    For screen-saver control:
         s [timeout [cycle]]  s default    s on
         s blank              s noblank    s off
         s expose             s noexpose
         s activate           s reset
    For status information:  q

```

---

### Post by meishiwanwan on 2005-12-05
[QUOTE=greenway]On my thinkpad (as well as on Toshiba/Futjitsu if I remember correctly) there's a key combo which you can use to switch between your laptop's screen and display port for using external monitors, so using this key without a external monitor equals turning of your screen all together. Guess it depends on your laptop brand and model...[/QUOTE]
You're right. On the thinkpad there is a key to switch between your laptop's screen and display port,and my laptop too.but the key of my laptop is still invalidity of key ,and i don't know what's wrong with it.Maybe it's fake.:???:

---

### Post by er-ku on 2005-12-05
[QUOTE=meishiwanwan]You're right. On the thinkpad there is a key to switch between your laptop's screen and display port,and my laptop too.but the key of my laptop is still invalidity of key ,and i don't know what's wrong with it.Maybe it's fake.:???:[/QUOTE]


Nah, It's just there are laptops smart enough not to switch outputs when there's no monitor attached.

However, here's a  command:
```

xset dpms force off

```
should work. ;) cheers!

---

### Post by meishiwanwan on 2005-12-05
[QUOTE=er-ku]Nah, It's just there are laptops smart enough not to switch outputs when there's no monitor attached.

However, here's a  command:
```

xset dpms force off

```
should work. ;) cheers![/QUOTE]
thank you ,the command is valid.i forgot add 'force' in a command.:smile: 
and thanks all guys.

---

### Post by thecrust on 2006-01-15
xset dpms force off turns my screen blank, but the lcd backlight stays on.

Any suggestions?

[ hp omnibook XE3 PIII850 ]

---

### Post by thecrust on 2006-02-11
I had to install the omnibook module (sourceforge).  From there it gave me /proc/omnibook/lcd as an interface to control the backlight.

---

