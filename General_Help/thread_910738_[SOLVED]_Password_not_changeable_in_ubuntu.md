---
title: "[SOLVED] Password not changeable in ubuntu"
date: 2008-09-04
forum: General Help
---

### Post by Camilia on 2008-09-04
Unable to change password fro logging on to computer. I open about me. Get this message - There was an error while trying to get the addressbook information Evolution Data Server can't handle the protocol.  Could this because I removed evolution mail or is this do to a virus? I can't even close the page. 

Pasted in terminal 'sudo apt-get -f and got installE: Invalid operation instal. So I reinstalled evolution. Don't understand why I have to have. Can't even get it to work, for after I put in password of address I get prompted for a key password. Well now the second about me worked. Guess the second one will go away after I shut pc off.

---

### Post by Cheesehead on 2008-09-04
The long answer:
About Me is part of the gnome-control-center package. When you uninstalled Evolution, you may (or may not) have broken a dependency - it depends on how you uninstalled it. Or it might be a bug - Gnome is...complicated.

Your Options:
1) If you simply want to change your own user password, and you're not allergic to the command line, use the command 'passwd' (no sudo). The system will prompt you for your current password and then your new password twice. *The system will not move the cursor* when you're typing passwords - that's normal for command-line passwords.

2) If you feel obligated to fix your gnome-control-center package (if it doesn't annoy you, then don't bother), you can do so from Synaptic, or by using the command 'sudo apt-get -f install'. If they can't locate anything broken, then don't worry; it's a bug and the original error was the system's fault (not yours).

---

