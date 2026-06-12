---
title: "I can't set screen resolution above 800x600"
date: 2009-10-21
forum: Hardware
---

### Post by perstromgren on 2009-10-21
I have an eee 901 (with its tiny screen) and just bought a separate LCD screen. I tried to set the screen resolution with gnome-display-properties, but the maximum in the drop-down menu is 800x600 pixel. How can I change this?

I checked the xorg.conf, but it is more or less empty.

This is on 9.04

Per.

PS. My other 9.04 machines ("normal" size laptops) have a lot more alternatives for screen resolution.

SOLVED: The trick is to uncheck "Mirror screens".

---

### Post by TheStroj on 2009-10-21
The most common problem is that you don't have graphics drivers installed. 
You can try and go to 'System - Administration - Hardware Drivers' to see if there are any drivers available for you graphics card.

---

### Post by perstromgren on 2009-10-21
> **TheStroj said:**
> The most common problem is that you don't have graphics drivers installed. 
You can try and go to 'System - Administration - Hardware Drivers' to see if there are any drivers available for you graphics card.

Hm... How do I know what my graphics card is? 

But thanks!

---

### Post by TheStroj on 2009-10-21
> **perstromgren said:**
> Hm... How do I know what my graphics card is? 

But thanks!

by typing lspci in terminal, you can find the name of your graphics card.
You should find a long output, but there will be something like this:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)

I guess you have Intels graphics card (EEEs use Intels I think).

---

### Post by cenzorrll on 2009-10-21
> **perstromgren said:**
> Hm... How do I know what my graphics card is? 

But thanks!

your best chance is to look up your model of laptop on the ASUS website and see what it says, it'll be under something like video chipset, or graphics processor, or some other combination of the two.

I'm pretty sure (say 90%) that any atom processor only comes with specific intel components, so chances are you have one of the intel graphics processors. it'll be called something like intel GMA-something or other


back in the day (read: 2006) I had some major problems getting my intel graphics card to display on an external screen in ubuntu. I doubt there's still issues with that, but as EEE's are relatively new and designed to be small I don't think there's been major effort put into making external monitors work perfectly, as in a higher resolution than the tiny screen can support.

you may try searching other threads or forums to see if anybody has been able to get a monitor working at higher resolutions on an EEE.

---

### Post by j_a_c_k_s_o_n on 2009-10-22
You may try these, but I did only in my compaq.

Setting Compaq C700 series Screen Resolution to 1280x800 in Ubuntu 9.04
Here's the procedures how to configure screen resolution.. do the update only if you have intel graphics else proceed to step 2.

Step1:
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel
sudo reboot


then backup and edit your xorg.conf by:

Step2:
sudo gedit /etc/X11/xorg.conf
next save as xorg_backup.conf
sudo gedit /etc/X11/xorg.conf


upon opening the xorg.conf like this

Section "Monitor"

    Identifier    "Configured Monitor"

EndSection



Section "Screen"

    Identifier    "Default Screen"

    Monitor        "Configured Monitor"

    Device        "Configured Video Device"

    SubSection "Display"

        Virtual    2048 779

    EndSubSection

EndSection



Section "Device"

    Identifier    "Configured Video Device"

EndSection



then edit the xorg.conf like this:


Section "Monitor"

    Identifier    "Configured Monitor"

EndSection



Section "Screen"

    Identifier    "Default Screen"

    Monitor        "Configured Monitor"

    Device        "Configured Video Device"

    SubSection "Display"

        Modes &#8220;1024x768&#8221; &#8220;1280x800&#8221;
        Virtual    2048 779

    EndSubSection

EndSection



Section "Device"

    Identifier    "Configured Video Device"

EndSection


next click save and on terminal type the following:

Step3:
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot


finally you got a widescreen resolution of 1280x800 in display preferences..

---

### Post by perstromgren on 2009-10-22
Thanks,  j_a_c_k_s_o_n, I'll try that on my 901!

Per.

---

### Post by perstromgren on 2009-10-22
> **perstromgren said:**
> Thanks,  j_a_c_k_s_o_n, I'll try that on my 901!


... but it did not work, I'm afraid! In fact, "dpkg-reconfigure -phigh xserver-xorg" destroys the xorg.conf edit, and resets it back t its default. I tried without dpkg-reconfigure but that turned my machine unusable; the system said it could not use my xorg.conf, and it had to reset it back to failsafe (default) state.

Anyone else, that can help me out on this?

Per.

---

### Post by perstromgren on 2009-10-25
I have it working now, but don't know exactly what I have done! I think that unchecking "Mirror screens" is the trick.

My external monitor is an old Samsung Syncmaster 172b with the native resolution 1024x768.

Per.

---

### Post by elhauk on 2009-11-10
This is great Per. Maybe you should set the thread as solved and write your answer in teh first post as others won't need to try the editing of the xorg file option when all you need is to turn off "mirror screens"

---

### Post by perstromgren on 2009-11-10
> **elhauk said:**
> This is great Per. Maybe you should set the thread as solved and write your answer in teh first post as others won't need to try the editing of the xorg file option when all you need is to turn off "mirror screens"

Thanks for pointing that out. I have done just that now.

Per.

---

