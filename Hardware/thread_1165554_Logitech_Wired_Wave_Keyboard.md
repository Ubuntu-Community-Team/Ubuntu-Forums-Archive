---
title: "Logitech Wired Wave Keyboard"
date: 2009-05-20
forum: Hardware
---

### Post by jimmio on 2009-05-20
Hello all,
I just purchased the parts for a new PC and put it all together and everything works fine except a few of the multimedia keys on my new keyboard. All of the important ones (Previous, Next, Volume Up/Down/Mute, Music player, email, and webbrowser) work fine, but most of the Fn modified function keys do nothing, along with the Command Prompt, Camera, Media Center, Zoom In/Out, and Aero Flip keys. I installed keytouch and keytouch-editor, and the editor is able to find the keys but it's a different event in the list than the standard keys, making me think this is an easy fix. Setting up the keys in keytouch-editor does nothing at all other than waste my time and get my hopes up, as once they're set, they do nothing.

Any input would be great.

Thanks,
Jim

---

### Post by drspangle on 2009-07-08
Instead of starting my own, I'm going to bump this instead.

Here is what I know: the extra keys are not supported for whatever reason - they do not produce keycodes.

keytouch should work, if you can get keyTouch editor 3.2.0 beta to compile in 8.10 onwards (so stll doesnt work in 9.04), which you can't as it doesnt compile and every thread I've seen asking for assistance regarding that is either in Hungarian or has no resolution.

Is there ANY solution to this issue, a good 3 years after this keyboard has been on sale?

This is silly really, it's a keyboard for God's sake. It's ridiculous how much work needs to go into just mapping my mouse buttons (since btnx stopped working), and my keyboard still isnt properly supported. It's 2009, why can't I easily (or even be able to..) configure my Logitech brand input devices within the Gnome settings?

---

### Post by Plasma_NZ on 2010-02-03
Ok i just baught a Logitech Wave Corded today, and in 6 hours i had all buttons apart from volume up/down/mute work..

albeit it stuffed my logitech G5 mouse buttons i managed some work-arounds for the time bing.. first off here's wat u do...

Download and install HIDPoint - and install 

have a fiddle and see what happens, its a bit touchy sometimes requiring hidpoint to be closed and started after making changes to buttons...

If your like me and run compiz and use the zoom feature and would like to program the keyboards zoom buttons try the following...

download and install xdotool - its in the repo's..

now u need to create a a file in this place like so..

```

sudo gedit /usr/local/bin/zoomin

```

inside there put this in

```

#!/bin/bash
xdotool key alt+1

```

save the file and then do the next command but change the alt+1 to alt+2 in the zoomout file

```

sudo chmod +x /usr/local/bin/zoomin

```

repeat the steps above for zoomout except change the filename too zoomout obviously...

next u want to open hid - and change the zoomin setting to "Launch Program" - and type in "zoomin"

repeat for zoomout one aswell..

Now u need to open compiz-manager and goto "enhanced zoom desktop"
and goto the "specific zoom" 

in zoom specific level 1 - change the zoom_specific_key to <alt>1
in zoom specific level 2 - change the zoom_specific_key to <alt>2

and close compiz manager..  close hid and kill it in gnome-system-monitor then reload it.. and make sure compiz is running, and test the zoomin/out keys... 


good luck... hope this has helped

if u require help with the mouse buttons, drop me a email via the forums...

---

