---
title: "11,04 touch pad not working"
date: 2011-04-30
forum: Hardware
---

### Post by Magick93 on 2011-04-30
Hi

I just upgraded my Fujitsu lifebook. Now the touchpad does not work.

Does anyone know how I can fix this?

---

### Post by Magick93 on 2011-05-02
Bump?

Anyone? My laptop is unusable after upgrading.

---

### Post by branaja on 2011-05-02
I have the same problem but don't know how to solve it :(

is your tuchpad working before you log in? :/

---

### Post by branaja on 2011-05-02
try this:

in terminal run this:
> gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

don't know is it temporary or just until you log out but it's working ;)

hope I helped :)

---

### Post by Magick93 on 2011-05-02
> **branaja said:**
> try this:

in terminal run this:


don't know is it temporary or just until you log out but it's working ;)

hope I helped :)

Thanks for the reply. Before the graphical login I dont see any output or prompts, no grub, nothing.

---

### Post by Magick93 on 2011-05-09
I have a 'Live CD' running from a USB stick, but I cannot get my files off the computer. When I navigate to where my files are I get a permission error. I think I used an encrypted file system when I first installed ubuntu on my laptop.

Does anyone know how I can either fix the upgrade so I can use my laptop again, or how I can get my files off it?

---

### Post by Magick93 on 2011-05-10
Does anyone know of there is a payed support option?

No one on this forum seems to be able to offer assistance unfortunately.

---

### Post by Ashfaque on 2011-05-10
Try navigating to the mouse options with your keyboard and check.
Also, maybe your touchpad's physically disabled, like I have a button right above mine that disables it.

---

### Post by Magick93 on 2011-05-12
> **Ashfaque said:**
> Try navigating to the mouse options with your keyboard and check.
Also, maybe your touchpad's physically disabled, like I have a button right above mine that disables it.

I dont think I can navigate using the keyboard. I have tried all sorts of combinations but - tab etc, but I dont get anything. 

Are there any keyboard shortcuts for the new unity interface?

---

### Post by aeronutt on 2011-05-12
> **Magick93 said:**
> I dont think I can navigate using the keyboard. I have tried all sorts of combinations but - tab etc, but I dont get anything. 

Are there any keyboard shortcuts for the new unity interface?

[http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html](http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html)
[http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts](http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts)

---

### Post by Pihraija on 2011-08-07
Hi!

I have a similar problem, when installing Ubuntu 11.04 on my HP Pavilion DV7-1095 my keyboard and mousepad stopped working.. It worked fine when setting up the keyring password and all that, but when I'm to type in what my user account, computer name and password should be, neither the keyboard or the mousepad is working! So I tried connecting a USB-mouse and a USB-keyboard, and they both work!

Anyone have a solution for this? :)

---

### Post by aaitken1998 on 2011-08-07
If you installed Ubuntu 11.04 with mouse/keyboard attached then that could be your problem otherwise i don't know.

By the way, to get your files of the folder without the permissions open a terminal and type the following 

```
 chmod 770 -R / 
```but this command will change the permissions of ALL of your files so you can backup whatever you want to.

Then re-installation will most likely be the best way.

PS I'm speaking from experience :P

---

### Post by Pihraija on 2011-08-07
Update: Seems that the problem was only occuring for the setup program. When I rebooted and the login screen showed up, everything was back to normal, keyboard and mousepad working!

Just a little glitch I s'pose..

Take care out there!

---

