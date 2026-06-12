---
title: "Screen Brightness"
date: 2008-05-06
forum: Hardware
---

### Post by chuckado on 2008-05-06
My screen brightness is set a maximum and i cannot find a way to turn it down. I have tried my key combinations, ddccontrol and the brightness applet.  None of these seem to work.  I am using a Gateway MX 6959 with an Intel 945 mobile chip set.  Thank you for any help.

---

### Post by chuckado on 2008-05-06
bump

---

### Post by acron1 on 2008-05-06
I think you can go to System-> Preferences-> Advanced Desktop Effects Settings and do it there.
Good luck

---

### Post by chuckado on 2008-05-07
What do i do in the compiz config

---

### Post by atomkarinca on 2008-05-07
If you have an nVidia card you can use nvidia-settings. If you don't have it installed then

```
sudo apt-get install nvidia-settings
```

After installation type "nvidia-settings" without the quotes, under "X Screen 0 > X Server Color Correction" decrease the Gamma value.

---

### Post by chuckado on 2008-05-07
i have an Intel integrated graphics card

---

### Post by atomkarinca on 2008-05-07
Then from a command line (Applications > Accessories > Terminal) type

```
xgamma -gamma 0.75
```

Just change 0.75 to your liking. You can add this to your launcher: System > Preferences > Sessions and add that line.

---

### Post by chuckado on 2008-05-07
that only changes the color ratio it does not bring down the brightness of my screen

---

### Post by Zorael on 2008-05-07
> **atomkarinca said:**
> Then from a command line (Applications > Accessories > Terminal) type

```
xgamma -gamma 0.75
```

Just change 0.75 to your liking. You can add this to your launcher: System > Preferences > Sessions and add that line.
Will this make the screen itself go darker or merely send a darker picture to be drawn? I mean, laptops generally have a hardware brightness setting. I can modify mine through KDE's power manager. But lowering xgamma does not lower this setting; it merely further darkens things while keeping the LCD backlight at the same level.

---

### Post by atomkarinca on 2008-05-07
> **Zorael said:**
> Will this make the screen itself go darker or merely send a darker picture to be drawn? I mean, laptops generally have a hardware brightness setting. I can modify mine through KDE's power manager. But lowering xgamma does not lower this setting; it merely further darkens things while keeping the LCD backlight at the same level.

I'm not using a laptop so I don't know if it works for laptops but that *is* the only method I know so sorry I couldn't help :)

---

### Post by Whiffle on 2008-05-07
Try 

xbacklight -set 50

to change it to 50%.

---

### Post by chuckado on 2008-05-07
this did not change anything but thx anyway

---

### Post by Whiffle on 2008-05-07
Hmm, that app was designed for intel chipsets.  I'd play around with it.

---

### Post by chuckado on 2008-05-07
like what should i try

---

### Post by Catalyst2Death on 2008-05-07
the command you're looking for is:

```
# echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
```

replace 50 with a number between 37 and 100

usually I use 37,50 or 100

NOTE: you MUST be root to use this command, sudo will NOT work so:

```
$ sudo -s
# echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
# exit
$

```

this was stolen from:

[http://www.ubuntu1501.com/2007/12/backlight-brightness-fix.html](http://www.ubuntu1501.com/2007/12/backlight-brightness-fix.html)

I use this command regularly on my laptop... When you forget it (which I always do) you can find it easily using:

```
$ history | grep brightness
```

I would really like to be able to use my fn brightness keys on the keyboard, and they work in other distributions so I think its a kernel problem... I would like to hack it, but unfortunately my skills are not quite there yet...

---

### Post by chuckado on 2008-05-07
that worked great thx for the help

---

### Post by Zorael on 2008-05-08
My /proc directory architecture seems different.
```
zorael@sunspire:~$ ls /proc/acpi/video
GFX0
```
No VGA directory. :<

---

### Post by Catalyst2Death on 2008-05-08
thats odd... whats in the GFX0 folder?  I'm assuming its a folder...

---

### Post by Zorael on 2008-05-08
```
zorael@sunspire:/proc/acpi/video/GFX0$ ls -l
total 0
dr-xr-xr-x 2 root root 0 2008-05-08 19:28 DD01
dr-xr-xr-x 2 root root 0 2008-05-08 19:28 DD02
dr-xr-xr-x 2 root root 0 2008-05-08 19:28 DD03
dr-xr-xr-x 2 root root 0 2008-05-08 19:28 DD04
dr-xr-xr-x 2 root root 0 2008-05-08 19:28 DD05
-r--r--r-- 1 root root 0 2008-05-08 19:28 DOS
-r--r--r-- 1 root root 0 2008-05-08 19:28 info
-r--r--r-- 1 root root 0 2008-05-08 19:28 POST
-r--r--r-- 1 root root 0 2008-05-08 19:28 POST_info
-r--r--r-- 1 root root 0 2008-05-08 19:28 ROM
zorael@sunspire:/proc/acpi/video/GFX0$ cd DD01
zorael@sunspire:/proc/acpi/video/GFX0/DD01$ ls
brightness  EDID  info  state
zorael@sunspire:/proc/acpi/video/GFX0/DD01$ cat brightness
<not supported>
```
I tried cat brightness on all DD0* folders, and system locked up when doing it on DD05's, heh. All said <not supported>.

---

### Post by Catalyst2Death on 2008-05-08
thats odd, I'm not sure... I would try the command anyway and see if you can't get a response, but only if your feeling gutsy... I mean I don't want to suggest that you break it, but I would try the command anyway.

Maybe someone better versed in the acpi setup could help here?

---

### Post by Zorael on 2008-05-09
The DD0 directories weren't of any help, but I explored the [FONT="Courier New"]/proc/acpi[/FONT] directory structure and quickly found an acer-specific section.
```
zorael@sunspire:~$ ls -l /proc/acpi/acer
total 0
-rw-r--r-- 1 root root 0 2008-05-09 14:21 bluetooth
-rw-r--r-- 1 root root 0 2008-05-09 14:21 brightness
-rw-r--r-- 1 root root 0 2008-05-09 14:21 interface
-rw-r--r-- 1 root root 0 2008-05-09 14:21 threeg
-rw-r--r-- 1 root root 0 2008-05-09 14:21 version
-rw-r--r-- 1 root root 0 2008-05-09 14:21 wireless
```
The brightness has an interval between 0 and 15, and as expected, I can toggle bluetooth and wireless here, as well.
```
root@sunspire:/proc/acpi/acer# echo 1 > bluetooth
         *<blue led goes blue!>*
root@sunspire:/proc/acpi/acer# echo 1 > wireless
         *<orange led goes orange!>*
```
Time to make some eth0 up/down scripts! :>

---

### Post by priegog on 2008-05-17
> **Zorael said:**
> 
The brightness has an interval between 0 and 15, and as expected, I can toggle bluetooth and wireless here, as well. Hi, Dumb question, but how did you explore the individual "files"? I also do not have a VGA folder, but I can find a brightness file buried deep in the directory tree and would like to know how to find out the intervals and such. Thanks :)

---

### Post by Zorael on 2008-05-18
> **priegog said:**
> Hi, Dumb question, but how did you explore the individual "files"? I also do not have a VGA folder, but I can find a brightness file buried deep in the directory tree and would like to know how to find out the intervals and such. Thanks :)
Well, the files are text files* and as such you can view them and write to them in your text editor of choice, be it either Gedit, Kate, Mousepad, nano, **cat**, etc. I navigated to the directory, made myself root with '[FONT="Courier New"]sudo su[/FONT]', then did '[FONT="Courier New"]echo 15 > brightness[/FONT]' to make it easy-ish.

As for the intervals; I just set the brightness to max using my Fn+left arrow shortcut and see what the [FONT="Courier New"]brightness[/FONT] file ended up saying.

Noteworthy is that if you try to edit the file and make the number '16', it refuses to save. As such, you could (save your work and) start with making it 10, then 20, then 30, and by trial and error find out where the limit is. At least this was the case for me; your system may well hard-lock.

*: Not really "files", since everything under /proc just pretends to be files. Difficult to explain. Virtual file system thingie.

---

### Post by priegog on 2008-05-18
Thanks a bunch, I'll give that a try. 
> **Zorael said:**
> *: Not really "files", since everything under /proc just pretends to be files. Difficult to explain. Virtual file system thingie.Oddly enought I do know this little fact about the architecture of UNIX, the fact that every single thing must be represented in teh filesystem.

Edit: I just tried doing that, but when I did "nano /proc/acpi/video/VGA/LCD/brightness" (under root), all that was inside the file was ```
<Not Supported>
``` Any ideas? Am I doing it right?

---

