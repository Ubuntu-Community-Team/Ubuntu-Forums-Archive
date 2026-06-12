---
title: "[SOLVED] Reprogram buttons?"
date: 2008-11-07
forum: General Help
---

### Post by gkrules on 2008-11-07
I have a laptop with a broken "1" on its keyboard.[The entire key is ripped out]
I have Ubuntu 8.10 on it.
How can I reprogram an unused button to put in a "1"?
I am hoping to change the F1 button, but any others will work too.

Is there a program that I can use to change it, or is it built in on ubuntu?

---

### Post by drs305 on 2008-11-07
I have seen some reports that xmodmap acts differently in intrepid, but I just tried it and didn't seem to have a problem. I ran the following to change the F1 key into a 1:
```

xmodmap -e "keycode 67 = 1"

```

There are probably system key reassignments - this is just the old school way of doing it. For more on xmodmap: man xmodmap

You can put that into your System, Preferences, Sessions, StartUp as a command so it is available at boot.

You can use an app called ''xev' to see key assignments.


**Added**: If your '1' key doesn't work at all and you need the uppercase Exclamation as well ( ! ) change the code to:
```

xmodmap -e "keycode 67 = 1 exclam"

```

---

### Post by gkrules on 2008-11-07
Yes!
Thank you!
It works amazingly now.

---

### Post by gkrules on 2008-11-08
Hmm, when I restart, I have to run the script again for it to work.
How can I make it automatically run the script at bootup?

---

### Post by Xgen on 2008-11-08
'Twas explained  at top post :)

> You can put that into your System, Preferences, Sessions, StartUp as a command so it is available at boot.

System-->Preferences-->Sessions-->Add. Name it whatever and add the command. It will automatically run with the booting process.

---

