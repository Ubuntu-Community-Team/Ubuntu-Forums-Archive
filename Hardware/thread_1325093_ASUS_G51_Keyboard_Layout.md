---
title: "ASUS G51 Keyboard Layout"
date: 2009-11-13
forum: Hardware
---

### Post by lreal on 2009-11-13
Hello,

Some people have already related this problem when Karmic was still under test. I am with up-to-date Karmic here and still have this problem:

[http://ubuntuforums.org/showthread.php?t=1294323](http://ubuntuforums.org/showthread.php?t=1294323)

The backslash/pipe key prints less/greater signals. I still can type pipe using RightAlt plus this key, but I have no backslash, so this is quite annoying.

Has anyone reported this bug or have a solution for this?

Thanks in advance

---

### Post by mihaid on 2009-11-24
i found the solution on another site: 

```
xmodmap -e "keycode 94 = backslash bar"
```

cheers :)

---

### Post by s3MA00RRNY on 2009-12-08
How do you get it to work in the console? I don't use the console that much, but it's annoying.

---

### Post by andon21 on 2009-12-10
Thanks so much, it was really annoying to not be able to pipe.

---

### Post by s3MA00RRNY on 2009-12-12
I found a way to get it to work in the console, but I can't get it to stick. Modify the file /usr/share/keymaps/i386/qwerty/<country>.kmap.gz. Replace '86 = greater lesser bar' (or whatever it is) with '86 = backslash bar', then run 'sudo kbd-config' and select the new keymap. It will fix it, but you have to run the command every time.

---

### Post by dummyaja on 2009-12-28
> **mihaid said:**
> i found the solution on another site: 

```
xmodmap -e "keycode 94 = backslash bar"
```cheers :)

by using this code, i'm able to fix my g51 keyboard error.
to make it always run this command, u can place the command in the startup.

here are the step.
1. create execute able file. (place it where aver u want it and dont forget to chmod +x)
```

touch fix_keyboard.sh
chmod +x fix_keyboard.sh

```2. insert command xmodmap into the file
```

nano fix_keyboard.sh
> type in = xmodmap -e "keycode 94 = backslash bar"
save the file

```3. open System ->Preferences -> Statup Applications
    in the Startup Programs Tab, click Add button.
    fill up all the input, 
    search the file we create before (in this case fix_keyboard.sh).
    press Add button.

Done.
try to restart and test your keyboard :popcorn:

---

### Post by lreal on 2010-02-09
Thanks a lot for the help! It is working here.

---

### Post by Sinlak on 2010-10-25
Thank you so much for this, I was losing my mind trying to solve this problem, I am learning cpp so I need thos keys! and im new to ubuntu so I needed the help. Thanks again!

---

