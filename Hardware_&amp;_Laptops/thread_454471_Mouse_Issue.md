---
title: "Mouse Issue"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by Dylnuge on 2007-05-25
**For those just coming in (which, since this is still just a thread of useless bumps and one completely unhelpful post, should be everyone), please see page two AFTER reading this post. **

Hello,

Using Feisty-Ubuntu Studio. Followed Instructions Here:
[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons#head-f34e1a53b6bf6433891bcd5c2ed34f3e1af84a7c](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons#head-f34e1a53b6bf6433891bcd5c2ed34f3e1af84a7c)

Scroll buttons now act as back and forth buttons, and back and forth buttons still do nothing.

Xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Buttons"       "7"
        Option          "ButtonMapping" "1 2 3 6 7"
        Option          "Emulate3Buttons"       "true"
EndSection

```

imwheel:
```
".*" None,Up,Alt_L|Left None,Down,Alt_L|Right

```

57xmodmap:
```
#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 4 5"

```

---

### Post by Dylnuge on 2007-05-25
I can fix the scroll button issue by blanking the 57xmodmap file. Does nothing else.

---

### Post by Dylnuge on 2007-05-28
Okay, I think I got somewhere, but its still not working. I used imwheel -c and noticed that 6 and 7 were assigned to my scroll wheel for some reason. I swapped ZAxisMapping to "6 7" and Buttons to "1 2 3 4 5". Imwheel is the same.

When I tried changing xmodmap to "1 2 3 4 5 6 7" the same things as before happened-scroll wheel moved the pages back and forth. When I switched it back however, to "1 2 3 6 7 4 5", everyting worked normally, except with no back and forward buttons.

Before Ubuntu Studio, this all worked seamlessly, including in Feisty. This is a new Ubuntu Studio install. I want to like this release, but I need to get this problem fixed first.

---

### Post by Dylnuge on 2007-05-28
Anyone? I need some help with this issue.

---

### Post by gjtoth on 2007-05-28
> **Dylnuge said:**
> Anyone? I need some help with this issue.

I don't use anything but:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Emulate3Buttons" "false"
	Option "Buttons" "7"
	Option "ButtonMapping" "1 2 3 6 7"
	Option "ZAxisMapping" "4 5"
EndSection

No other imouse, magicmouse, nothing but what I have in the xorg.conf

---

### Post by Dylnuge on 2007-05-28
Tried that, didn't work.

---

### Post by Dylnuge on 2007-06-16
Okay. I reinstalled the OS-normal version this time, didn't really love UbuntuStudio. Ran through the instructions again, same problem! Look, this is annoying, and while it may seem minor, I use the buttons so much that when they don't work I continue to use them, then get frusturated.

As much as I love Linux, I really wish this started working again for me like before. Will there be automatic support in gusty?

-Dylan

PS: Please Help!!!!!!!!!

**Additional Information**

If I change:

```
xmodmap -e "pointer = 1 2 3 6 7 4 5"
```

to:

```
xmodmap -e "pointer = 1 2 3 4 5 6 7"
```

then I can scroll again. Still can't go back and forth.

---

### Post by Dylnuge on 2007-06-17
Okay, I checked imwheel -c. It seems that my scroll wheel is mapped to buttons 4 and 5. My back button is mapped to button 6. My forward button does not seem do change the imwheel screen.

---

### Post by Dylnuge on 2007-06-19
Okay, I am borrowing a friends Logitech mouse. Much nicer then mine, and has back/forth buttons, so I will try it and see if it works.

If so, I guess I will buy a new mouse. After, of course, I buy a new headset. And external hard drive. And flash drive. And build a server.

Reflecting on this, this is one expensive hobby.

---

### Post by Dylnuge on 2007-06-19
Did not work. Still cant go back and forth. On both mice, the back button middle clicks, and the forward button right clicks.

Please. Help.

---

### Post by Dylnuge on 2007-06-19
I am sorry for bumping, but I can't seem to find a solution. Or a useful post.

Thanks,
Dylan

---

### Post by Dylnuge on 2007-06-20
I am really starting to miss this functionality. I know it is not something big enough to switch back to windows because of, but it is getting to be very big, and I am hoping someone will help.

-Dylan

---

### Post by Dylnuge on 2007-06-23
I actually promise this will be my last bump. I will find somewhere else to look after this.

I realise that by now everyone who could have possibly helped has probably seen it, and does not know what to do.

---

