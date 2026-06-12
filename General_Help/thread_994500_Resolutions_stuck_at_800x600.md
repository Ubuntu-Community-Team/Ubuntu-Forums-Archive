---
title: "Resolutions stuck at 800x600"
date: 2008-11-26
forum: General Help
---

### Post by Bobatron on 2008-11-26
Hey all I recently upgraded from windows XP to latest Ubuntu, I had some trouble installing it but it worked fine when I installed in safe mode, does that mean it only installed safe mode of Unbuntu? I had thought it only meant a safe mode of installation with reduced graphics during installation




As I cant seem to change resolution above 800x600 which makes it pretty unbearable, I've restarted PC already a few times and no matter what I pick I cant change resolution when I log in


Is there a command line in terminal I can use to change it just to test around?

---

### Post by HittingSmoke on 2008-11-26
> **Bobatron said:**
> Hey all I recently upgraded from windows XP to latest Ubuntu, I had some trouble installing it but it worked fine when I installed in safe mode, does that mean it only installed safe mode of Unbuntu? I had thought it only meant a safe mode of installation with reduced graphics during installation




As I cant seem to change resolution above 800x600 which makes it pretty unbearable, I've restarted PC already a few times and no matter what I pick I cant change resolution when I log in


Is there a command line in terminal I can use to change it just to test around?

What video card are you using?

Have you checked the Hardware Driver settings under System>Admin?

If that doesnt help (which is the case with my Nvidia card), try installing your drivers with EnvyNG.
```

sudo apt-get install envyng-gtk
```

I have to use this tool to get my restricted video drivers properly installed. Just run it and select your video card make (provided its Nvidia or ATI) and it does the rest for you

---

### Post by Bobatron on 2008-11-26
> **HittingSmoke said:**
> What video card are you using?

Have you checked the Hardware Driver settings under System>Admin?

If that doesnt help (which is the case with my Nvidia card), try installing your drivers with EnvyNG.
```

sudo apt-get install envyng-gtk
```

I have to use this tool to get my restricted video drivers properly installed. Just run it and select your video card make (provided its Nvidia or ATI) and it does the rest for you


Radeon 7000, pretty old but it ran XP without any problems


and I just checked Hardware Drivers and they aint installed apparently so I'll try run Envy, thanks for the help :D

---

### Post by Bobatron on 2008-11-26
being completely new to Linux I have to ask a stupid question....how do I get Envy to run? I used that line of code to download the installer yeah? but cant seem to get the program to run and when I use line of code again I just get an error saying its already the most up to date version

---

### Post by evildragon2 on 2008-11-26
Type:

```
envyng-gtk
```

in terminal to launch.
You can also go to Applications-->System Tools-->Envy to start it.

---

### Post by Bobatron on 2008-11-26
> **evildragon2 said:**
> Type:

```
envyng-gtk
```

in terminal to launch.
You can also go to Applications-->System Tools-->Envy to start it.


Command not found and there is no system tools in Applications.


I went onto ATI site and there are no drivers for Radeon 7000 series for Linux, is for XP but not Linux.

---

### Post by coolethan on 2008-11-26
have you tried using the screens and graphics GUI to change the resolution? applications-->other-->screens and graphics. if it is not there then you have to add it to the menu by right clicking up by applications and then clicking on edit menus. a new window will pop up, along the left side you will see a list of different menu catagories, select other and then on the right check the box beside screens and graphics and go ok or close whatever the button is. from the screens and graphics GUI you can choose exactly what monitor you have and the graphics card you have too.

---

### Post by Bobatron on 2008-11-26
> **coolethan said:**
> have you tried using the screens and graphics GUI to change the resolution? applications-->other-->screens and graphics. if it is not there then you have to add it to the menu by right clicking up by applications and then clicking on edit menus. a new window will pop up, along the left side you will see a list of different menu catagories, select other and then on the right check the box beside screens and graphics and go ok or close whatever the button is. from the screens and graphics GUI you can choose exactly what monitor you have and the graphics card you have too.


its not there

I see where other is and theres a few things I can add but no sign of Screens and Graphics or anything close

---

### Post by coolethan on 2008-11-26
are you using hardy (8.04) or intrepid (8.1) i'm using hardy so i'm unawares of how intrepid is set up but it should be in there, if not under other then somewhere else like system or settings or something. using screens and graphics was how i originally got my resolution fixed, i've never actually installed any drivers for my graphics card at all.

---

### Post by Bobatron on 2008-11-26
> **coolethan said:**
> are you using hardy (8.04) or intrepid (8.1) i'm using hardy so i'm unawares of how intrepid is set up but it should be in there, if not under other then somewhere else like system or settings or something. using screens and graphics was how i originally got my resolution fixed, i've never actually installed any drivers for my graphics card at all.

8.1 so it could be little different, checked around though cant find it anywhere.

Wish I could cause I cant find the drivers anywhere

---

### Post by coolethan on 2008-11-26
you are looking in the edit menu's GUI right.

---

### Post by coolethan on 2008-11-26
did some research, this thread should help you out, if screens and graphics is not there then it is possible to download it. 

```
sudo apt-get install displayconfig-gtk
```


this is the rest of the thread if you wish to read it there are some other solutions in there too.

[http://ph.ubuntuforums.com/showthread.php?p=6176274](http://ph.ubuntuforums.com/showthread.php?p=6176274)

---

### Post by HittingSmoke on 2008-11-27
> **Bobatron said:**
> Command not found and there is no system tools in Applications.


I went onto ATI site and there are no drivers for Radeon 7000 series for Linux, is for XP but not Linux.

The command to run it is simply

```
envyng
```

no envyng-gtk. Try just typing "envyng" into a terminal, or just type envy and press Tab to autofill it in.

---

### Post by Bobatron on 2008-11-27
> **HittingSmoke said:**
> The command to run it is simply

```
envyng
```

no envyng-gtk. Try just typing "envyng" into a terminal, or just type envy and press Tab to autofill it in.


Didnt work, cant find drivers for it myself


I managed to get Screen and grapics working thought after I followed advice in this thread

[http://ph.ubuntuforums.com/showthread.php?p=6176274](http://ph.ubuntuforums.com/showthread.php?p=6176274)

But I cant select my graphics card as an option its just not there and every time I try change resolution it fails


"Please verify the selected devices and configuration." Error when I test it


"The X Server failed it must not be configured well." Error when I try log out after changes


Come to conclusion graphics card just isnt supported by 8.10

---

### Post by thestig_992 on 2008-11-27
Do you have proprietry drivers installed? Go to system > Administration > hardware drivers and it should tell you whether or not ur card is working properly.

Another point with changing the screen resolution is to change the refresh rate as well, i cant seem to use full resolution unless i have 80Hz in intrepid only...maybe you have a similar problem

---

