---
title: "Middle-Click not copying and pasting"
date: 2008-10-10
forum: General Help
---

### Post by go7Ul1ai on 2008-10-10
Hello,

I just did a fresh install of Hardy Heron today (after a bad experience with Intrepid Ibex) and now I've come to find that my middle mouse button doesn't copy and paste text anymore. 
How can I resolve this?

Thanks in advance,
Lee Jarratt

---

### Post by go7Ul1ai on 2008-10-10
Whenever I ask a question on these forums, I never get replies, and I thought Ubuntu was known for it's community..

---

### Post by Sam on 2008-10-10
Hum you should wait a little more before complaining...


Run "xev" in a terminal, then clic on the new window with your middle button. Is the output like this ?

```
ButtonRelease event, serial 31, synthetic NO, window 0x4c00001,
    root 0x187, subw 0x0, time 29274533, (100,50), root:(107,865),
    state 0x210, [COLOR="Red"]button 2[/COLOR], same_screen YES
```

I've highlighted in red the important part. You should have "button 2" here.

---

### Post by go7Ul1ai on 2008-10-10
Sorry, I've had a very stressful & emotional day, thanks for your reply. I do what you say, there is a small window, with a little box in the window, when I click the middle button, nothing happens. The terminal output is just displaying where abouts I am placing the mouse cursor (per pixel). It's hard to explain,

Lee

---

### Post by Sam on 2008-10-10
Yep that's it. But if you click (without moving the mouse) on this window, the terminal should output which button was clicked. With this you can check if the middle button (#2) is really recognized.

---

### Post by go7Ul1ai on 2008-10-10
Nope, it isn't being recognised. The left and right click are though (obviously :P).

Lee

---

### Post by Sam on 2008-10-10
I'm not sure but try this:

Edit /etc/X11/xorg.conf (backup first !!!)

Find the section "InputDevice" corresponding your mouse. Add the "Buttons" option. Example:

```
Section "InputDevice"
    Identifier  "Generic Mouse"
    Driver      "mouse"
    Option      "Buttons" "5"
    # Other options goes here
EndSection
```

Then restart X using Ctrl-Alt-Backspace (save and close any work first !)

---

### Post by go7Ul1ai on 2008-10-10
Hahah, wow. This actually solved my problem, many thanks to you Sir!

Lee

---

### Post by Sam on 2008-10-10
Glad to see this! :)

---

