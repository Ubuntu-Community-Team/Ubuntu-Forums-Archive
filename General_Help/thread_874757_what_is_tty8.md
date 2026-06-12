---
title: "what is tty8 ?"
date: 2008-07-30
forum: General Help
---

### Post by dexter.deepak on 2008-07-30
i just wanted to know this out of curiosity..what do we get on presssing Ctrl+Alt+F8 ? is seems to be on a standstill ...no prompt or anything...

---

### Post by iaculallad on 2008-07-30
Try the command below if it could allow you to access it:

```
sudo chmod 640 /dev/tty8
sudo chown $USER.root /dev/tty8
```

---

### Post by ibutho on 2008-07-30
> **dexter.deepak said:**
> i just wanted to know this out of curiosity..what do we get on presssing Ctrl+Alt+F8 ? is seems to be on a standstill ...no prompt or anything...

The reason why its blank is because most distros only enable 7 virtual terminals by default, so tty1 to tty6 will give you a CLI login prompt and tty7 is where X is run from. You can enable more virtual terminals by editing /etc/inittab or in the case of Ubuntu create the relevant tty files in /etc/event.d.

---

### Post by Growbag on 2008-07-30
It's the one between tty7 and tty9!

lol

But seriously......

You can actually open a new x-session, ie log in as another user and switch between 2 (or more) complete desktop sessions by pressing the ctrl-alt-f7 and f8 keys.

It's great for openGL games so that you can run a chat prog on one "desktop", and switch between them easily.

Well, you can with openSUSE, I guess you can also under Ubuntu, it should have a "switch users" function somewhere around the logout button.

---

### Post by dexter.deepak on 2008-07-30
i think i should reformulate my query ..
what "program" is running at tty8 ? it it neither need a user interaction, nor does it seems to do by itself !!

@iaculallad
i couldnt understand what you are trying to say..i am actually afraid of running the code without understanding it...wont it disturb any of my system's functionality ?

---

### Post by geirha on 2008-07-30
Some process during the bootup has redirected some text to /dev/tty8 . Not sure what the purpose is, on my machine there's about the last half of the messages from init, so it's not very useful.

Try ```
echo Hello >/dev/tty8
``` and switch to ctrl+alt+f8 to see your message. 

If you run something like ```
tail -f /var/log/syslog >/dev/tty10
``` then Ctrl+alt+f10 should be showing you the loglines as they are added. Not very useful in these days with GUIs.

---

### Post by ibutho on 2008-07-31
> **dexter.deepak said:**
> i think i should reformulate my query ..
what "program" is running at tty8 ? it it neither need a user interaction, nor does it seems to do by itself !!

@iaculallad
i couldnt understand what you are trying to say..i am actually afraid of running the code without understanding it...wont it disturb any of my system's functionality ?

Like I said above, on most distros tty8 and above are not configured to do anything, so they are just blank and you can't input anything. You can however configure them to do something, using the methods I described above. Also extra X sessions can be started and will run from tty8 and above if those ttys have not been configured for anything.

---

