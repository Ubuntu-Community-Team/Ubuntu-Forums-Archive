---
title: "[SOLVED] Help!!! Computer wont allow me to log in!!!"
date: 2008-09-04
forum: General Help
---

### Post by RolandFlagg on 2008-09-04
I got annoyed for entering this password for a keyring to use the wireless internet so I googled it and followed the instructions from this website:
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)
When I logged out and tried to log back in again, it wouldn't even let me enter my username and password. There's just a message box saying "Authentication failed" with an "ok" button, which when I press does not do anything. I can't log in at all.
I can get into the virtue console mode, and am trying to edit the file back with the "vi" command, but I dont know how to use it, and made a bunch of changes I didn't mean to. So now I'm just trying to quit "vi" without saving.
Any help would be greatly appreciated.

---

### Post by Thingymebob on 2008-09-04
Quite vi without saving press esc to exit insert mode then type:
 
:q!

press return

once your back try replacing network manager with wicd [http://wicd.sourceforge.net]("http://wicd.sourceforge.net")

---

### Post by RolandFlagg on 2008-09-04
sorry, too late. I already did it the "easy" way by restarting the computer, hope it didn't save...

---

### Post by RolandFlagg on 2008-09-04
Update: Ok i successfully edited that file back to what it was before, but the msgbox is STILL there and wont let me enter my username and password...

---

### Post by RolandFlagg on 2008-09-04
Update again... Ok nevermind... turns out I didn't change the file properly... now the gibberish I typed in mistake is always there when I type "recover" after I vi the file.
I tried to follow the directions here: [http://ubuntuforums.org/showthread.php?t=581249](http://ubuntuforums.org/showthread.php?t=581249)
But all I hav access to is the virtual console, and I can't use gedit... The worst thing is... I'm completely confused by vim... someone PLEASE give me some pointers... I'll respond in about 8-9 hrs as i'm going to sleep now.

---

### Post by Thingymebob on 2008-09-04
Clearly you know how to open a file in vim,

Basics,
press **i** to enter insert mode so as you can edit
use cursor keys to navigate around
press **Esc** to exit insert mode

exit insert mode and type
**:w** (press return) to save the file
**:q** (press return) to quit vim
**:q!**(press return) to quit discarding changes
**:wq!**(press return) to quit writing changes
**u**(press return) undo

---

### Post by RolandFlagg on 2008-09-04
Omg thanks so much, I got it working. I dunno why, for others they needed that last line "@include common-pamkeyring" but for me, it was a matter of removing it...

In case anyone else had the same problem as I did, if you screwed up the file and shut down your computer, every time you edit it's gonna ask you to recover something, you have to delete the swap file with "sudo rm <file>", and THEN reedit the original file.

So now my question is how DO I get rid of this annoying window that asks me to "enter password for default kayring to unlock"?

edit: nevermind, I found another thread that deals with it specifically.

---

