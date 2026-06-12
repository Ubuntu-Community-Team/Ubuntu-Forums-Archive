---
title: "Keypad vs shift key"
date: 2008-07-28
forum: General Help
---

### Post by ben_ezzell on 2008-07-28
Normally I have the keypad set to NumLock off and I use the keypad as arrow and function keys (I'm an old timer and predate separate arrow keys ... and habit die very hard).  In Ubuntu, instead of a Shift/Arrow Key (on the keypad) allowing me to select (highlight), pressing shift puts the keypad back into Number mode ... which I don't want ... ever.  Does anyone know a way to remap the keypad? Or some other workaround?

Thanks,

Ben

---

### Post by mvaldez on 2008-09-06
Ben:

> Normally I have the keypad set to NumLock off and I use the keypad as arrow and function keys (I'm an old timer and predate separate arrow keys ... and habit die very hard). In Ubuntu, instead of a Shift/Arrow Key (on the keypad) allowing me to select (highlight), pressing shift puts the keypad back into Number mode ... which I don't want ... ever. Does anyone know a way to remap the keypad? Or some other workaround?

I am also used to old keyboards which used the numeric keypad as cursor browser. I only use the inverted-T arrow keys when playing games, never while editing text, reading email or browsing the web. I really hate the default Shift + Keypad = numbers; ugh. (The logic of this default would be that, just like CapsLock, NumLock is just a constant Shift.)

Anyway, the solution is simple, go to the **System** menu (or alike, as my Ubuntu is in Spanish), select **Preferences**, select **Keyboard**, select **Layout**, select **Layout options**, select **Compatibility options**, check the option **Shift with numeric keypad keys work as in MS Windows**. 

I think that option should read "as in DOS", but anyway.

Hope this helps.  :)


Regards,

Mario A. Valdez-Ramirez.

---

### Post by davidsarah on 2011-03-21
The location of this option in Gnome has changed a bit, so here's an updated description of how to set it for anyone googling this.

Go to System | Preferences | Keyboard, click the Layouts tab, click Options..., expand 'Miscellaneous compatibility options', and check both "Shift does not cancel NumLock, chooses 3rd level instead" and "Shift with numeric keypad keys works as in MS Windows". Click Close. You'll probably want to apply this change system-wide, so click that button and authenticate. Also make sure that 'Pointer can be controlled using the keypad' is not checked under the 'Mouse Keys' tab.

---

