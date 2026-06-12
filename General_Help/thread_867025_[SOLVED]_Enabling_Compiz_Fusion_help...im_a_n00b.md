---
title: "[SOLVED] Enabling Compiz Fusion help...im a n00b"
date: 2008-07-22
forum: General Help
---

### Post by mikedemario17 on 2008-07-22
so i have ubuntu 7.10 gu....and i upgraded to 8.04 and i saw a video for Compiz Fusion and thats what i always wanted in a pc...all tht cool stuff....i think this seems ez enuf to follow but when i click on Enable it says something is not Enabled..? .[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200]("http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200").

---

### Post by f37u5g0d on 2008-07-22
In 8.04 the drivers for nvidia and ati cards is handeled exceptionally well.  For most when you click enable desktop effects it will automatically figure out which driver you need and install it for you, ask you to reboot and it should be working.  A "one-click fix."  Did that not happen for you?

---

### Post by ibuclaw on 2008-07-22
What type of graphics card do you have?

Can you post the output of:
```
sudo lshw -short | grep display
```
in your next post?

Secondly, make sure the right bits are installed for compiz

[LIST]
[*]Check your Restricted Drivers and make sure that it is enabled.
[*]Reboot your system.
[*]Install the correct compiz packages
```
sudo apt-get install compiz compizconfig-settings-manager fusion-icon
```
[*]Press **Alt+F2** and type in:
```
fusion-icon
```
In the run-command bar.
[/LIST]

Then right-click on the applet and enable the features you want.

To make fusion-icon the default whenever you login, run:
```

gconftool-2 -s --type=string /desktop/gnome/applications/window_manager/current /usr/bin/fusion-icon
gconftool-2 -s --type=string /desktop/gnome/applications/window_manager/default /usr/bin/fusion-icon

```

Regards
Iain

---

### Post by mikedemario17 on 2008-07-22
well can u do the step by step of what i need to do like 
example->example->download->
in tht format.plz

---

### Post by zipperback on 2008-07-22
System -> Administration -> Hardware Drivers

Activate the video driver by clicking the check box next to the video driver.

Click close.

Reboot.

Login.

System -> Preferences -> Appearance

Click the Visual Effects tab.

Click the radio button by normal or extra and see if it still gives you that error message. (I have extra selected on mine.)

You will also want to install the compiz config settings manager

System -> Administration -> Synaptic Package Manager

Now use the search function and search for: compizconfig-settings-manager

Click it, and select "Mark for installation".

If it prompts you to mark additional changes, click OK.

Click Apply.

Click File -> Quit

Once that is installed you can access it with the following:
System -> Preferences -> Advanced Desktop Effects Settings

- zipperback
:popcorn:

---

### Post by mikedemario17 on 2008-07-22
> **tinivole said:**
> What type of graphics card do you have?

Can you post the output of:
```
sudo lshw -short | grep display
```
in your next post?

Secondly, make sure the right bits are installed for compiz

[LIST]
[*]Check your Restricted Drivers and make sure that it is enabled.
[*]Reboot your system.
[*]Install the correct compiz packages
```
sudo apt-get install compiz compizconfig-settings-manager fusion-icon
```
[*]Press **Alt+F2** and type in:
```
fusion-icon
```
In the run-command bar.
[/LIST]

Then right-click on the applet and enable the features you want.

To make fusion-icon the default whenever you login, run:
```

gconftool-2 -s --type=string /desktop/gnome/applications/window_manager/current /usr/bin/fusion-icon
gconftool-2 -s --type=string /desktop/gnome/applications/window_manager/default /usr/bin/fusion-icon

```

Regards
Iain
when i go to Restricted Drivers then try to enable it... it says error not enabled...how do i get the name of my graphics card ? I THINK ITS AN 
nVIDIA Geforce something...but tht error poped up on 7.10 and im updating to 8.04 now on my other pc...if it helps its a windows xp...windows xp home edition...Hewlett Packard Pavilion 7955 (P5269A#ABA) PC Desktop ... im useing differnt cd drives and diff. everything ,,,but it still has the org. graphics card

---

### Post by mikedemario17 on 2008-07-22
when i go to System -> Administration -> Hardware Drivers there is nothing in the Hardware Drivers window???

---

### Post by mikedemario17 on 2008-07-22
this is the output....
mike@mike-desktop:~$ sudo lshw -short | grep display
/0/100/1/0                      display     NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
mike@mike-desktop:~$

---

### Post by zipperback on 2008-07-22
Sorry that didn't work for you. I don't have an nvidia chip set. Mine is ATI and that worked for me out of the box.

Perhaps someone else can help you get the nvidia driver installed and working.

- zipperback
:popcorn:

---

### Post by adrien214 on 2008-07-22
> **mikedemario17 said:**
> this is the output....
mike@mike-desktop:~$ sudo lshw -short | grep display
/0/100/1/0                      display     NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
mike@mike-desktop:~$

compiz won-t work on this video card, at least that-s what other threads in the ubuntu and other forums suggest.

---

### Post by ibuclaw on 2008-07-22
Yeah, those cards are good 2D graphics card, but were not built for 3D rendering capabilities. Such as the strain that compiz may put on it.

Sorry.

Regards
Iain

---

### Post by mikedemario17 on 2008-07-22
whats a card i can buy that can handel it? post a link

---

### Post by mikedemario17 on 2008-07-24
yeah..so my graphics card is a 2-d and cant support it....but whats weird is when i installed 7.10 again coz 8.04 is slow as sh*t on my pc and it cant handle 8.04...and i tried to do it just for fun...and no error popped up under restricted drivers when i went to activate the high performince card... so i restarted and all the settings poped up for it.! but when i switched my card to custom...it says it cant be supported... so im just waiting for a new pc to put the hard drive in...

---

