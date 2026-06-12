---
title: "ATI fglrx driver problem"
date: 2012-05-18
forum: Hardware
---

### Post by barna on 2012-05-18
Hi,

With Ubuntu 11.10 I used xserver-xorg-video-radeon, because fglrx misbehaved (see later).

I upgraded to 12.04, and my notebook froze about once in every two days. (Dell Inspiron, lspci gives: 02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4300 Series]). There appeared vertical strips on the screen, and that was it. I guess this is related to the radeon driver.

So I tried to install the fglrx driver (the fglrx_updates failed to install...), and check if this works or not. It has the same problems as before, with ubuntu 11.10. When I run a 3D application (Ansoft Maxwell, a 3D modeler and electro/magneto-static solver, from a remote machine), the 3D model in the application is flickering. When I move the mouse within the window, the model appears/disappears at random times. With xserver-xorg-video-radeon there is no such problem. I have not been using fglrx long enough yet to be able to say whether it solved the freeze problem or not. 

Does anybody have an idea why, how it could be fixed, and what I should check?

Thanks
Daniel

---

### Post by QIII on 2012-05-18
How did you install the driver?

Have you installed the additional packages for hardware acceleration?

---

### Post by barna on 2012-05-18
Hi,

I used the 'Additional Drivers' from the KDE/Applications/System menu, i.e. the 'official' and correct way, I guess. 

What do you mean by the additional packages? I have glxgears for example, which is running without problem. 

Thank you

---

