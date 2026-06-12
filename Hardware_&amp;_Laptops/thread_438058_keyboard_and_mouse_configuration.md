---
title: "keyboard and mouse configuration?"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by mad chey on 2007-05-09
Hi

hoping someone can help with configuring a logitech cordless desktop mx3000

finally getting my sons pc converted over to ubuntu feisty along with the rest of us, but he has the above, and i cant seem to get all of his mouse buttons working (keyboard hmm havent even ventured down that road yet)

he has the normal left and right buttons, scrolling wheel, plus 2 additional shoulder buttons and the mouse wheel can move left or right

now ive used the normal 5 button mouse config which worked lovely for the rest of us, but for this one his shoulder buttons are not working as ours are

one does nothing and the other does the same as the right click

the left and right movement of the mousewheel will move your selection to the next file to the left or right accordingly which im guessing is what they are supposed to do (ive never had one)

so for me the main problem is not being able to get these shoulder buttons working, ive tried google but am drawing a blank

anyone got any suggestions pls?

---

### Post by mad chey on 2007-05-09
ok ive fixed it, dont know how i didnt notice this before but

on our pcs in xorg.conf the protocol is "ExplorerPS/2"

but on his it was "IMPS/2"

changed it to what we have and perfect works lurvely

---

### Post by mad chey on 2007-05-19
except when you log in as a different user most bizzare

---

