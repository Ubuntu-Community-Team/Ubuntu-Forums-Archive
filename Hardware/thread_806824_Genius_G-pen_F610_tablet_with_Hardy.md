---
title: "Genius G-pen F610 tablet with Hardy"
date: 2008-05-25
forum: Hardware
---

### Post by Alexstone on 2008-05-25
In a decided departure from the usual tone of challenges and problematic issues with a new build, i've had a great time so far, with a relatively painless install, and general usage. (Ubuntustudio hardy 64bit)
My compliments to the Ubuntu and Studio teams, for (at least for me) a good build, that works well, with little hassle. Well done chaps.

And that extends to my latest addition to Parchment Studios, that of a Genius G-pen F610 tablet. I bought this to test tablet use in general,but more specifically, to test 'writing' notes into mscore, Ardourmidi, etc..

It works, and well. I can't enthuse enough about the speed i've picked up already.

I have but one question.

This particular tablet has a shedload of hotkeys on three sides, and i'd really like to use em, and kill off the damn mouse, once and for all. Between the qwerty and the tablet, i'm determined to put the nasty little ache inducing rodent out of business, and i'm nearly there.

Does anyone know how i could achieve this?

Thanks again to the Ubuntu teams. You did good. (imho)

Alex.

:)

---

### Post by Mishootka on 2008-05-27
Hello, Alex.

Coud you please expain to me how did you get this thing (G-pen f610) to work?

I tried to calibrate it under the Ubuntu Hardy, but had no success.

After your post I upgraded to Ubuntu Studio 8.04 x64 (as you have), but had the same result.

Tablet works, but pretty bad:
1. it seems that it is recognised by the system as a mouse rather than a tablet
2. i can not see it in GIMP
3. pressure signal is ignored
4. the cursor has a very limited area of movement not the whole screen.
5. the editing of xorg.conf reverts to the initial state after restarting the system.

Thank you.

-----------
Update.

Everything works ok for me now. That's how i did it:

```
Create file
[code]sudo gedit /etc/udev/rules.d/20-medion-MD85637.rules
```...add line 
```
KERNEL=="event*", SYSFS{idProduct}=="0031", SYSFS{idVendor}=="172f", SYMLINK+="input/tablet", MODE=="0666"
```...open corg.conf
```
sudo gedit /etc/X11/xorg.conf
```Insert this after the InputDevice "Configured Mouse" section:

```

Section "InputDevice"
          Identifier "Tablet"         
         Option "Name" "WALTOP Slim Tablet"
         Driver  "wacom"
         Option  "Device" "/dev/input/tablet"
         Option          "SendCoreEvents" "true"
         Option  "Type"   "stylus"
         Option  "USB"    "on"
         Option  "Mode" "Absolute"
         Option  "TopX"          "0"
         Option  "TopY"          "0"
         Option  "BottomX"       "10000"
         Option  "BottomY"       "6250"
         Option  "MaxX"          "10000"
         Option  "MaxY"          "6250"
EndSection

```Inset this into the ServerLayout section:

```

InputDevice     "Tablet" "SendCoreEvents"

``````
sudo apt-get install wacom-tools
```CTRL+ALT+BACKSPACE to resatart Xserver.
[/code]If it doesn't work try this one:

```
Create file
[code]sudo gedit /etc/udev/rules.d/20-medion-MD85637.rules
```...add line 
```
KERNEL=="event*", SYSFS{idProduct}=="0031", SYSFS{idVendor}=="172f", SYMLINK+="input/tablet"
```...open corg.conf
```
sudo gedit /etc/X11/xorg.conf
```Insert this after the InputDevice "Configured Mouse" section:
```

Section "InputDevice"
         Identifier "WALTOP Slim Tablet"
         Driver  "wacom"
         Option  "Device" "/dev/input/tablet"
         Option  "Type"   "stylus"
         Option  "USB"    "on"
         Option  "Mode" "Absolute"
         Option  "TopX"          "0"
         Option  "TopY"          "0"
         Option  "BottomX"       "10000"
         Option  "BottomY"       "6250"
         Option  "MaxX"          "10000"
         Option  "MaxY"          "6250"
 EndSection

```Inset this into the ServerLayout section:
```

       InputDevice     "WALTOP Slim Tablet" "AlwaysCore"

```Installing wacom-tools:

```
sudo apt-get install wacom-tools
```CTRL+ALT+BACKSPACE to resatart Xserver.
[/code]

---

### Post by DataMatrix on 2008-08-31
Yes, I'm also interested in this topic. I intend to buy that tablet (Genius G-Pen F610), but I'm unsure if it'll run with my Ubuntu 8.04.1 Hardy releace (32bit) and I don't have money to waste. Can you give us some clues about this?

PS: I don't need the hotkeys on the tablet, just the pen-thing working propperly.

---

### Post by Amazona aestiva on 2008-12-30
> **DataMatrix said:**
> Yes, I'm also interested in this topic. I intend to buy that tablet (Genius G-Pen F610), but I'm unsure if it'll run with my Ubuntu 8.04.1 Hardy releace (32bit) and I don't have money to waste. Can you give us some clues about this?

PS: I don't need the hotkeys on the tablet, just the pen-thing working propperly.

Greetings,

I could get it working under Intrepid. [See]("http://ubuntuforums.org/showpost.php?p=6460895&postcount=2")

And here is a [clue]("http://ubuntuforums.org/showpost.php?p=6438885&postcount=831") :)

Regards

---

### Post by michelkogan on 2009-11-05
I have no problem with my genius F610 under Ubuntu 9.04 but hotkeys dosn't work at all. How can I configure hotkeys under Ubuntu :?:

---

### Post by AlexDS on 2010-07-04
On my machine, my GPen F610 works only with Ubuntu 9.04. No driver specially installed needed. Wish it could work with 10.4.

---

