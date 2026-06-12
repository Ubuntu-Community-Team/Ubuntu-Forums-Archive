---
title: "[SOLVED] How can I change this full screen like thing?"
date: 2008-11-04
forum: General Help
---

### Post by Arwen on 2008-11-04
Hello everyone!

How can I go back from the view you can see in my screenshot? I did't change any options, it changed on its own and sometimes it flashes and won't respond.
I didn't do anything weird, the only thing I installed is Open Office 3..

Thanx!

---

### Post by jazzgossen on 2008-11-04
Strange... try alt+f4 to close the window? Or alt+f10 to toggle the maximisation state?

---

### Post by Arwen on 2008-11-04
Alt+F4 works fine and Alt+F10 opens the File menu up left..How can I bring back minimise,maximise and close window buttons up right?

---

### Post by Peter09 on 2008-11-04
What theme are you using, have you got compiz enabled?

---

### Post by Arwen on 2008-11-04
I don't remember the name of the theme,it's a black and blue one..I have compiz enabled too.But everything worked fine for four months..

---

### Post by Peter09 on 2008-11-04
Try changing the theme, I have found that some themes do not show the buttons correctly. Also check your compiz settings. It is possible to stop these buttons from displaying.

---

### Post by Arwen on 2008-11-04
Nothing changes with different theme..It's strange because (thank ubuntu!) only in Nautilus the top of windows disappears,in all other apps everyting is fine..for now..that's why I won't try to disable compiz yet as proposed to similar problems.
I'll take a more careful look in compiz settings in a few hours and post back.
Thank you!

---

### Post by Arwen on 2008-11-04
This command > compiz --replace ccp & emerald --replace &

gave me these:

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:02e1 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: The program 'emerald' is currently not installed.  You can install it by typing:
sudo apt-get install emerald
bash: emerald: command not found
present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (core) - Warn: Plugin 'ccp' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


Is that sth that can cause problems? Can I do anything about it and fix my problem?

---

### Post by Peter09 on 2008-11-04
Just to check, can you post the output of

```
lshw -C display
```

---

### Post by Arwen on 2008-11-04
> WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: G73 [GeForce 7600 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia


Do you think it's because of my graphics card?It won't be a surpise,for a month now I have to do "gksudo nvidia-settings" to change the screen resolution to the one I want(I replaced my monitor) everytime I login as it's never saved to X configuration file..

---

### Post by Peter09 on 2008-11-04
I think you have a problem with your compiz configuration. Not sure where to go from here. You could try removing compiz and re-installing it.

---

### Post by Arwen on 2008-11-04
I can simply remove everything having "compiz" in its name and install them all again right?

---

### Post by Peter09 on 2008-11-04
Well, thats the problem I'm not sure. Try re-installing? I am worried that removing compiz may make your GUI non-operational. You could still install from the recovery mode, just a bit hesitant I guess.

---

### Post by Arwen on 2008-11-04
I wouldn't like to remove it completely and cause worse problems than I already have.
I removed some effects (3D Windows, Wobbly Windows, Animations, Fading windows, Window Decoration) from tab Effects in compiz settings and it made tha tops of -all- windows disappear(I mean not only nautilus but firefox, open office, etc)..so I enabled them again..

---

### Post by Peter09 on 2008-11-04
Yes - windows decoration is the outside borders+titles on your windows.

---

### Post by syms on 2008-11-04
open home folder. in nautilus click view, then choose show hidden files and then youll see folder named .compiz, try to rename it to somethink like .compiz-backup . restart x server (ctrl + alt + backspace) or restart pc and see what will happen. if there would not be somethink good, then rename your .compiz-backup back to .compiz

---

### Post by Arwen on 2008-11-04
I did it but nothing changed..

---

### Post by Arwen on 2008-11-05
I think it's a problem of Window Decoration pluggin..Should I change anything in its general settings? I disabled/enabled it a couple of times.
Also would " compiz --replace " make things worse?

---

### Post by syms on 2008-11-05
hmm, install emerald ```
sudo apt-get install emerald
``` then go to compiz settings manager to window decorations and change line from compiz-decorator to emerald --replace. then restart x server

---

### Post by Arwen on 2008-11-20
The problem seems to be solved (on its own I must say,I just booted ubuntu and the tops of nautilus wondows were there!). Sometimes they disappear but most of the time they're OK and when they're not I use Alt-Tab to move around.

I wouldn't mind an explanation for this strange problem though..

Thank you everyone for your advice!

---

