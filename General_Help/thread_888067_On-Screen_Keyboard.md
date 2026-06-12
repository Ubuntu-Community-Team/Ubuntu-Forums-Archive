---
title: "On-Screen Keyboard"
date: 2008-08-12
forum: General Help
---

### Post by Rose Valencia on 2008-08-12
Hi everyone, im new to ubuntu, and linux in general. I just switched over from Mac OS X 10.5. Anyway, a long time ago I spilled a bit of ramen on my keyboard and the enter button no longer works. So, in order to use it I downloaded an on-screen keyboard in OS X. Now that im here, Ive been looking for one for a while, and have only found a few, and even those require me to use terminal to install, which is impossible seeing as any sudo command requires me to enter my password and press enter, which I cant do anyway because I cant press enter. SO, I really need some help if anyone would be willing to give it. :)

---

### Post by Rose Valencia on 2008-08-12
Oh, and also, neither my sound or my wifi works, and im hoping to be able to find solutions to those once I can actualy use terminal for all its worth. I cant exactly give you specs for my machine, no enter. But im running a newer MacBook.

---

### Post by BUSHYBOB on 2008-08-12
Could you remap another key to be the enter key?

---

### Post by Rose Valencia on 2008-08-12
I dont know, Ive never tried... how might I go about it?

---

### Post by mb_webguy on 2008-08-12
Have you tried the on-screen keyboard included in Ubuntu?  There's no need to hit the enter key to install, because it already is.

Go to System->Preferences->Preferred Applications, the Accessibility tab, and in the Mobility section select OnBoard and check "Run at Start".

BushyBob:  Remapping the Enter key is probably a good idea for Rose in the long run, but it would be awfully hard to do without being able to hit the Enter key.  :wink:

---

### Post by pauper on 2008-08-12
> **Rose Valencia said:**
> I dont know, Ive never tried... how might I go about it?

An example: Assign Enter to Shift_L-Shift_R.

If on mac these keys (Shift_L and Shift_R) are called otherwise find the proper
names:

Press Alt-F2, type in

```
xev > ~/output
```

Click on "Run". A window pops up. Press right Shift once. Close the window.

"output" file will be created in your /home/john_doe. Look for "KeyPress" and
"KeyRelease" events, then search for "keycode 62 (keysym 0xffe2, Shift_R)" part.

Alt-F2:

```
gksudo gedit /etc/xmodmap.conf
```

Press Ctrl-f, type Shift_R in "Search for:" field. Click on "Find". Again make
note whether Enter or Return is correct name for the key.

Now, simply add "Enter" past "Shift_R" (make sure there is a space in between):

> keycode  62 = Shift_R Enter

Press "Save", exit gedit.

Alt-F2:

```
xmodmap /etc/xmodmap.conf
```

Now, hold down left Shift and press right Shift to test if it works, in gedit
for example.

Note: You might need to add these lines to /etc/gdm/PostLogin/Default to keep
it consistent after reboot (you must create Default beforehand).

> #!/bin/sh

xmodmap /etc/xmodmap.conf

---

