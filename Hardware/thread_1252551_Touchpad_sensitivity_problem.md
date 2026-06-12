---
title: "Touchpad sensitivity problem"
date: 2009-08-29
forum: Hardware
---

### Post by fontis on 2009-08-29
Well the topic says it all.
I've recently switched over to Ubuntu, trying to adapt fulltime to this OS instead of dualbooting or running back to Windows as soon as it gets too annoying..

But this is just one of those small things that really really buzzkills my experience.
My touchpad is extremely sensitive. When I type something and I accidently "swirl" above it, the touchpad reacts and makes my marker go apeshit.

This is annoying because sometimes whilst surfing I accidentally hit it..
Now what I wonder is, how do I disable this, or at least retard it's reaction so that I don't have to "lock" the touchpad everytime I write something.

Help me please, I'm going insane.

---

### Post by panmoto on 2009-08-29
I too have this problem. And I found this link. I haven't try it, so I'll update how it works/or not for me.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adjust_touchpad_sensitivity](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adjust_touchpad_sensitivity)

---

### Post by panmoto on 2009-08-29
I've tried it and for some reason my Ubuntu went to low graphic mode after editing xorg.conf because it couldn't processed the edited xorg.conf. So I must restore it to the original. maybe because the method is meant for feisty.

sorry I can't help you :(

I'll look for Jaunty spesific fix.

---

### Post by Kushal S. Pandya on 2009-08-29
First open gconf -editor, its same as registry of Windows, then navigate to system>peripherals>mouse or touchpad, here u'll see various options like enabling or disabling vertical or horizontal scroll. Make changes to relavent values.

---

### Post by fontis on 2009-08-29
Thanks for the replies, but I am NOT having problems with the "scrolling".

Everything works fine with the touchpad, it's just it's too damn sensitive. If I get my thumb remotely close to it, it reacts and moves the 'mouse' or "clicks" which is annoying.

---

### Post by xyppy on 2009-08-29
I found [this wiki link]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig") in the "how to" subforum and tried it.  It worked for me.  

I followed the instructions for enabling sysdaemon and then I used this command:  syndaemon -S -d -i 1

I plugged it into my startup apps. 

good luck.

---

### Post by fontis on 2009-08-29
Thanks, I think syndaemon worked or else Its just psychologically working :p

Thanks 1000000 times for your help!

---

### Post by panmoto on 2009-08-30
thanks xyppy. it works!
for specified time after last key was pressed my touchpad is locked. and that's good :)

---

### Post by ratdog on 2009-09-23
I am having trouble with this...

After typing $xinput list my Synaptics touchpad is detected, but when I try to run syndaemon I get this error.

```
$ syndaemon -d
  X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  143 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by ratdog on 2009-09-23
I was able to fix my touchpad sensitivity problem with the gsynaptics package.  It allows you to adjust the actual sensitivity so that minor brushing with your palm while typing doesn't mess you up.

---

