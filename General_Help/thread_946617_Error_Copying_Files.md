---
title: "Error Copying Files"
date: 2008-10-13
forum: General Help
---

### Post by undoIT on 2008-10-13
Sometimes when I am dragging one folder to place in another folder that is open in a new window, if I let go to quick I get an Error Copying message. I am given the options to skip, retry or cancel. Retry doesn't work, so I cancel and then redrag the folder over to the new folder again and let go more slowly.

I don't remember this being a problem in Gutsy. Is anyone else seeing this?

---

### Post by shawnrgr on 2008-10-13
My best guess (cause this happens to me with Nautilus) when your dragging over the sidebar with all your location shortcuts the mouse likes to let go, then it tries to move the files to whatever shortcut you were over and it fails.

Try avoiding dragging the files directly over the sidbar and i bet you don't notice that anymore. Hopefully this will be corrected in later versions.

---

### Post by geirha on 2008-10-13
I tried to reproduce this myself, but either I don't have that problem, or I'm not fast enough.

When it happens, look at "~/.xsession-errors" and see if there are some more descriptive error messages.

Also, try creating a new user and see if that one also has this problem. If it doesn't, then it might be some setting nautilus doesn't like.

---

### Post by undoIT on 2008-10-13
I see this happen on two different laptops, both with Ubuntu 8.04 64-bit.

Looking at the .xsessions-error file. Nothing is time-stamped. What am I looking for?

---

### Post by geirha on 2008-10-13
Some applications print messages about what it's doing to stdout. This is caught and sent to .xsession-errors. I don't know if nautilus would print anything, but if it does, it might provide some more meaningful message than just "Error copying".

If you open a terminal and run ```
tail -f ~/.xsession-errors
``` it will continuously print the lines as they appear in the file, so see if it prints anything when you reproduce the problem.

---

