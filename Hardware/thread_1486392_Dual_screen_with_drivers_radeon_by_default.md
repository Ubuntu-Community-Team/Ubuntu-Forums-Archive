---
title: "Dual screen with drivers radeon by default"
date: 2010-05-17
forum: Hardware
---

### Post by Hizoka on 2010-05-17
Hi !

Sorry for my english, I'm french guy.

I'm lost with the drivers radeon and my screens...

2 screens :
 - A : PC
 - B : TV

1 GPU : hd4850 (asus eah4850, ddr3 512mb) with 2 output
 - 1 : DVI (but view like VGA-0)
 - 2 : DVI (DVI-0)

A is in 1.
B is in 2.

I would like :
 - A : 1280*1024
 - B : Clone of A and 1280*1024

Xrandr :
```
hizoka@hizo-pc:~$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1     70.1  
DIN disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9 
```
With drivers ati.run, no problems... (1280*1024 for my 2 screens but I don't like them...)

I have try [update kernel and drivers]("http://ubuntuforums.org/showthread.php?t=1238129&highlight=ati") but  unchanged...

But if I try :
 - Resolution 1280*1024 in A, Resolution 1024*768 in B
 - I exchange A and B (A is in 2, B is in 1)
 * A is in 2 : resolution at 1024*768
 * B is in 1 : resolution at 1280*1024
 - Change resolution of A in 1280*1024
 - validation
=> My screens are both in 1280 * 1024 and they work

Xrandr :
```
hizoka@hizo-pc:~$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1     70.1  
DIN disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1     70.1
```


but after reboot (bouhouhouuu) :
 - Resolution A : 1024*768
 - Resolution B : 1024*768


Kernel : 2.6.34-020634rc7-generic
xserver-xorg-video-ati : 1:6.3.99

anyone have a good idea for this problem ?

Thank

---

### Post by Hizoka on 2010-05-20
up because is verry impeding.

Thx

---

### Post by Hizoka on 2010-05-22
After search ++++,

I've got a solution :
```
# cvt with selected resolution
h=1024
l=1280
infos=$(cvt ${l} ${h})
infos=${infos##*Modeline }

# Add new mode
xrandr --newmode ${infos}

# Add this mod for DVI-0
xrandr --addmode DVI-0 ${l}x${h}

# Choice of this mode
xrandr --output VGA-0 --mode ${l}x${h} --output DVI-0 --mode ${l}x${h}
```
it's ok.

But I would like this on boot, [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) :
 - Use ~/.xprofile : I don't know why but it does not work.
 - Use /etc/kde4/kdm/Xsetup : works but my KDM has a problem, instead of an image stretched to my resolution, I have images that are repeated in the background
 - Use autostart : I don't know why but it does not work.

I search how launch this commands before KDM for solve this problem...

---

