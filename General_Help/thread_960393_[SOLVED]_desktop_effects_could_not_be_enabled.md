---
title: "[SOLVED] desktop effects could not be enabled"
date: 2008-10-27
forum: General Help
---

### Post by Sponzenbroekske on 2008-10-27
Yesterday they worked today they don't
```
annick@asus:~$ compiz                                                                                                                                                             
Checking for Xgl: not present.                                                                                                                                                     
Detected PCI ID for VGA:                                                                                                                                                           
Checking for texture_from_pixmap: not present.                                                                                                                                     
Trying again with indirect rendering:                                                                                                                                              
Checking for texture_from_pixmap: present.                                                                                                                                         
Checking for non power of two support: present.                                                                                                                                    
Checking for Composite extension: present.                                                                                                                                         
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.                                                                                                         
Checking for Software Rasterizer: Not present.                                                                                                                                     
Checking for nVidia: not present.                                                                                                                                                  
Checking for FBConfig: present.                                                                                                                                                    
Checking for Xgl: not present.
Segmentation fault
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
Window manager warning: Failed to read saved session file /home/yannick/.config/metacity/sessions/105ee0a946bc0d3df1122512324727302300000060670017.ms: Failed to open file '/home/yannick/.config/metacity/sessions/105ee0a946bc0d3df1122512324727302300000060670017.ms': No such file or directory
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:129: Unable to locate image file in pixmap_path: "arrow-down-ins.png"
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:133: Background image options specified without filename
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:542: Unable to locate image file in pixmap_path: "arrow-down-ins.png"
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:544: Overlay image options specified without filename

```

This do I get when I try to update/upgrade, it says that the compiz-core needs to be upgraded
```
he following packages will be upgraded:                                                                                                                                           
  compiz-core                                                                                                                                                                      
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                                                                                                                     
Need to get 0B/843kB of archives.                                                                                                                                                  
After this operation, 2228kB of additional disk space will be used.                                                                                                                
Do you want to continue [Y/n]? y                                                                                                                                                   
WARNING: The following packages cannot be authenticated!                                                                                                                           
  compiz-core                                                                                                                                                                      
Install these packages without verification [y/N]? y                                                                                                                               
debconf: unable to initialize frontend: Dialog                                                                                                                                     
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)                                                                                           
debconf: falling back to frontend: Readline                                                                                                                                        
(Reading database ... 148761 files and directories currently installed.)                                                                                                           
Preparing to replace compiz-core 1:0.7.8-0ubuntu4 (using .../compiz-core_1%3a0.7.9+git20080918.shame-0_amd64.deb) ...                                                              
Unpacking replacement compiz-core ...                                                                                                                                              
dpkg: error processing /var/cache/apt/archives/compiz-core_1%3a0.7.9+git20080918.shame-0_amd64.deb (--unpack):                                                                     
 trying to overwrite `/usr/bin/compiz', which is also in package compiz-wrapper                                                                                                    
dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                                                                          
Processing triggers for man-db ...                                                                                                                                                 
Errors were encountered while processing:                                                                                                                                          
 /var/cache/apt/archives/compiz-core_1%3a0.7.9+git20080918.shame-0_amd64.deb                                                                                                       
E: Sub-process /usr/bin/dpkg returned an error code (1)        

```

edit: ow yeah
Ubuntu 8.10 64bit
ATI RADEON HD 2400 (driver installed)

---

### Post by Sponzenbroekske on 2008-10-27
Still not working and for the record, I'm using GNOME (and while I'm here, what does GNOME stand for?)

---

### Post by hictio on 2008-10-27
Not sure, but, I start my Desktop Effects like this:
```

/usr/bin/compiz --replace ccp & /usr/bin/emerald --replace &

```

Did you installed or upgraded something? Any why the Effects stopped working?
My Desktop Effects, I mean, the only problem I had was that I have disabled up purpose, thru "System -> Preferences -> Appearance -> Visual Effects", and after that I wasn't able to start them again. 


> 
I'm using GNOME (and while I'm here, what does GNOME stand for?)


From Wikipedia:
"The name originally stood for GNU Network Object Model Environment, though this acronym is deprecated."

---

### Post by hictio on 2008-10-28
Last week I had a similar problem, couldn't start the Desktop Effects, even tho they were working perfectly, stopped them a minute, and after that I wasn't able to make them work again.

In the end, I was able to, using a script which link I found on the Compiz forum, it is called "[compiz-check](http://forlong.blogage.de/entries/pages/Compiz-Check)".

I have posted everything on my blog: [Vanishing plugin](http://oesediez.blogspot.com/2008/10/vanishing-plugin.html), compared to your posted problems, there are a few things I did not had or did:

- I never tried to update/ upgrade compiz while I wasn't able to use Compiz.

- I did not got a [segmentation fault](http://en.wikipedia.org/wiki/Segmentation_fault) when tried to execute Compiz.

- The errors I got when I was trying to run Compiz manually did not include the Theme errors that I see on yours:

```

Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
Window manager warning: Failed to read saved session file /home/yannick/.config/metacity/sessions/105ee0a946bc0d3df1122512324727302300000060670017.ms: Failed to open file '/home/yannick/.config/metacity/sessions/105ee0a946bc0d3df1122512324727302300000060670017.ms': No such file or directory
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:129: Unable to locate image file in pixmap_path: "arrow-down-ins.png"
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:133: Background image options specified without filename
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:542: Unable to locate image file in pixmap_path: "arrow-down-ins.png"
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:544: Overlay image options specified without filename

```

Hope this helps.

---

### Post by Sponzenbroekske on 2008-10-28
Thx that got me a little further but not far enough though :(

```
yannick@asus:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME      
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 2400
 Driver in use:         fglrx                                       
[COLOR="Red"] Rendering method:      None [/COLOR]                                       

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


```

SO I HAVE NO RENDERING METHOD, WHAT NOW?

---

### Post by hictio on 2008-10-28
Too bad, I'm sorry, then again, that segfault doesn't look good at all.
Do you have any clue why the Desktop Effects might have stopped working?
Updates? Installed something?

---

### Post by Sponzenbroekske on 2008-10-28
> **hictio said:**
> Too bad, I'm sorry, then again, that segfault doesn't look good at all.
Do you have any clue why the Desktop Effects might have stopped working?
Updates? Installed something?

I upgrade every time I log on (sudo apt-get update && sudo apt-get upgrade).
But I didn't install something, or at least I don't think so.

I turned off my laptop with compiz working, I turned it back on the next day without compiz working or even without any desktop effects.

But it is off course still a BETAversion, so maybe it is a bug.

---

### Post by niaz11 on 2008-10-28
start the Desktop Effects, even tho they were working perfectly, stopped them a minute, and after that I wasn't able to make them work again.

---

### Post by Sponzenbroekske on 2008-10-28
> **niaz11 said:**
> start the Desktop Effects, even tho they were working perfectly, stopped them a minute, and after that I wasn't able to make them work again.

type in a terminal ```
compiz
``` and post the output

---

### Post by Sponzenbroekske on 2008-10-28
> **hictio said:**
> 
- The errors I got when I was trying to run Compiz manually did not include the Theme errors that I see on yours:

```

Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
Window manager warning: Failed to read saved session file /home/yannick/.config/metacity/sessions/105ee0a946bc0d3df1122512324727302300000060670017.ms: Failed to open file '/home/yannick/.config/metacity/sessions/105ee0a946bc0d3df1122512324727302300000060670017.ms': No such file or directory
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:129: Unable to locate image file in pixmap_path: "arrow-down-ins.png"
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:133: Background image options specified without filename
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:542: Unable to locate image file in pixmap_path: "arrow-down-ins.png"
/home/yannick/.themes/CarbonoRED-0.3/gtk-2.0/gtkrc:544: Overlay image options specified without filename

```

Hope this helps.

about the theme-errors, there no big deal, just that theres a file missing, but that is replaced automatically by the default file, or thats what I think :)

---

### Post by hictio on 2008-10-28
Yeah, I think so too, but I was just pointing the differences between my setup and tests.
I bet your problem lies on segfault one.

---

### Post by Sponzenbroekske on 2008-10-28
> **hictio said:**
> Yeah, I think so too, but I was just pointing the differences between my setup and tests.
I bet your problem lies on segfault one.

I know so :p
I'll try removing compiz and the ATI driver and reinstall them.

---

### Post by Sponzenbroekske on 2008-10-28
owkeej reinstalled everything (purge and then install), gonna reboot for the driver to become active, wish me luck :p

Still not able to turn on desktop effects, but the rendering method is filled in :)
```
yannick@asus:~/Desktop$ ./compiz-check       

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME      
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 2400
 Driver in use:         radeon                                      
 Rendering method:      AIGLX                                       

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

yannick@asus:~/Desktop$

```

---

### Post by Sponzenbroekske on 2008-10-28
```
yannick@asus:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME      
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 2400
 Driver in use:         fglrx                                       
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

yannick@asus:~$

```

No rendering method anymore, but desktop effects are enabled :)
Compiz is installed, but only the base off it, so ill post this thread s solved and install the rest off compiz, if anything else go's wrong ill let you know. :)

---

### Post by hictio on 2008-10-28
F*ck, that's weird isn't?
Is it any slow than before or something strange?

---

### Post by Sponzenbroekske on 2008-10-28
> **hictio said:**
> F*ck, that's weird isn't?
Is it any slow than before or something strange?

nope
I thought I removed my config files too, but all the settings were still the same.

I know it: Linux is self-healing :p


(ps.: team errors are solved too, just went to the mentioned path and line and corrected the path-name:))

---

### Post by SaddaGocaraRupa on 2008-10-30
> **hictio said:**
> F*ck, that's weird isn't?
Is it any slow than before or something strange?

I have the same compiz-check output as the above user (no rendering method when turning on compiz) but have a 4870, not a 2600. 

My emerald decorators show up but the windows can't be moved. I just purged and reinstalled all my drivers, compiz and emerald. what can i do???

PS: this is what the terminal says:

```
wigui@ubuntu:~$ /usr/bin/compiz --replace ccp & /usr/bin/emerald --replace &
[1] 9804
[2] 9805
wigui@ubuntu:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (core) - Warn: Plugin 'ccp' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop

```

---

### Post by Sponzenbroekske on 2008-10-30
just type ```
compiz
``` a terminal and post the output plz

---

### Post by SaddaGocaraRupa on 2008-10-30
> **Sponzenbroekske said:**
> just type ```
compiz
``` a terminal and post the output plz

```
wigui@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
Starting gtk-window-decorator
```

and compiz-check:

```
wigui@ubuntu:~$ ./compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

like you earlier (kind of)..no rendering method

---

### Post by Sponzenbroekske on 2008-10-31
You could try what I have done.
```
cd /
``````
sudo apt-get purge compiz*
```

And remove your ATI driver, i actually dont know anymore how it did thar, what I do know is that you gotta be carefull, cuz I got a terminal question were I had to type yes in full, cuz it would harm my system, so i didnt type yes ;)

---

