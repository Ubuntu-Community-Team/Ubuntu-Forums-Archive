---
title: "Cannot input commands"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by mgichoga on 2005-12-08
I have a peculiar problems with ubuntu, I recently installed ubuntu and I'm running into a case where when I press ctrl + alt + F1 to get to the console when the login screen appears, I cannot input any commands after I log in at the console. The same happens when I ssh into the box, I can't input any command e.g even ls...returns 'command not found'. Is a service not running or what do I need to correct this

Mike

---

### Post by taurus on 2005-12-08
Sounds to me like your PATH either is all screwed up or doesn't setup correctly!!!  What shell (bash or csh/tcsh) are you using?  May need to modify ~/.bashrc (for bash shell) or ~/.cshrc (for csh/tcsh shell) then...

---

