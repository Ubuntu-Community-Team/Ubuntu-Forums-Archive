---
title: "Keyboard question!"
date: 2008-07-19
forum: General Help
---

### Post by Duranxl on 2008-07-19
Hi!

I have some questions regarding my keyboard layout.
It's set to general 105 with USA international (like i had on windows)>
The layout itself is fine, but I have this annoyance that is REALLY bugging me

Whenever i want to type e.g. "don't" i have to press <space> after the ' sign.
In windows this was not the case, and after pressing ' it would automatically insert the ' after pressing the next key.

So in windows i press:
d o n ' t

In ubuntu:
d o n ' <space> t

I really need to get this sorted!

thanks!

---

### Post by solwic on 2008-07-19
It's your keyboard settings...I had this issue, too.  You need to change the keyboard layout to USA/USA.  Go to Settings -> Preferences -> Keyboard.

Your layout should simply be "USA".  

Good luck.

EDIT:  If it's not set to USA I think you can remove the current layout and add a new one.  Under "Selected Layouts" choose your current layout and click the "Remove" button beneath the box.  Then click the "Add" button and it'll bring up a list.  Scroll way down to the bottom and you'll see "USA".  Choose that, and you may have to restart X or something (Ctrl + Alt + Backspace)...I'm not sure.

---

### Post by Duranxl on 2008-07-20
But i chose the international USA because i want to be able to do é and è by pressing '+e and `+e!
The default USA layout doesn't seem to have these éè under the E key!

---

### Post by solwic on 2008-07-20
> **Duranxl said:**
> But i chose the international USA because i want to be able to do é and è by pressing '+e and `+e!
The default USA layout doesn't seem to have these éè under the E key!

Ahh I didn't know you had a reason for using the international layout!  In that case...I have no idea what could be causing that.  

Sorry!  :(

---

### Post by der_joachim on 2008-07-20
A nice alternative is using Compose Keys. In the 'compose' way, an é is created by Compose+'+e, thus enabling you to type accent charactrs normally. You can enable the compose key by adding an XkbOption to your keyboard section in your xorg.conf . I am currently not on my Ubuntu box now, so I cannot post my xorg.conf, but a quick forum or wiki search should do the trick.

---

