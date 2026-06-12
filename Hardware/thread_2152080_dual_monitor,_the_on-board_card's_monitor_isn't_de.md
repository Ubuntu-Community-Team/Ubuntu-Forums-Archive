---
title: "dual monitor, the on-board card's monitor isn't detected"
date: 2013-06-06
forum: Hardware
---

### Post by Luis8 on 2013-06-06
I have tried several solutions but nothing works. First of all, I'm using ATI Radeon HD 5400. The first monitor (which works) is connected to the graphic card by DVI, the second monitor (which isn't detected) is connected to the motherboard by VGA. One important point - when I used Windows (yesterday?) the two monitor worked together fine.

[LIST=1]
[*]Followed by the instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installation_via_the_Ubuntu_repositories](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installation_via_the_Ubuntu_repositories). Installed fglrx by writing ```
sudo apt-get install fglrx
```. Then typed fglrxinfo in the Terminal and got:

```
display: 0  screen: 0

``````
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 4.2.11903 Compatibility Profile Context
```
[*]Tried that solution: [http://askubuntu.com/a/281117](http://askubuntu.com/a/281117). I installed:[http://i.stack.imgur.com/JD9li.png](http://i.stack.imgur.com/JD9li.png) and added in Xorg.conf the following line: Virtual 3600 3600.
[*]System Settings > Details > Graphics displays Driver: VESA:JUNIPER
[*]The second monitor isn't detected either by the Catalysit Control Center nor by System Setting > Display.
[*]```
$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] 
```
The meaning is that it knows about the existence of the on-board graphic - Radeon HD 4200 (?).
[/LIST]

[FONT=arial]* Motherboard model is Gigabyte MA785GMT-UD2H, integrated ATI Radeon HD 4200 graphics.[/FONT]

---

### Post by QIII on 2013-06-06
Hello and welcome to the Forums!

Might I ask which version of Ubuntu you are using?

Thanks.

---

### Post by Luis8 on 2013-06-06
Thank you.

I'm using 12.04.2 LTS (just installed..).

---

### Post by QIII on 2013-06-06
Well, you are in for some trouble, unfortunately.

AMD/ATI dropped driver support for the HD 2 - 4xxx drivers for Linux.  The last version of Ubuntu that they will support is 12.04.1 out of the box.  Your dedicated card is fine, for now...

So you'll probably not get that integrated GPU to work unless you can get both working with the default open source driver.

There are folks that have instructions for getting older cards to work for versions after 12.04.1, but those methods are hacks that effectively break your system.  I recommend so strongly against those methods that I won't even suggest them (although someone may come along and point you that way.)

I recommend against those methods because:

1.  As hacks, nobody can be sure what will happen in the future with regard to updates and dependencies.  I have already responded to two threads where the users broke their installations with updates.

2.  12.04.1 is supported for four more years, so you can use that without worries.

My recommendation is to do a fresh install of 12.04.1 and have a good time!

Hate to bear bad news...

Best wishes!

---

