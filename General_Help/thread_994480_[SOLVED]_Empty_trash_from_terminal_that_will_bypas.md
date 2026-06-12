---
title: "[SOLVED] Empty trash from terminal that will bypass permissions"
date: 2008-11-26
forum: General Help
---

### Post by coolethan on 2008-11-26
i have a file in my trash can and due to permissions on some of the files it won't delete from my trash can. how can i get it to go away. i have tried logging in as root in the terminal then typings some -r something somthing trash/* and that doesn't work.

---

### Post by ibutho on 2008-11-26
When you switch to root, the files you need to delete should be somewhere in /home/$USER/.local/share/Trash/files.

---

### Post by aysiu on 2008-11-26
Instead of logging in as root and typing "something," *paste* this command into the terminal: ```
sudo chown -R $USER:$USER ~/.local/share/Trash
``` and then empty your trash the normal point-and-click way.

Pasting instead of typing has two advantages:
1. You don't have to spend as much time and energy typing
2. You're less likely to make a mistake in spacing or case

---

### Post by coolethan on 2008-11-26
thanks a lot, i couldn't find the file anyways when i logged in as root and this worked perfectly. thanks again.

---

### Post by Krepta3000 on 2009-07-09
Wow, thanks, I just had the exact same problem, someone (me) had put a bunch of files into my shared Public folder, using credentials for a different user account, so that when I went and moved those files to the trash, well, they went to the trash, and wouldn't get deleted due to permissions.  Then I couldn't figure out where the heck the Trash folder existed in the file system structure, it was driving me nuts till I finally decided to come to ubuntu forums and search for an answer.  This thread was the first thing that popped up!  Your so awesome! :)

Yay!  I finally have an empty trash bin, and my hard drive is not full to the point that the system crashes and stuff!

---

