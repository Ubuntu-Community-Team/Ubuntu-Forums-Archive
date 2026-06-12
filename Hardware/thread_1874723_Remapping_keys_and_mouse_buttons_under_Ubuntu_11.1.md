---
title: "Remapping keys and mouse buttons under Ubuntu 11.10"
date: 2011-11-03
forum: Hardware
---

### Post by vaul on 2011-11-03
*Disclaimer: I do realize that this question have been asked and answered many times, but all of the howtos and instructions I have found are obsolete. Regrettably, despite quite a lot of effort, I was unable to find a solution that still works.*

Methods that I have tried are listed below.
[LIST=1]
[*]Utility called keytouch that was often mentioned in the past no longer works with Ubuntu 11.10 and therefore is removed from the repositories. Installing it manually from the Source Forge does not make it work either.
[*]Utility called xkeybind-configure do not detect key presses from either zoom slider on the keyboard or additional mouse buttons, even if you are able to get past segmentation fault crashes in the very beginning.
[*]Utilities xev and xmonad, well, I was just unable to get those two to work — they do not seem to detect key presses from buttons that I need to configure when ran in the mode «xev | grep keysym» and produce a lot of useless information otherwise, still not detecting key presses I need.
[*]I have also tried utility called imwheel, but whenever I try to run it in the configuration mode by typing «imwheel -c» it crashes saying «Configuration terminated by signal 11».
[*]I have tried graphical utility called «btnx» and was somewhat shocked by the fact that this one actually worked. Unfortunately, it allows user to *add* key combinations to the mouse button presses, not remap them. So, if I use it, I end up with mouse buttons calling up two commands: one that I want to appear and the other, present by default.
[/LIST]

Specific hardware: I use a very nice pair of [Microsoft Natural Ergonomic Keyboard 4000]("http://www.microsoft.com/hardware/en-us/p/natural-ergonomic-keyboard-4000/B2M-00012") and [Microsoft Natural Wireless Mouse 6000]("http://www.microsoft.com/hardware/en-us/p/natural-wireless-laser-mouse-6000") which are both very nice and convenient to use, with the exception some keys are configured in a useless and annoying ways.

The keyboard and mouse are already configured to make use of multimedia keys and extra mouse buttons, but I am specifically interested in making zoom slider that do not at all just now scroll and little and big thumb buttons on the mouse to emulate mouse middle button  press and Super + W respectively.

Is there a tool in GNU\Linux to do this that is not currently bugged and/or broken? Anyone?

P.S. Also, I am completely desperate to find a way to change mouse wheel scrolling speed in Ubuntu. It have been said a few times that it is not currently possible. Is this true?

---

### Post by beruic on 2011-12-27
I use a script for remapping my mousebuttons, but essentially the command:
  xinput --set-button-map
is quite handy for swapping mouse buttons.

---

### Post by vaul on 2011-12-29
Many thanks, I have already figured that one out myself. Indeed, 'xinput' is very handy for remapping mouse buttons and I was able to find solution to make zoom slider work and even scroll [here]("http://sandilands.info/sgordon/scroll-with-microsoft-natural-ergonomic-keyboard-4000-ubuntu-linux") (read the comments in both explanation and command sections for updated instructions).

But one issue still stands &#8212; how can I make one of the mouse buttons produce a combination of key presses? For example, I would like little thumb button to function as 'Super + W' in order to be useful.

Utility 'xbindkeys' can do that, but there is a problem &#8212; it adds keys combination to the mouse, not replaces them. So, instead of one shortcut it produces two simultaneously, which is not nice.

Any advice?

---

### Post by beruic on 2011-12-29
Well, I only had issues with history back and forward on the mouse. I solved that by remapping buttons 6 and 7 to 8 and 9.

My first attempt was however to make the mouse buttons fire [Alt]+[Left] and  [Alt]+[Right]. You can do this with xbindkeys, but to my experience it's easier to use the 'Commands' plugin in Compiz. Then you don't have to install xbindkeys and xautomation, only xvkbd.

I manage without either however, because of the remapping. I can't however figure out how to remap a mouse button for a keyboard button, or combination. Perhaps you should remap the mouse button to one without a function assigned (if that's possible) in order to not have two events fired at the same time.

---

### Post by vaul on 2011-12-29
Hmm. That is quite interesting point, I do have a mouse button that is neither assigned nor physically present &#8212; it is numbered 13; will try that.

However, I have heard that CompizConfig sometimes ruins people's desktops as of 11.10, is it true? It seems that in some [cases]("http://askubuntu.com/questions/66079/compiz-crash-means-launcher-and-almost-everything-else-has-disappeared-from-desk") it is true, but nothing terrible happened to me yet.

Hooray! Thanks to your help I have finally managed my little thumb mouse button to do what I want &#8212; initiate expo wall plugin.

For future reference, here is what I did: I had to install CompizConfig Settings Manager, or CCSM for short, and package 'xautomation', of which I used utility called 'xte'. I have remapped needed mouse button 9 to the present, but unused and unassigned button 13 using the following command. For me, this command looked like this:
```
xinput set-button-map 10 1 2 3 4 5 6 7 2 13 10 11 12 8
```

To do that, obviously package 'xinput' was necessary (I also had to add that command to the Startup Applications to make the customization permanent to my user account). To make sure everything worked as planned, you may want to run command 'xev | grep button' and see if button you press is indeed identified as a button you want it to be.

Then, I determined how 'xte' command for the action I wanted to perform would look, I turned out to be something like the following. 
```
xte 'keydown Super_L' 'usleep 50000' 'key W' 'usleep 50000' 'keyup Super_L'
```

Note that in order for X server to properly «catch» fake key presses you need to specify a delay between them, one twentieth of a second worked best for me.

Then, I simply added before mentioned xte command to the CCSM plugin Commands as a Command 0 and specified it to be used when mouse button 13 is pressed.

---

