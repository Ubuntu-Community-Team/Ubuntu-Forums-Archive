---
title: "[SOLVED] xfce4-terminal copy-paste problem"
date: 2008-11-18
forum: General Help
---

### Post by virx on 2008-11-18
Does on Xubuntu 8.10 copy text from program and paste to xfce4-terminal not with mouse right click but with shortcut keys ctrl+shift+V work for you? 

For me with shortcut keys cursor only blinks but no paste. With mouse right click it works fine.

---

### Post by Thanoulis on 2008-11-18
Did you try with Ctrl-v or Shift-Insert instead?

---

### Post by OutOfReach on 2008-11-18
...Because the xfce4-terminal doesn't have a shortcut to copy/paste. You can only do it from right-clicking.

---

### Post by sisco311 on 2008-11-18
> **virx said:**
> Does on Xubuntu 8.10 copy text from program and paste to xfce4-terminal not with mouse right click but with shortcut keys ctrl+shift+V work for you? 

For me with shortcut keys cursor only blinks but no paste. With mouse right click it works fine.

works for me.

check the shortcuts: xfce4-terminal --> Edit --> Preferences --> Shortcuts
(Ctrl+Shift+c = copy;  Ctrl+Shift+v = paste)

---

### Post by Quarg on 2008-11-18
you can't paste into a terminal using shortcut keys, thats just the way it is.

---

### Post by ratmandall on 2008-11-18
Shift insert works for me.

---

### Post by sisco311 on 2008-11-18
> **OutOfReach said:**
> ...Because the xfce4-terminal doesn't have a shortcut to copy/paste. You can only do it from right-clicking.

> **Quarg said:**
> you can't paste into a terminal using shortcut keys, thats just the way it is.

the default shortcuts are Ctrl+Shift+c (copy) and Ctrl+Shift+v (paste)

---

### Post by virx on 2008-11-18
Thank you for answering - Shift + Insert works indeed, but my problem must be keyboard related, if I reprogram shortcut keys for Shift+c/v or Ctrl+c/v it works but not with default Ctrl+Shift+c/v.

I leave it for Ctrl+c/v like firefox has.

---

### Post by prshah on 2008-11-18
> **virx said:**
> 
I leave it for Ctrl+c/v like firefox has.

Ouch! Ctrl+C is already mapped to "break" / cancel for the terminal, which is why it is suggested to use Ctrl+Shift+C.

Ctrl+V is mapped to... something that slips my memory right now. 

Other standard mappings:

Ctrl+Z ; suspend current job
Ctrl+D ; Accept and close (Ctrl+Z in DOS)

---

### Post by virx on 2008-11-18
Ouch, right ... just noticed it :D.

Any ides how to find out why 3 key combinationd does not work?

---

### Post by sisco311 on 2008-11-18
> **virx said:**
> Thank you for answering - Shift + Insert works indeed, but my problem must be keyboard related, if I reprogram shortcut keys for Shift+c/v or Ctrl+c/v it works but not with default Ctrl+Shift+c/v.

I leave it for Ctrl+c/v like firefox has.

try to edit the terminalrc file:
```
nano ~/.config/Terminal/terminalrc
```
and change the shortcuts manually:
> [Configuration]
...
*AccelCopy=**<Control><Shift>c***
*AccelPaste=**<Shift><Control>v***
...save the file and exit(Ctrl+o, Enter, Ctrl+x).

restart the terminal. 

when you edit the shortcuts in the preferences the shortcut for copy is saved as <Shift><Control>c not <Control><Shift>c

it's a bug?

---

### Post by virx on 2008-11-18
> **sisco311 said:**
> try to edit the terminalrc file:
```
nano ~/.config/Terminal/terminalrc
```
and change the shortcuts manually:
save the file and exit(Ctrl+o, Enter, Ctrl+x).

restart the terminal. 

when you edit the shortcuts in the preferences the shortcut for copy is saved as <Shift><Control>c not <Control><Shift>c

I changed lines to
AccelCopy=<Control><Shift>c
AccelPaste=<Control><Shift>v
restarted terminal - no help.

EDIT:

After logging out and in it works now as expected. Thanks.

---

