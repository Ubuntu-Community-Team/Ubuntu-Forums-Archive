---
title: "CLI - it awaits my command and I don't know what to do!"
date: 2008-10-30
forum: General Help
---

### Post by adamogardner on 2008-10-30
Without further ado:

adamogardner@CRONUS:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by tbehrens on 2008-10-30
Rather than run it in the shell you should run that from the alt-f2 "Run application"  dialog.  It seems to work alot better than running the compiz -replace or even metacity -replace for that matter...

---

### Post by adamogardner on 2008-10-30
do you suggest I close my terminal and reenter command in the altf2 app?

---

### Post by conundrumx on 2008-10-30
Yes.  This goes back to the olden days, when most applications you launched were ones you'd be interacting with until they exited.  If you're going to be running a command which is not CLI interactive (like compiz --replace) you should do it through Alt F2, or by appending an ampersand ( & ) to the end.  The ampersand tells the system to run the command and keep doing other things.

If you really want to get into things, you can launch a task, then decide to background it later by hitting Ctrl Z.  A message will show up with a number in brackets and the command you executed.  You can then type "bg bracketed_number" or "fg bracketed_number" to set it running in the background, or foreground; respectively.

---

