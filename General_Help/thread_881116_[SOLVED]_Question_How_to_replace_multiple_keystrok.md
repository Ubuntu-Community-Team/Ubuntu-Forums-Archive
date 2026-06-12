---
title: "[SOLVED] Question: How to replace multiple keystrokes with one keystroke"
date: 2008-08-05
forum: General Help
---

### Post by rhololkeolke on 2008-08-05
I was trying to learn how to type unicode characters in ubuntu.  After finding out that using alt and numpad doesn't work like in windows I did some searching.  I found sites telling people about the compose key.  I set it to the right windows key but then I couldn't find a key combination to display greek characters such as the omega.  I looked around some more and found sites detailing how to change the character mapping.  That didn't work then I found that if you enable support to enter complex characters using the the language tools and then press ctrl+shift+u while typing in the unicode value (such as 3a9 for omega).  I was able to get an omega and other Greek characters to show up.  My problem is that I would like to be able to either just press and hold one button instead of three while typing in the unicode number or substitute different key combinations for frequently used special characters such as the omega.  I know I could copy and paste it but I want to be able to just type a button or two instead of interrupting my work flow for just one character.  Therefore I would like to know how I can substitute one keystroke for many using a program like xbindkeys (or something similar).  Thanks in advance.

---

### Post by pauper on 2008-08-06
> I looked around some more and found sites detailing how to change the character
mapping. That didn't work then

System--Preferences--Keyboard (Preferences)

"Layouts" tab, click on "Add" button (it supports up to 4 different layouts).
Choose Greek under "Layouts", select something under "Variants". Click "Add".
You can reorder list by holding down left mouse button and dragging selected
layout up or down.

"Layout Options" tab, open Group Shift/Lock behavior, check any box to trigger
layout switch. I find "Both Shift keys together..." the most appealing. Click
"Close".

Right-click on top or bottom panel, select "Add to panel". Scroll down to
"Utilities" section, select "Keyboard Indicator". Click "Add". Right-click on it, check
"Lock to panel".

Done.

---

### Post by rhololkeolke on 2008-08-06
Thank you.  That fixes my problem of not being able to easily type non english characters.

---

