---
title: "two big problems"
date: 2008-07-26
forum: General Help
---

### Post by bradpurvis on 2008-07-26
i'm having two big problems with ubuntu. i can't get flash to work or compiz someone please help or i will have to switch back to windows.i have already set up flash but something called nash keeps going in from of whatever it is i try to watch/listen to

---

### Post by stevoo on 2008-07-26
how did you set up flash ? 
there are two ways
Install libflashplugin ... think that is the name
or download and install flash from adobe and run that one.

---

### Post by bradpurvis on 2008-07-26
how do i install the plugin its on my desktop but ubuntu doesn't know how to handle that file.

plus whenever i try to enable desktop effects it says The Composite extension is not available and i have to exit the windows instead of hitting ok

---

### Post by bradpurvis on 2008-07-26
Does anyone know how to help me with the desktop effects or flash player i really need some help or i will have to switch back to windows i really don't want to but i cant use my computer if i don't have flash. Please help

---

### Post by avtolle on 2008-07-26
On the first problem, remove gnash by going to Synaptic (System>>Administration>>Synaptic Package Manager) and search for gnash. Mark for total removal, click on apply, and that should resolve the conflict.

---

### Post by bradpurvis on 2008-07-26
k i will work on that. does anyone know about the desktop effects error?

---

### Post by Ryadt on 2008-07-26
Try enabling your graphic card in System > Administration > Hardware Drivers.

---

### Post by Sef on 2008-07-26
> plus whenever i try to enable desktop effects it says The Composite extension is not available and i have to exit the windows instead of hitting ok

Have you enabled the drivers in System > Administration > Hardware Drivers?

If that does not work, then please inform us as to your graphics card.  

It is best to post each problem separately.

---

### Post by overdrank on 2008-07-26
> **bradpurvis said:**
> k i will work on that. does anyone know about the desktop effects error?

Also look at the link in my signature FAQ's on comp-fusion. :)

---

### Post by bradpurvis on 2008-07-26
yes i have enabled the system drivers.

i have a compaq presario i have a ATI RADEON XPRESS 200 GRAPHICS CARD

I HAVE A 3200+ AMD SEMPRON PROCCESSOR Is there any problem with any of that?

---

### Post by overdrank on 2008-07-26
> **bradpurvis said:**
> yes i have enabled the system drivers.

i have a compaq presario i have a ATI RADEON XPRESS 200 GRAPHICS CARD

I HAVE A 3200+ AMD SEMPRON PROCCESSOR Is there any problem with any of that?

Hi and the ATI 200 has given me issues when trying to assist users. But there is some users that have had luck with it and if you search the forums I am sure you will find some info.

---

### Post by Ryadt on 2008-07-26
try ```
sudo apt-get install xserver-xgl
```

---

### Post by bradpurvis on 2008-07-26
i ran compiz check and this is what showed up

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Composite manually disabled 

what do i do?

---

### Post by Ryadt on 2008-07-26
Type in terminal
```
sudo apt-get install linux-restricted-modules-generic
```
```
sudo apt-get install xserver-xgl
```
```
sudo apt-get install compiz compizconfig-settings-manager
```

---

### Post by bradpurvis on 2008-07-26
i did have a look at that FAQ but compiz still isn't working. neither is flash i tried the compiz checker thing this is what showed up

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Composite manually disabled 

Would you like to know more? (Y/n) y

 It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "0"

---

### Post by bradpurvis on 2008-07-26
i tried what Ryadt said but it said everything was installed already and desktop effects still haven't been fixed

---

### Post by bradpurvis on 2008-07-26
i don't know how to fix the composite thing any pointers anyone?

---

### Post by aeon on 2008-07-26
for the compiz problem, try adding 
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

at the end of /etc/X11/xorg.conf, restart X and then try it again

---

### Post by Ryadt on 2008-07-26
Can you post the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by bradpurvis on 2008-07-26
didn't work and i don't know why i pasted both codes in the terminal this is what showed up

purvis@purvis-desktop:~$ Section "Extensions"
bash: Section: command not found
purvis@purvis-desktop:~$     Option         "Composite" "Enable"
bash: Option: command not found
purvis@purvis-desktop:~$ EndSectioncat /etc/X11/xorg.conf
bash: EndSectioncat: command not found
purvis@purvis-desktop:~$

---

### Post by bradpurvis on 2008-07-26
i fixed the flash problem

---

### Post by Ryadt on 2008-07-26
Try this```
gksudo gedit /etc/X11/xorg.conf
```
Change the value of the composite line from 0 to 1. Save and close. Restart X (CTRL+ALT+BACKSPACE).

---

### Post by bradpurvis on 2008-07-26
thanks that worked perfect

---

### Post by Ryadt on 2008-07-26
:)...
can you please mark the thread as solved please...

---

