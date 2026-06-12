---
title: "desktop effects with ATI Radeon HD3200"
date: 2009-10-25
forum: Hardware
---

### Post by Ampi on 2009-10-25
I want to enable desktop effects (normal or extra) but I get the message: 

Desktop effects could not be enabled. 

I have a ATI Radeon HD3200 graphics card. I've seen in other posts that this has to do with the driver 'fglrx'. But when I do:

dmesg|grep 'fglrx'

I have no output at all. This should mean I don't have the restricted driver installed. That is true. But when I do activate the driver, the screen suddenly shows some horizontal lines (on and off) and it looks like the cable isn't connected correctly, as if there is some sort of an interruption. 

I downloaded en installed the driver from the ATI webpage, but I get the same horizontal line. Looking and the Compiz webpage when I give th command:

glxinfo | grep -i direct

Then this is the output:

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

So I am not sure what to do to be able to enable Desktop effects. It looks like I don't even can. Is that true?
Anyone has a different idea?

---

### Post by nathan726 on 2009-11-13
Apparently "Compiz works fine" after following the steps (post #2) in this thread:
[http://ubuntuforums.org/showthread.php?t=1133950](http://ubuntuforums.org/showthread.php?t=1133950)

---

