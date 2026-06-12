---
title: "How to Create A Keyboard Shortcut For Mute Microphone"
date: 2016-11-08
forum: Hardware
---

### Post by Erdem on 2016-11-08
Hello
I was looking for a solution for keyboard shortcut to mute my Logitech C310 webcam microphone and i finally figure out how to do it. 8-)
Just want to share here if anyone looking for a solution. 

Probably it will work for all kind of microphone

First open System Settings and then go to Keyboard Setting, click Shortcuts tab

Under the Custom Shortcuts add a new one and name it Toggle Microphone
See screenshot below.

In command add this
```
amixer -c 1 sset Mic toggle
```
&#304;f you want a desktop notification you can type 
```
amixer -c 1 sset Mic toggle && amixer get -c 1 Mic | grep '\[off\]' && notify-send "MIC switched OFF" || notify-send "MIC switched ON"
```
You can use it for internal microphone too but you have to figure it out what is the name of your microphone
For that you can see all list below command and pick your microphone
```
amixer contents
```
If your mic is not a USB connected one remove -c 1 in the command.
Hope it will be usefull.

---

