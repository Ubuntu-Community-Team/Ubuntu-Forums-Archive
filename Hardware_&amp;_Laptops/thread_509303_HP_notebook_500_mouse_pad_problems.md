---
title: "HP notebook 500 mouse pad problems"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by fishvetmj on 2007-07-25
Hi. I'm completely new to Linux and Ubuntu and have just loaded Ubuntu 7.04 onto my laptop using the alternate CD (I couldn't get the live CD to run), so there is dual booting with XP (until I stop being so nervous!). I'm really pleased with the result. However, Ubuntu does not recognise or run my laptop's mouse pad, so I can only work with a USB mouse at the moment. Anyone know how to fix this problem?

Many thanks, great product, great website.

---

### Post by NickArgyle on 2007-07-25
My touchpad didnt work properly on my hp until I reconfigured xorg and switched from PS/2 (I think) to the Explorer option.

Type the following into the terminal "sudo gedit /etc/X11/xorg.conf"
and see if you have a line similar to the following.
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

---

### Post by fishvetmj on 2007-07-25
I've typed in the line you suggested but get a message saying "/ is a directory, please check that typed the location correctly and try again". The xorg.conf window is empty. Should I type in the code you have mentioned?

---

### Post by NickArgyle on 2007-07-25
did you put the quotation marks in? Youre not supposed to.

---

### Post by fishvetmj on 2007-07-25
No. I've tried typing in the address for the file several times, but keep getting the same message.

---

### Post by NickArgyle on 2007-07-25
see if you can manually navigate to the file. Also the file address is case sensitive so X in X11 is capitalized.

---

### Post by fishvetmj on 2007-07-25
OK, have found the relevent file manually, and it has exactly the code you mentioned in it. How should I modify it????

---

### Post by NickArgyle on 2007-07-25
Check that the following code has explorer instead of IM under protocol

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

---

### Post by fishvetmj on 2007-07-25
Have changed the line "protocol" to "ExplorerPS/2" from "ImPS/2", but when I try and save the altered file I get the message "The file "etc/X11/xorg.conf" is read only", and when I try and replace it with the modified file I get the message "Could not save the file /etc/X11/xorg/conf you do not have the necessary permissions to save the file. Please. Check that you typed the location correctly and try again."

Now I'm lost... it's my own personal laptop, I instanned Ubuntu yesterday, so I must be the administrator... there's no-one else to log in as, I'm the only user.

---

### Post by NickArgyle on 2007-07-25
To edit these files you have to have administrator privaliges. See if you can just type "sudo gedit" into the terminal. That should open up the root (admin) version of the text editor. Then locate the file using the text editor, edit it and then you should be able to change it. Make a backup of the file as well.

---

### Post by fishvetmj on 2007-07-25
When I type "sudo gedit" into the terminal, I get a window called "Unsaved document 1 - gedit" with a blank screen. Try as I might, I can't get the text editor to find the file "/ etc/X11/xorg.conf" for me to edit... I can only find this file manually and then it won't allow me to alter it.

I'm lost!

---

### Post by NickArgyle on 2007-07-25
That's very strange. My advice would be to reconfigure X. type in the terminal "sudo dpkg-reconfigure xserver-xorg" then follow the automated configuration. Make sure you know what video card driver you are using.

---

### Post by fishvetmj on 2007-07-25
Sorry... I'm now right out of my depth because I have no idea what video card driver I'm using... is there an easy way to find out???

---

### Post by NickArgyle on 2007-07-25
What video card do you have, Ati, Nvidia, intel?

---

### Post by fishvetmj on 2007-07-25
The processor is an Intel Celerom M 350M. That's about the limit of my knowledge. You're talking to a real novice here!!!

---

### Post by fishvetmj on 2007-07-25
Have to go offline now... many thanks for all your efforts, will continue to try and solve this problem and let you know if I get anywhere.

---

### Post by homogenizer on 2007-08-16
Hello there,

Try the simpliest way.  I too have an HP 500 notebook and I tried Mepis 6.5, Ubuntu and Kubuntu with it.

From a usual install of Ubuntu/Kubuntu Fiesty Fawn, Allow the Ubuntu's Synaptic Updater/ Kubuntu's Adept Manager to "Auto Update" or Patch your system.  After patching restart your Linux box and you will notice that your Touchpad is working.  I used this method to easily solve the problem.  I noticed that the Ubuntu/Kubuntu patched seldom freezes with my TS-L632D with HH15 firmware.

---

### Post by homogenizer on 2007-08-16
By the way, As of 8-16-2007 my Kubuntu from standard install had 107++ updates so Full Patching may take some time.  It took me 1 hour on my slow DSL.

---

