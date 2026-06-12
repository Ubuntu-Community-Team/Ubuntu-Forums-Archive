---
title: "[SOLVED] keyboard preferences, &amp;quot;Apply system wide&amp;quot; doesn't work"
date: 2008-12-18
forum: Hardware
---

### Post by hatten on 2008-12-18
I have recently changed keyboard from qwerty to dvorak and added it in the keyboard preferences. But i cannot make it system wide, there happens nothing when i click "apply system wide" after I have marked the keyboard forcing me to use qwerty in the login screen. Do i have to "sudo" it in terminal or? If that would be the case, what command should i use to open up the keyboard preferences?

---

### Post by hatten on 2008-12-19
bump


in the beginner section everything is fixed in an hour, here in the main support categories i have to bump my threads several times until i get a reply!

---

### Post by hatten on 2008-12-21
> **hatten said:**
> bump


in the beginner section everything is fixed in an hour, here in the main support categories i have to bump my threads several times until i get a reply!bump!

---

### Post by hatten on 2008-12-22
> **hatten said:**
> bump


in the beginner section everything is fixed in an hour, here in the main support categories i have to bump my threads several times until i get a reply!

bump bump bump!!!

---

### Post by rajan on 2008-12-22
so what exactly is the problem? 

are you stuck at the login screen trying to modify the keyboard setup? or did you modify the keyboard configuration once and then the next time you log in, the change has not been saved? 

a quick description of your system would also go a long way toward fixing your setup.

have you tried the setxkbmap command? my computer did not like to take the keyboard that i set it up with so i included a command to run upon gnome's bootup. that command for me is 

```

 setxkbmap -model toshiba_s3000 -layout us

```

in order to run a startup command, go to "System>Preferences>Sessions>Startup Programs" and add whatever command you like


EDIT: note that i'm using 6.06, which is likely different from your setup

---

### Post by hatten on 2008-12-22
the problem is (was) that nothing happened when i clicked the "apply system-wide" button. The keyboard works perfect in all other ways.

By some mysterious reason it worked after i had ticked the "separate layout for each window" and it have worked since that. (asking me to unlock)

---

### Post by rajan on 2008-12-22
glad to see it worked out

---

