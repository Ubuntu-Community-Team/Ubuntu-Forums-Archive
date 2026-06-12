---
title: "Mouse doesn't work as Plug &amp; Play with evdev driver"
date: 2008-09-24
forum: Hardware
---

### Post by mgol on 2008-09-24
I have USB optical Logitech MX310 mouse (6 buttons):
[IMG]http://www.mb-tech.at/images/mx310.jpg[/IMG]
Because last button, located under the middle button is recognized by "mouse" (Driver "mouse" entry in xorg.conf) as the middle one, too - and I wanted to assign different functionalities to them both, I had to apply another solution.

I found this thread: ["Calling Logitech MX 310 owners only"]("http://ubuntuforums.org/showpost.php?p=5266834&postcount=11") and did as written there, using "evdev" driver and script put in /etc/X11/Xsession.d/.

Now all buttons work fine, but when I disconnect a device and connect a USB plug again, mouse is not recognized. The only way to make it work again is to restart X server (Ctrl+Alt+Backspace).

What should I do to make it work normally, again?

**Edit:** It seems that most of the problems are caused by evdev driver - I don't know why (maybe sb knows?), but it completely ignores devices plugged after start of X server. Moreover, it uses handlers names like /dev/input/eventX, where X is some number and... it sometimes changes after restart! So it always can happen to anybody that they must edit xorg.conf after restart... Not very nice.

Is there any way to teach standard, "mouse" driver, that middle button and the button below it (let's name it "appChanger" from its standard function in Windows XP - you can see it in the picture) are not the same one (both see it as "button 2")? This would let me get rid of this evdev driver.

I tried remapping this "2" button to unsupported "9":
```
xmodmap -e "pointer = 1 9 3 4 5 6 7 8 2"
```
and then asign some functionality to both of these buttons using btnx, but there are also problems with that app. (See [my thread about this issue]("http://ubuntuforums.org/showpost.php?p=5847755&postcount=1125"))

---

### Post by prashime on 2008-09-25
Try this
[http://www.hidpoint.com/](http://www.hidpoint.com/)

---

### Post by mgol on 2008-09-25
> **prashime said:**
> Try this
[http://www.hidpoint.com/](http://www.hidpoint.com/)
"Unsupported kernel version."
And, moreover, Logitech MX 310 does not exist on "Supported Devices" list.

**EDIT:** I tried another configuration and it run, but it doesn't recognize my mouse. Probably because it's not supported. :/

**EDIT2:** Not relevant any more (at least to me). I switched to Karmic and its Xorg recognizes the additional button.

---

