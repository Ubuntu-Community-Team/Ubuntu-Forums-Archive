---
title: "[SOLVED] Compiz Cube Help?"
date: 2008-11-03
forum: Hardware
---

### Post by cairnzi on 2008-11-03
hi there, ive got compiz installed n somewhat working, but i do not no how to make the cube appear so i can turn it Etc. any help would be great many thanks.

---

### Post by mcclown on 2008-11-03
> **cairnzi said:**
> hi there, ive got compiz installed n somewhat working, but i do not no how to make the cube appear so i can turn it Etc. any help would be great many thanks.

Hey,

Install the package compiz-settings-manager if you haven't already.

```
sudo apt-get install compiz-settings-manager
```

Now if you go to System->Preferences->CompizConfig Settings Manager you will be able to set more preferences for compiz.

For the cube to work disable the *Desktop Wall* plugin and enable the *Desktop Cube* and *Rotate Cube* plugins.

Click the general button on the right and choose *General Options* and go to the *Desktop Size* tab. Increase the *Horizontal Virtual Size* slider to 4 (ie. 4 sides of a cube). This is the missing configuration step that I find most people miss, I can't understand why this isn't automatically configured when you enable the desktop cube.

Now you should have your rotating cube working, the standard key bindings(these can be changes by using *CompizConfig Settings Manager*):

Rotate Left: <Ctrl> <Alt> <Left Arrow>
Rotate Left: <Ctrl> <Alt> <Right Arrow>
Free Rotate: <Ctrl> <Alt> <Mouse Button 1>
Move Selected Window To Left Desktop: <Ctrl> <Alt> <Shift> <Left Arrow>
Move Selected Window To Right Desktop: <Ctrl> <Alt> <Shift> <Right Arrow>

Have fun!

---

### Post by cairnzi on 2008-11-03
excellent!!! cheers very much.

---

