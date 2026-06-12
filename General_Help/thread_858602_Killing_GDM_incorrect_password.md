---
title: "Killing GDM incorrect password"
date: 2008-07-13
forum: General Help
---

### Post by dethredic on 2008-07-13
So, I needed to kill gdm and run some commands from there. I did sudo /etc/init.d/gdm stop. That brought me to a terminal login screen, but when I typed in my username and password it kept saying it was incorrect. I only use one password, caps is off. I typed it in like I normally do in the GUI login screen.

EDIT: Now I can't even get to the login part. It always freezes after the "checking boot scripts". (I forget exactly what it is called, could be slightly different)

---

### Post by fsmithred on 2008-07-15
I'm gonna take a guess and say that it's possibly something you did before you did the 'sudo /etc/init.d/gdm stop'. Killing gdm shouldn't do anything to mess up your login or password.

---

### Post by Archmage on 2008-07-15
No need to kill GDM. Normaly it is like this:

CTRL+ALT+F1 = Terminal
CTRL+ALT+F2 = Terminal
CTRL+ALT+F3 = Terminal
CTRL+ALT+F4 = Terminal
CTRL+ALT+F5 = Terminal
CTRL+ALT+F6 = Terminal
CTRL+ALT+F7 = Graphical Loginscreen
CTRL+ALT+F8 = Status screen

Maybe you are using a different keyboard-layout in the terminal. If you have keys like z in your password try to make them work with the wrong keys like "y"

If you can't boot, you still can try the recovery option and undo what you have done to stop GDM.

---

