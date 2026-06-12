---
title: "Thinkpad W500 (FireGL v5700) + hardware drivers = no desktop"
date: 2010-11-14
forum: Hardware
---

### Post by allbread on 2010-11-14
I've just installed Linux Mint 10 (based on Ubuntu 10.10) on my new Thinkpad W500 last night;  everything appeared to be going smoothly until I activated the fglrx hardware  drivers (for the FireGL V5700 Mobility GPU card) via the hardware devices panel...

Now on restart the GUI refuses to launch and instead boots me into the text  console - I can login and such but haven't thus yet figured out how to  launch the desktop (although since I am relatively new to Linux so I may  just not be familiar with the command to do this); 'startx' gives me an  error along the lines of "there is no compatible display"...

How do I get the desktop to launch with the proprietary drivers... or, if I need to deactivate these from the console how do I go about doing this?

Searching  the web (and these forums) doesn't bring up any immediate answers...  any advice (even to just point me in the right direction) would be much  appreciated.

Thanks!

---

### Post by allbread on 2010-11-17
> **allbread said:**
> I've just installed Linux Mint 10 (based on Ubuntu 10.10) on my new Thinkpad W500 last night;  everything appeared to be going smoothly until I activated the fglrx hardware  drivers (for the FireGL V5700 Mobility GPU card) via the hardware devices panel...

Now on restart the GUI refuses to launch and instead boots me into the text  console - I can login and such but haven't thus yet figured out how to  launch the desktop (although since I am relatively new to Linux so I may  just not be familiar with the command to do this); 'startx' gives me an  error along the lines of "there is no compatible display"...

How do I get the desktop to launch with the proprietary drivers... or, if I need to deactivate these from the console how do I go about doing this?

Searching  the web (and these forums) doesn't bring up any immediate answers...  any advice (even to just point me in the right direction) would be much  appreciated.

Thanks!

Well, although I'm a bit disappointed with the support level on this question, I figure that I should probably post my workaround for posterity nonetheless...

In short, for anyone viewing this thread in the future (and indeed this may likely be applicable to all laptops with dual "dynamic" switchable GPUs):

On the Thinkpad W500 there is a BIOS option for either "discrete", "integrated" or "switchable"... by default my laptop was configured to "switchable" however this feature has only been implemented in Windows 7 (at least thus far neither Ubuntu nor Linux Mint has "out of the box" support for switchable GPUs) it defaults to the "integrated" (in my case the Intel GMA MHD4500 controller) GPU and hence when I installed the ATI drivers (and restarted) I no longer had the correct drivers installed for the default integrated GPU. 

The solution was to boot into the BIOS and manually change the selected GPU to "discrete". 

Some other threads of interests:

[http://www.phoronix.com/forums/showthread.php?t=21979&highlight=w500](http://www.phoronix.com/forums/showthread.php?t=21979&highlight=w500)

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

and

[http://ubuntuforums.org/showthread.php?t=1292723&highlight=w500](http://ubuntuforums.org/showthread.php?t=1292723&highlight=w500)

are both attempts to implement some form of "switchable" GPU control... although the former set involves possibly patching the kernel and the latter is simply a script-able means of detecting the correct hardware on boot such that the correct drivers can be loaded (requires restart to switch GPUs).

---

### Post by ekh on 2010-12-13
Thank you for this very helpful thread.

ekh

---

### Post by amorteza on 2011-01-26
Thank you very much for your useful thread, I had the exact same problem, and you suggestion resolved it.

but now GUI is all glitch. I mean it is fine until I open any window, and the title bar is all glitchy and the mouse cursor slows down

any suggestions?

---

### Post by shards72 on 2011-04-18
LIFESAVER!  Thanks so much for this...fixed my problem instantaneously!

Sorry you got poor response but thanks so much for the follow up.

Cheers,

s

---

### Post by luvshines on 2011-12-24
I know this is an old thread, but couldn't find any other thread which discusses the same.
Infact, when I installed Ubuntu 10.10 on my W500 and ran into this issue, this very thread helped me out to switch that BIOS option to discrete and get desktop back :)

My issue now is that the system runs fine for couple of reboots but then again goes into command only mode after booting. The BIOS keeps switching the mode to integrated which is really frustrating.
How to resolve this once and for all ?

**EDIT: Maybe I know the answer now. Searching intensely over the net :), I noticed there is another option just below the 'Graphics Mode', 'OS switchable graphics' which was 'Enabled' by default and since I am running Ubuntu 10.10 which supports switchable graphics, the Graphics Mode kept on toggling its mode back to 'switchable' which ruined everything. Disabling this option and setting the graphics mode to integrated should work now :D**

---

