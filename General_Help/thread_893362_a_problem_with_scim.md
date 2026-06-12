---
title: "a problem with scim"
date: 2008-08-18
forum: General Help
---

### Post by benner on 2008-08-18
i installed xubuntu in english. unlike in ubuntu, when i opened the language selector, english was the only one listed.  so i added all the packs for chinese. no problem.  then it appeared in the language selector and i was able to add it. but the scim trigger (ctrl+space) does nothing. i can't access the chinese input.

but then i logged out and logged in again in chinese.  scim worked fine.  the trigger worked, the fonts were there.  i logged out and in again in english.  again, nothing.

?

---

### Post by benner on 2008-08-18
when it is logged in in chinese, the 'enable input of complex characters' box is checked. when i am logged in in english, i check off the box, hit 'apply' and it gives me a 'reboot required' message. i click 'ok' and then the check mark in the box disappears. i reboot, it doesn't work, i open language support, the box is still unchecked.

---

### Post by seshomaru samma on 2008-08-19
try installing scim-bridge-client-gtk
```

sudo aptitude install scim-bridge-client-gtk
```

---

### Post by benner on 2008-08-19
thanks. but it didn't work. i added that and a few other scim packages afterwars.  still nothing.  then i did a fresh install and tried again.  this time i installed in chinese.  so scim works in chinese but when i log in in english, nothing.

---

### Post by seshomaru samma on 2008-08-20
in that case read [this ]("https://help.ubuntu.com/community/SCIM")
go to the part that says :Additional configuration if you're not using a CJK session and try running the im-switch. log out ,log in and if it doesnt work try the next step ("Edit the file /etc/X11/xinit/xinput.d/scim ")

---

### Post by benner on 2008-08-20
well, it sorda worked. now, i can right click in the document (in abiword) and select 'input method' and choose scim. then when i ctrl+space, scim comes up. but when i type, the document gives me tiny little circles where there should be chinese characters.  the scim selector gives me characters to choose from but once clicked, they appear in the document as the little circles.

which may or may not be related to my other thread:

[http://ubuntuforums.org/showthread.php?t=894576](http://ubuntuforums.org/showthread.php?t=894576)

where i am trying to get xfce to display the menus in chinese.  only some parts of them appear in chinese.  

apparently, chinese support in ubuntu is just bad. shame, really. i am trying to get it all perfect then remaster the disk so no one else i know has to go through this.

---

### Post by seshomaru samma on 2008-08-22
can you tell me which stages you followed?
did you run the im-switch?
did you edit the /etc/X11/xinit/xinput.d/scim file?
I have installed Xubuntu with Chinese support in the past and it worked in the end. 
Though Chinese support is far from perfect it does work but a little tricky to set up on XFCE

---

### Post by benner on 2008-08-22
after i ran the imswitch scim came up with the trigger. i didn't edit the file because i assumed that the reason for doing that was to get scim to appear. well now it appears with the ctrl+space.  now the problem seems to be font related as i am getting those little circles where chinese characters should be. but then i installed every font i could find for chinese and nothing.

i will to edit the file you mention and see if it makes a difference.  i will post back with the results.  thanks for sticking with me.

---

### Post by seshomaru samma on 2008-08-22
if scim shows up with the trigger then editing the scim file probably wouldn't work.
I don't know how to solve the font problem
i suggest you post on the scim forum

---

