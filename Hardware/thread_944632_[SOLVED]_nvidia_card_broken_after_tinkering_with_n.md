---
title: "[SOLVED] nvidia card broken after tinkering with nvidia-settings"
date: 2008-10-11
forum: Hardware
---

### Post by sokopok on 2008-10-11
I have a real problem now. I had some time on my hand so I thought I'd fix some stuff that'd been annoying me for a while. One of those things is the TV out not working properly (bad resolution, grayscale images etc...) so I read some posts about this on the forums and tinkered a bit with nvidia-settings.

First thing that started going wrong is: when I enabled the TV screen in nvidia-settings a lost access to my virtual terminals (CTRL+ALT+F1 etc...). I just got a black screen on all the terminals.

So I thought no problem: sudo dpkg-reconfigure xserver-xorg nvidia-glx-177 (when I tried nvidia-glx I got the message this package was not installed, so I checked which version was installed). This reset the configuration, so I could try again. Maybe a bit overkill to reconfigure xorg, but it shouldt hurt, should it?

I tried a couple different setups (separate X screens, Xinerama on/off TwinView, etc...). No real progress there. Allways grayscale and always funky resolution.

In the end I manually edited my xorg.conf, to manually inspect what was going on, decided to leave it for now and cleaned out the config to get it back to the way it was before I messed things up. Rebooted. When kdm starts I got horizontal black/white stripes and the system freezes (no ctrl+alt+backsp, mouse doesn't move, no ctrl+alt+f1, nothing). Hard reboot. Same thing.

I think: something really got messed up, and I'm tired of this so I load my Interpid install CD and perform a clean install. All well up untill I activate the restricted nvidia driver and reboot -> same thing: black/white stripes and a freeze. uninstalling everything nvidia doesn't fix this, I just get a black screen then.

So I boot my Windows and guess what? Same story here: black screen when I should get the login prompt. I can only boot in safe mode.

So I'm starting to suspect something went physically wrong, this is not just software anymore.

Thanks for staying with me for so long. Here comes my question now: is it possible that I physically damaged my videocard playing with nvidia-settings? And does anyone know a way to run some hardware tests on the videocard?

---

### Post by sokopok on 2008-10-12
Disregard this thread. Aparently I suffer from the linux-image-2.6.27.7 problem. I hve some other questions about this, but I'll post thosein the corresponding forum.

---

