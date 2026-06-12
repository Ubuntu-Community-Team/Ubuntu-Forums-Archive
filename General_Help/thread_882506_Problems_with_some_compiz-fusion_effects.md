---
title: "Problems with some compiz-fusion effects"
date: 2008-08-07
forum: General Help
---

### Post by deccan on 2008-08-07
Well hello, first of all I want to apologize for my English. This is my story: I have an Asus F3Sseries notebook on which I  installed Ubuntu 8.04, I could manage to install the drivers of my Ati Mobiliy radeon HD 2400 card,
when i type lspci in the terminal I got :01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400.
And glxinfo gives direct rendering: Yes. At this point my compiz-fusion effects worked perfectly (except the speed of the effects: very slow), but as soon as I install Ati catalyst 8.7 and enable the Ati graphic accelerator I loose some effects, like when I want to use the "film effect" (alt+ctrl+down) I got a white screen, same for the effect when I am doing alt+tab, thought the speed of all the working effects is much better withe the accelerator. 

This is my first post sorry if it is a little bit hard to understand.

If anyone have any idea about my problem, I would appreciate any comment. Thx.

---

### Post by overdrank on 2008-08-07
> **deccan said:**
> Well hello, first of all I want to apologize for my English. This is my story: I have an Asus F3Sseries notebook on which I  installed Ubuntu 8.04, I could manage to install the drivers of my Ati Mobiliy radeon HD 2400 card,
when i type lspci in the terminal I got :01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400.
And glxinfo gives direct rendering: Yes. At this point my compiz-fusion effects worked perfectly (except the speed of the effects: very slow), but as soon as I install Ati catalyst 8.7 and enable the Ati graphic accelerator I loose some effects, like when I want to use the "film effect" (alt+ctrl+down) I got a white screen, same for the effect when I am doing alt+tab, thought the speed of all the working effects is much better withe the accelerator. 

This is my first post sorry if it is a little bit hard to understand.

If anyone have any idea about my problem, I would appreciate any comment. Thx.

Hi and welcome, I have moved this thread to Desktop Effects & Customization

---

### Post by jualin on 2008-08-07
You can try installing the package "fusion-icon" which will let you change some performance Compiz Options right away such as Loose Binding or Indirect Rendering. All done by right clicking on the icon when you run Compiz Fusion Icon located under Applications, System Tools. Good luck!

---

### Post by deccan on 2008-08-07
I tried to activate loose blindings as you said Jualin, it had no effect, I still got the white screen when using the film effect. ( I do not have to restart X when I enable it, do I?)

---

### Post by jualin on 2008-08-07
No restarting X is not necessary. When you say Film Effect you mean Rotating the Cube?

---

### Post by jualin on 2008-08-07
Something that might help you is installing the package "compiz-settings-manager". And playing with different options such as the "Workarounds" sections or changing the configurations of many effects. To install it via terminal run > sudo apt-get install compiz-settings-manager

---

### Post by deccan on 2008-08-07
No the rotation of the cube is normal, the film effect is the thing when you see all your desktops on a stripe/bande

---

### Post by jualin on 2008-08-07
I have checked under the Workarounds section of Compiz Settings Manager something called "Fix screen updates with fglrx" is found. Maybe enabling this might help you out with your problem since "Fglrx" is the driver for ATI video cards. You can find Compiz Settings Manager under System, Preferences, Advanced Effects. Good luck!

---

### Post by jualin on 2008-08-07
> **deccan said:**
> No the rotation of the cube is normal, the film effect is the thing when you see all your desktops on a stripe/bande

I know what you mean now, when you enable the Cube and "unfold it" into something that looks like a film, that makes sense:). In that case I suppose that you already have Compiz Settings Manager.

---

### Post by deccan on 2008-08-07
I do not have the package compiz-settings-manager, but I have an application called 
Simple CompizConfig Settings Manager.

---

### Post by deccan on 2008-08-07
What is important in my problem is that when I disable the ati accelerator, all the effects work, they work much slover but no white screen

---

### Post by deccan on 2008-08-07
I just figured out that I have one more problem: when I watch a video file (in vlc for instance) I got the image but there are black stripes on it

---

