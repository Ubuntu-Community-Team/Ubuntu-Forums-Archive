---
title: "disable touchpad on the fly"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by gushy on 2005-06-23
Anyone know if there is a way to turn a touchpad off on the fly? Either by clicking a key  combo or preferably when a mouse is plugged in.

My old laptop had an off button for the touchpad but my Evo N800v doesn't. :(

---

### Post by ywwg on 2005-06-23
I created a little script called touchpad_toggle.sh:
```
#!/bin/sh

current_touchpad=`synclient -l |grep TouchpadOff | sed 's/  */ /g' | cut -d' ' -f 4`
if [ $current_touchpad = 0 ] ; then
        new_touchpad=1
else
        new_touchpad=0
fi

synclient TouchpadOff="$new_touchpad"
```

And then created a shortcut from ctrl-alt-T to that script, using run_command entries for metacity in gconf-editor.  It works quite well.

---

### Post by gushy on 2005-06-28
looks nice, i'll give it a try today, thanks.

:)

---

### Post by drewex on 2005-08-16
Hi,
I couldnt do it
how does this file work sh extension i never used it? can anyone help?

Addition is this for some mac machine or somethin. i have a dell 6000 with windows xp pro 6000 any ideas

---

### Post by wellery on 2005-08-16
[QUOTE=drewex]Hi,
I couldnt do it
how does this file work sh extension i never used it? can anyone help?

Addition is this for some mac machine or somethin. i have a dell 6000 with windows xp pro 6000 any ideas[/QUOTE]

You can type 

```
chmod 755 <filename> 
``` 

which will make it executable. then you can type 
```
./<filename> 
``` 

to execute it

---

### Post by Biloume on 2005-08-16
Hey, i just got ubuntu and i'm having some trouble withthe touchpad...i  can tap for certain things and i can't for others...it's driving me crazy, i'm so used to tapping so i'll tap on the touchpad and somethin will be copied or i'll close a window or some such thing. I tried to adjust the settings but for some reason it's not working...can anyone help me?

---

### Post by gushy on 2005-10-14
I totally forgot about this thread, thank for the script ywwg!

I'm getting an error when running it though:```
Can't access shared memory area. SHMConfig disabled?
/usr/local/bin/touchpad_toggle.sh: line 4: [: =: unary operator expected
Can't access shared memory area. SHMConfig disabled?

```

---

