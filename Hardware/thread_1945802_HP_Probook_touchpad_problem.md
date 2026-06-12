---
title: "HP Probook touchpad problem"
date: 2012-03-23
forum: Hardware
---

### Post by dhack on 2012-03-23
Hello.

I'm starting this thread because I have some problems with ubuntu 11.10 x64 on my HP Probook 4530s laptop. Among this problems is problem with touchpad, this is one of the main problems, so that's why i doing that.
I asked about that on askubuntu, ubuntu-ru, LOR (professional russian forum about linux), superuser, etc. but problem is still not solved.

When I bought my laptop (about 2.5 months ago) SLED (Suse Linux Enterprise Desktop) was installed on it. And on that system everything was ok: discrete graphics worked good as well as touchpad and others. 
Then I decided to install ubuntu 11.10 x64 and windows 7 (dualboot). After that i booted up in ubuntu. First of all the fans worked very loudly and temperature was on cpu etc was pretty big (about 52 C) even if i didn't do anything. Then I realized that the problem is in my discrete video card (Radeon HD 6490M) and I turned off it (I thought at that moment: "First I will fix other problems and only then I'll fix problems with discrete graphics"). 
So now the main problem is in my touchpad. 
First of all - I have a LED in upper left corner and double touching in this field must enable\disable my touchpad. In windows 7 this feature works properly, in SLED this thing worked too. How to fix that? I dont know. First I tried to install SLED driver, but that driver was a *.rpm file, so I converted it and installed, but didn't help. Now I can disable\enable my touchpad only with small bash-script, which uses 
```
synclient TouchpadOff = 1
```command.
The other problem is that touchpad is "super sensetive". Because in windows it's comfortable to work with enabled touchpad. If I accidentally touch the touchpad with my wrist during typing - the cursor isn't moving, only when I touch with finger it moving.
In ubuntu even if I accidentally touch my touchpad with my wrist - the cursor moves and "clicks". How to fix that? (until this time I just use syndaemon -i -2 -t).
I also enabled "Disable touchpad when typing" in "Mouse and touchpad", but either way it didn't change anything.

Please help if you know how to fix that.
Thanks.

P.S.: Sorry if there any mistakes in my english.

---

### Post by razedafear on 2012-03-24
I have the same problem with the touchpad. The on and off feature for touch pad does not work on Ubuntu 10.10. Also the touchpad behaves weird if i accidently touch it with the wrist.

Plus i have two more issues:

1- My graphics behave weird when i move the windows and get rough and distorted edges. Checked in additional drives but no drives were found there. The Hp support site lists drives for Open SUSE i guess bt not for ubuntu10.10

2- My wifi get real slow on ubuntu but works fine in win7. 

HP Probook 4530s
i7 2630QM QUad core,
8GB, 500 GbHDD, 
Intel HD3000 Graphics.

PLease help

---

### Post by dhack on 2012-03-24
> Also the touchpad behaves weird if i accidently touch it with the wrist.
Yes, this really annoying when working\typing something.

> Plus i have two more issues:
1- My graphics behave weird when i move the windows and get rough and  distorted edges. Checked in additional drives but no drives were found  there. The Hp support site lists drives for Open SUSE i guess bt not for  ubuntu10.10

The HP support site list drivers for Suse Linux Desktop (not for openSUSE). You should to disable discrete graphics in BIOS (EFI) and work on your internal graphics.
(in ubuntu 11.10 it should help)

---

### Post by razedafear on 2012-03-29
> **dhack said:**
> Yes, this really annoying when working\typing something.
Any fix for this ?

The HP support site list drivers for Suse Linux Desktop (not for openSUSE). You should to disable discrete graphics in BIOS (EFI) and work on your internal graphics.
(in ubuntu 11.10 it should help)
This means everytime i decide to boot up Ubuntu i first have to go in BIOS and disable discreet BIOS ? and den enable it back when i want to boot win 7? . it is one hell of a task.. :(

---

### Post by dhack on 2012-03-29
> This means everytime i decide to boot up Ubuntu i first have to go in  BIOS and disable discreet BIOS ? and den enable it back when i want to  boot win 7? . it is one hell of a task.. :sad:Actually- yes.

In fact can configure your discrete graphics, it's possible, but not easy (some guys, which are exprerts in linux did this). But for what do you need to enable discrete graphics every time when you want to boot into windows? Sometimes you can enable it if you want to play games on windows, but if you don't - you can use internal graphics. Also discrete graphics needs more power so if you work from battery then your charge will fall faster.

Conclusion: 
If you work from battery - internal graphics preferable.
If you want to play games on windows (working from the socket, not from battery) - discrete graphics would be better decision.


P.S.: Does anybody know how to solve my problem?

---

### Post by siepo on 2012-04-02
I have a probook with only integrated graphics, which has been completely trouble-free. I tamed the touchpad with a script with a bunch of synclient commands: 

synclient TapButton1=0 
synclient TapButton2=0 
synclient TapButton3=0

together deactivate clicking with the touchpad - but you can still click with the touchpad buttons.

A command

synclient PalmDetect=1

can also be useful.

synclient -l

gives you a list of all settings which are in effect.

I called this script in .xsession in my home directory, but I am not sure whether this would work with a normal graphical login. Otherwise, you could still call it manually.

I recall mention of patches for the synaptics driver to enable the on/off double-tap but I didn't investigate further since the touchpad works fine for me as it is.

---

### Post by dhack on 2012-04-03
Thanks for advice, but unfortunately it didn't help... PalmDetect was zero before I've configured it. I set the value to 1, but nothing has changed..

---

### Post by Caelo on 2012-08-02
> **dhack said:**
> Thanks for advice, but unfortunately it didn't help... PalmDetect was zero before I've configured it. I set the value to 1, but nothing has changed..
Hi, I'd like to add to this that, at least for me, it does work. However to have the palm detection work more like it does on Windows you need to set PalmMinZ to a more sensable value like 5.

---

