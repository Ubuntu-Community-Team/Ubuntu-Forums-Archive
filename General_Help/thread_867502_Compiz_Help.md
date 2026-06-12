---
title: "Compiz Help"
date: 2008-07-22
forum: General Help
---

### Post by redfox1160 on 2008-07-22
I typed ```
compiz
``` into the terminal and changed some settings. Now, I wanted to change them back; but when I type it in, nothing happens. Can someone help? Thanks.

---

### Post by iaculallad on 2008-07-22
Try:

```
compiz-settings
```

Or go to System > Preferences > Compiz Settings Manager

---

### Post by redfox1160 on 2008-07-22
> **iaculallad said:**
> Try:

```
compiz-settings
```

Or go to System > Preferences > Compiz Settings Manager

This Popped Up:
```
bash: compiz-settings: command not found
```

---

### Post by redfox1160 on 2008-07-22
bump

---

### Post by iaculallad on 2008-07-22
On your terminal, try installing the compiz manager:

```
sudo apt-get install gnome-compiz-manager
```

System > Preferences > Compiz Settings Manager

---

### Post by redfox1160 on 2008-07-22
> **iaculallad said:**
> On your terminal, try installing the compiz manager:

```
sudo apt-get install gnome-compiz-manager
```

System > Preferences > Compiz Settings Manager

This Popped Up:
```
eric@GrossBoysLaptop:~$ sudo apt-get install gnome-compiz-manager
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-compiz-manager

```

---

### Post by iaculallad on 2008-07-22
Replace it with:

```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```

---

### Post by redfox1160 on 2008-07-23
This popped up after I typed in compiz (after doing the sudo apt-get update and sudo apt-get install compizconfig-settings-manager):

```
eric@GrossBoysLaptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

---

### Post by northern lights on 2008-07-23
Run ```
gconf-editor
``` and navigate to ```
/apps/compiz/plugins/scale/allscreens/options/initiate_edge
```. Remove the value.

---

### Post by redfox1160 on 2008-07-23
> **northern lights said:**
> Run ```
gconf-editor
``` and navigate to ```
/apps/compiz/plugins/scale/allscreens/options/initiate_edge
```. Remove the value.
remove initiate_edge ?

---

### Post by northern lights on 2008-07-23
Set it to "Disabled" or leave it blank.

---

### Post by redfox1160 on 2008-07-23
Thanks.

---

### Post by redfox1160 on 2008-07-23
How do I set it as disabled? It has [] in where other ones say disabled right now.

---

### Post by redfox1160 on 2008-07-23
can someone help?

---

### Post by overdrank on 2008-07-23
Thread moved :)

---

### Post by redfox1160 on 2008-07-23
I still need help please...

---

### Post by redfox1160 on 2008-07-23
This is my last attempt at getting help (sorry for all the bumping)

---

### Post by overdrank on 2008-07-23
> **redfox1160 said:**
> This is my last attempt at getting help (sorry for all the bumping)

HI and I can try and help, what is the model of the graphics card?
Have you tried compiz-check from the FAQ's, link in my signature.

---

