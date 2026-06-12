---
title: "[SOLVED] cannot resize a window that has spilled over two workspaces"
date: 2008-11-16
forum: General Help
---

### Post by hwttdz on 2008-11-16
Somehow a window got resized such that it takes up two workspaces.  I can increase the width, but I can't decrease the width such that it is contained on only one workspace.  I've tried wmctrl, but I guess it doesn't handle things which have accidentally fallen onto two workspaces.  I've tried changing the number of workspaces (to one, in the hopes that it auto resized or something).  I've tried disabling compiz effects.  Any other suggestions.  I've also tried wmctrl after changing workspaces and disabling effects.

---

### Post by CatKiller on 2008-11-16
Go to the rightmost workspace that has the window on and resize it smaller as much as you can, then go to the next-left workspace and drag the window to the left so that the right edge of the window is on that workspace. Then resize the window smaller again. Once the window is the size that you want, move it to where you want.

---

### Post by hwttdz on 2008-11-16
I cannot resize it any smaller, and when it is size the minimum it can be it takes up more than the width of one full workspace.  

Which is to say if I got to the rightmost (2nd) workspace and only a fraction of the window is visible on that workspace because the majority of it is on the first workspace.  I cannot resize the window horizontally any smaller.  

Clearly window sizes are remembered somewhere, if I could edit the file which is remembering all would be well.  

Solved: The window was the file properties of an image.  To my dismay moving, copying or renaming the image did not work.  Finally I tried editing in an image editing program and saving as.  That did work.  So a workaround is found, however no solution to the bug exists.  And if it were firefox or something that got stretched across two workspaces I would have been in more serious trouble.

Interestingly this does not work if I export from gimp, but does if I export from kolourpaint.

---

### Post by CatKiller on 2008-11-16
If it were a Firefox window, it wouldn't be a problem at all. The key part is dragging the window to the left so that the resize border is accessible with enough space to resize it.

In this case, you say the window couldn't be resized because the window had to be that large to fit the content in. I've never had any problems with the file properties windows - they just behave like any other - but perhaps you had some very long metadata or comments or something that were causing you problems.

I'm glad you sorted it out, anyway.

---

