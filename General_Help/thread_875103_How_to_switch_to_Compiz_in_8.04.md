---
title: "How to switch to Compiz in 8.04?"
date: 2008-07-30
forum: General Help
---

### Post by Seven06Renault on 2008-07-30
There's a command in the terminal that switches to Compiz.  I just want the desktop cube.  I thought it was compiz --replace, but that only works as long as the terminal is open.  I know there's a simple command to switch to Compiz but for some reason every explanation on Google is overcomplicated and ridiculous.  Any help?

---

### Post by tuxxy on 2008-07-30
If you mean compiz window manager emerald, then your right that is the command, to run it and not have it close with the terminal you could try

ALT + F2 and run the command here, you can edit your system > prefs > sessions to prevent having to enter this command at every bootup

To enable desktop cube just enable the plugin in your advanced desktop effects manager.

---

### Post by Seven06Renault on 2008-07-30
Arg, that isn't working either.  It works for a split second and then immediately goes back to Metacity.

---

### Post by mehtdosa11 on 2008-07-30
> **Seven06Renault said:**
> Arg, that isn't working either.  It works for a split second and then immediately goes back to Metacity.
have you tried installing 'fusion icon' for compiz? it's a more graphical interface for turning on compiz or going back to metacity.

---

### Post by Seven06Renault on 2008-07-30
I just did that but it didn't work.  It switches to compiz for a split second then it switches back.  This is driving me so crazy in combination with Ubuntu being particularly unreliable and buggy right now.

Sorry for the frustration, I just really want this to work.  I can even use ctrl+alt+right/left to switch desktops.  I'm just stuck on one.

---

### Post by billgoldberg on 2008-07-30
in a terminal do

```
compiz
```

and look at the errirs,

post them

---

### Post by mehtdosa11 on 2008-07-30
well it's a bit beyond me then i'm afraid. bit of a newbie myself.

maybe try a complete re-install of compiz. good luck.

---

### Post by AnarchyCow on 2008-07-30
I would recommend, first, make sure Compiz Fusion is installed.

Then, if you would like, to use the "emerald --replace" command, make sure Emerald is installed.
```
sudo apt-get install emerald
```

Then, make sure that Emerald is setup to run when Ubuntu starts.
'System -> Preferences -> Sessions'
Then, under the "Startup Programs" tab, add this entry:
```
Name: Emerald
Command: emerald --replace
```
You can add a comment also if you wish.
Just hit OK, and close that window, then press 'CTRL+ALT+Backspace' to restart your X session, and that should have done it.

Once that is done, you can log back in, then simply go.
'System -> Preferences -> Advanced Desktop Effects Settings'
And use that GUI to configure what you want =]

---

### Post by Seven06Renault on 2008-07-30
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
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

---

### Post by Seven06Renault on 2008-07-30
I tried that but it didn't seem to work.  It still did the thing where it loads Compiz for a split second then switches back to Metacity or whatever.  I even removed Metacity.

EDIT: So I'm in Emerald or what not, and Desktop Wall works fine, but when I switch to Desktop Cube it doesn't work. So Compiz is working, just not the Cube, which is what I want of course.

---

### Post by Seven06Renault on 2008-07-30
SUCCESS!  Thanks all!

---

