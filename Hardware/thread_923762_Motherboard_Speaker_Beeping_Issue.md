---
title: "Motherboard Speaker Beeping Issue"
date: 2008-09-18
forum: Hardware
---

### Post by w35z0r on 2008-09-18
Hello,
I have a Dell Inspiron 1501 Laptop.  I recently installed Ubuntu 8.04 and LOVE it!  However, I have an issue.  Whenever I try and delete a character that is not there, the motherboard speaker beeps at me.  Its rather frighting and very annoying in a class.  

An example of what I mean by 'delete a character that is not there:'
If I where to click in a text box on a website that had nothing in it and press backspace, the speaker would beep.  

This mostly happens in the terminal, when I'm typing a command and change my mind and just hold down the backspace button.  when I hit the beginning of the line it beeps mercilessly at me.

I have my audio drivers installed... or at least I can hear things on my laptop so I assume they are installed.

Any help would be greatly appreciated! 

--W

---

### Post by bigken on 2008-09-18
I think you can turn the beep off in terminal edit profiles

---

### Post by IntuitiveNipple on 2008-09-18
If you are using *Terminal* (Applications > Accessories > Terminal) you can disable the **Terminal bell**.

From the Terminal window do **Edit > Profiles...**, select "Default" and press the **Edit** button. On the **General** tab deselect "Terminal bell" and then close the dialogs.

This setting will be used next time Terminal is started. To change the *current* session do the same thing from **Edit > Current Profile...**.

---

### Post by w35z0r on 2008-09-23
Great!  That fixed my problem with my terminal.  However, Pidgin does the same thing.  I searched for a bell option, but found none.

Any suggestions?

---

### Post by bigken on 2008-09-23
> **w35z0r said:**
> Great!  That fixed my problem with my terminal.  However, Pidgin does the same thing.  I searched for a bell option, but found none.

Any suggestions?



Tools/Preferences/Sounds

---

