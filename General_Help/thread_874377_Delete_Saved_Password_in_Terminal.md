---
title: "Delete Saved Password in Terminal"
date: 2008-07-29
forum: General Help
---

### Post by danjdel on 2008-07-29
I'm on 8.04. I was using ice window manager using terminal (I'm pretty sure the same one as default for gnome). 
I was getting git setup and I had to give it my SSH public key. I put that into some popup box and checked to save my key, but I put it in wrong. Now I can't figure out how to delete that saved thing. I already deleted the file in ~/.gnome2/keyrings/ (I forget what the name was but whatever single file was in there). 
If I don't delete this password I'll never be able to use git again.

---

### Post by ibuclaw on 2008-07-29
Have you looked in "**~/.ssh**"?

Running
```
ssh-vulnkey
```
Should help you find it (mine was in the ~/.ssh directory as I mentioned a moment earlier).

Regards
Iain

---

### Post by Mister.Vash on 2008-07-29
I believe they should be stored in the seahorse application.

Go to  Applications -> Accessories -> Passwords and Encryptions keys

---

### Post by danjdel on 2008-07-29
tinivole, the issue wasn't my ssh key it was that I typed something in that I thought was my ssh public key but wasn't and then saved that.

Mister.Vash I went there and tried. now I actually deleted everything in there and it still won't work. It must be stored somewhere else.

---

### Post by Mister.Vash on 2008-07-29
Did you restart after removing them?  I believe that it may be cached for the session

---

### Post by danjdel on 2008-07-30
No, just tried that. It didn't work.
It didn't just get saved automatically, I actually checked a "save this code" box. But I'm not sure what program it was that was saving it (remember that I was using ICE at the time).

---

### Post by danjdel on 2008-07-30
So anyone else have an idea?
Recap:
It effects all of my shells (terminal, konsole, xterm).
I was using Ice WM at the time.
I have no passwords saved in seahorse.

---

### Post by danjdel on 2008-08-04
Ok, as it turns out I just saved it for that key. If had just tried it again after generating a new key it would have been fine.
Thanks everyone for your help.

---

