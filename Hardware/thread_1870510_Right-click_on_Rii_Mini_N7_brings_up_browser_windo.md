---
title: "Right-click on Rii Mini N7 brings up browser window"
date: 2011-10-27
forum: Hardware
---

### Post by dwilsonphotog on 2011-10-27
Hi all,
I'm using a Rii mini II (N7) keyboard/touchpad on 11.10.
I had used it with 11.04 with no problems whatsoever. Snce upgrading to 11.10, whenever I right-click anywhere, it brings up a new instance of Firefox (my default browser.)
There is a button on the keyboard that is supposed to bring up a new browser, but that seems to have been switched to the right-click button in 11.10 for some reason.

Any ideas on how to get my ability to right-click back without a browser popping up?
I don't even have a use for that feature.

Additional: this is the 2.4GHz version, not Bluetooth - it's the one with the touchpad in the middle, not off to the side.

Any help appreciated!

---

### Post by jatteet on 2011-11-06
> **dwilsonphotog said:**
> Hi all,
I'm using a Rii mini II (N7) keyboard/touchpad on 11.10.
I had used it with 11.04 with no problems whatsoever. Snce upgrading to 11.10, whenever I right-click anywhere, it brings up a new instance of Firefox (my default browser.)
There is a button on the keyboard that is supposed to bring up a new browser, but that seems to have been switched to the right-click button in 11.10 for some reason.


I have the exact same problem here with a mini keyboard though I dont think mine is called Rii. I have come to realise it is to do with the moment/action when you release the right-mouse-button. (I held the button for 30 seconds the browser/Firefox) didnt start). I have googled around and couldnt find any solution to the problem.

At one stage I also had issue with the mouse button mappings but I managed to change/reset that by using xinput.

Seems like ubuntu is detecting the wireless mouse/keyboard unit as something it isnt and interpreting the signals incorrectly.

Help please?

---

### Post by jatteet on 2011-11-06
So it seems my unit is also a Rii. Below is the dump from "xinput list". I purposely plugged in a logitech corded mouse (device id 11) as comparison. Strangely the keyboard-mouse is identified as a "Micro Keyboard" (device id 9). I wonder if this has something to do with the issue.

> 
\u23a1 Virtual core pointer                        id=2    [master pointer  (3)]
\u239c   \u21b3 Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
\u239c   \u21b3 Riitek Micro Keyboard                       id=9    [slave  pointer  (2)]
\u239c   \u21b3 Logitech USB-PS/2 Optical Mouse             id=11    [slave  pointer  (2)]
\u23a3 Virtual core keyboard                       id=3    [master keyboard (2)]
    \u21b3 Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    \u21b3 Power Button                                id=6    [slave  keyboard (3)]
    \u21b3 Power Button                                id=7    [slave  keyboard (3)]
    \u21b3 Riitek Micro Keyboard                       id=8    [slave  keyboard (3)]



---

### Post by paul_r1 on 2012-04-23
I just got my Rii mini N7 today and have the same problem but have discovered a usable solution.

I'm running Ubuntu 10.04 LTS and found that if I do the following procedure I get the right click menu for the item I clicked and Firefox 'sometimes' opens. When firefox opens though the right click menu is on-top and the menu options still work as desired, such as paste, etc. I then just alt-f4 on the keyboard to close the firefox window.

The Procedure is:
1. Click and hold Left mouse button
2. Click and release right mouse button
3. Release left mouse button.

Try this combo with various time intervals. I find if I hold the left mouse button for 1/2 a second before steps 2 and 3 it works pretty well...

This procedure doesn't work for highlighting and copying though. For that you will need to highlight and ctrl+c still, but it will work for pasting functions as nothing needs to be highlighted when pasting...

Thought I should let you all know. These mini keyboards are still awesome!

Paul.

---

### Post by slartibartfast42 on 2012-07-14
I know it's quite an old thread but nevertheless I'd like to share a workaround for this behaviour:
Right mouse button works for me as expected if I press Fn + right mouse button.

Besides I discovered that the mouse button works without flaws when using Ubuntu 12.04 on my desktop computer but shows this "right mouse button - open default browser" behaviour on my htpc using the same system version.

---

