---
title: "[SOLVED] Bash Prompt Customization"
date: 2008-11-25
forum: General Help
---

### Post by aeroace on 2008-11-25
Hello All, 
    I have read many posts about customizing the bash prompt color. I can enter 

PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$"

to temporally change the color, but I can't make it permanent. I have tried adding the code above to etc/bash.basrc and commenting out the PS1 command already there, but it does not change the color in the terminal after rebooting. I am new to Linux so I'm sure I am just missing something simple. Any help would be much appreciated! Thank you so much for your time and advice.  

-- aeroace

---

### Post by bodhi.zazen on 2008-11-25
Add it to ~/.bashrc

Log out and back in (or start a new shell / terminal).

---

### Post by aeroace on 2008-11-26
Thanks so much, I thought the etc/bash.basrc was the correct place to add the code. Removing a quick comment in the correct file fixed the problem! Thanks again for your help.

-- aeroace

---

