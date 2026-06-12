---
title: "How to disable laptop internal keyboard"
date: 2011-01-09
forum: Hardware
---

### Post by Abhijit Navale on 2011-01-09
I am using external usb keyboard. I want to disable laptop's internal keyboard using software.

I know that i can just remove the internal keyboards wire and disconnect it physically, but i wanted to disable it using software so that later I can enable it by just executing a command in terminal easily. I am talking about disabling the keyboard and NOT the keyboard layout.

I am using 64 bit Ubuntu Lucid Lynx.:confused:

---

### Post by JunCTionS on 2011-08-31
Hi, I wanted to clean my laptop's keyboard without having to go through all the trouble of shutting down.

Be aware, I was stuck for a while constant keypress of Enter, and had to do a long workaround to get my keyboard back.

But it was all done with xinput and based [on this page here]("http://wpkg.org/Disable_/_enable_keyboard_and_mouse_in_Linux").

Short version:
to know the id number of each device connected to you computer do:
```
xinput --list
```
you will see both virtual core keyboard and mouse, and in them several devices. you cannot disable the core keyboard (which is good) so take note of any other keyboard id (in my case I had more than one, so test each).

let's say the id is 11, so to reenable the keyboard (as with my case that I only had the laptop's keyboard) have this text on a gedit 

> xinput set-int-prop 11 "Device Enabled" 8 1


so you can copy/paste it with your mouse.

and to disable:
> xinput set-int-prop 11 "Device Enabled" 8 0

note that pressing enter and with the device loosing communication with the computer, it will not receive the "unpressed" signal, so you might be left with a constant ENTER key that will follow you around.

Being unable to access my computer through ssh (and not realizing I could have just plugged in a usb keyboard), I found that this keypress was cleared by opening the shutdown dialog.

Good luck!

---

### Post by Renosam on 2011-09-14
> **JunCTionS said:**
> Hi, I wanted to clean my laptop's keyboard without having to go through all the trouble of shutting down.

Be aware, I was stuck for a while constant keypress of Enter, and had to do a long workaround to get my keyboard back.

But it was all done with xinput and based [on this page here]("http://wpkg.org/Disable_/_enable_keyboard_and_mouse_in_Linux").

Short version:
to know the id number of each device connected to you computer do:
```
xinput --list
```
you will see both virtual core keyboard and mouse, and in them several devices. you cannot disable the core keyboard (which is good) so take note of any other keyboard id (in my case I had more than one, so test each).

let's say the id is 11, so to reenable the keyboard (as with my case that I only had the laptop's keyboard) have this text on a gedit 


so you can copy/paste it with your mouse.

and to disable:


note that pressing enter and with the device loosing communication with the computer, it will not receive the "unpressed" signal, so you might be left with a constant ENTER key that will follow you around.

Being unable to access my computer through ssh (and not realizing I could have just plugged in a usb keyboard), I found that this keypress was cleared by opening the shutdown dialog.

Good luck!

Hi there. 

I just used this to disable my internal Keyboard. and its works but when i restart the system its enabled again, is there anyway to turn it off for good ?

---

### Post by JunCTionS on 2011-09-14
There are several ways to run a command at startup.

You can try just adding the command at the end of your /home/user/.bashrc file. Also you can just add your command in System>Preferences>Startup Applications (if you're using Ubuntu and not Kubuntu or Xubuntu, etc.)

But this will happen after you login and only for your user. If for some reason you want this to happen even before that, you can run an init.d script. This is explained here:[ http://ubuntuforums.org/showpost.php?p=6995332&postcount=3]("http://ubuntuforums.org/showpost.php?p=6995332&postcount=3")

---

