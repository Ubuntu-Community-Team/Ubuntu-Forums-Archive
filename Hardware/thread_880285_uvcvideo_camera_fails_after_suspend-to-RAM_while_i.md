---
title: "uvcvideo camera fails after suspend-to-RAM while in use."
date: 2008-08-04
forum: Hardware
---

### Post by The Warlock on 2008-08-04
So, I've got a shiny new Eee 901. It has a camera. The camera uses the uvcvideo driver.

uvcvideo is a module that doesn't play nicely with suspend-to-RAM (aka. "sleep mode"). 

But that's okay, because the module gets unloaded before sleep and reloaded afterwards automatically, right?

Well, yes, except when it's in use. If I have cheese or skype or mplayer using the camera when I sleep the laptop, when I get back from sleep the camera will refuse to work until a full reboot. Restarting the program using the camera does nothing. Even "sudo rmmod uvcvideo" hangs.

Is there any way to fix this? I mean, I'd like to use the camera without worrying about closing whatever programs are using it before suspending.

---

