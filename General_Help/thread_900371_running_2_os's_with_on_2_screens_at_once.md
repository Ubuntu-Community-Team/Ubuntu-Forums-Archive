---
title: "running 2 os's with on 2 screens at once"
date: 2008-08-25
forum: General Help
---

### Post by EnGorDiaz on 2008-08-25
hi engor here

i have a couple of questions that have entered my mind since my recent post i mentioned something illegal didnt know it but got an infraction i think thats worser than a warning but anyway

i was wondering i want to run 2 os's on the same comp with 2 screens impossible i think not so im wondering is there any tutorials anything to help me through this im planning on running ubuntu/osx/ipcop/vista im choosing but yeah :D 

i want to make a tutorial after i get my info

[http://www.youtube.com/watch?v=5dtnEFh493M](http://www.youtube.com/watch?v=5dtnEFh493M)

these questions will be answered 

is this possible?
anything is possible on linux

will it be easy?
i will make it easy for you

thank you for your time engor

---

### Post by durand on 2008-08-25
You can use virtualisation software like vmware, virtual box, etc

---

### Post by bryonak on 2008-08-25
Hi engor.
First, please throw in some punctuation, because youre pretty cumbersome to read. This makes me (and I believe other people as well) reluctant to answer... but since I've done what you are asking for, I'll give it a try.

There are several kinds of dualscreen setups, the two most common are multihead (with big screen or cloned screen) and multiseat.

Multihead is what you saw at the beginning of the video: one OS using two screens ("heads") in either one big desktop (like in the video) or two screens showing the identical view (often used with beamers).

Multiseat is intended for two people ("seats") to work on one machine, or one person to have two working environments.
First you have to realize that this is only possible with emulation (like in your video), with one OS being the host and the other one playing guest.
One way to achieve this is to create a multihead big screen setup, then start an emulator (vmware, vbox, ...) and place it on one screen. This is what happens in the video.
You can then turn off the emulators window decoration (title bar, buttons and border) with compiz or simply maximize it (depends on the emulator).
You can also use Xephyr to separate the regions of your screen: for example start Xephyr on one screen, launch an emulator inside and bind a second mouse only to the guest OS. This also makes it easier to maximize the emulator, since it will be restricted to the Xephyr window.

One important thing is that you will not be able to move windows or drag&drop files from one OS to the other, but that's not possible with Windows XP/Vista either.

Also note that if you use an graphics adapter with two video outputs, you might not be able to go run 3D applications or play videos on both screens. This is heavily dependant on your graphics hardware, especially with older cards/chips.
You'll have less problems with two distinct graphics adapters, though that might be difficult to get with a laptop...

To get started and learn some basics, google for these keywords:
multihead, multiseat, vmware, xephyr


A more complex approach is to configure the X server to share its virtual terminal with a second X, which gives you a good multiseat setup because the desktops are completely separated (you can't move the mouse or windows from one to the other) and each user can use his own mouse&keyboard... but I think this is not what you want.

One more note on Xephyr: this software is especially powerful if you want to run the same Linux distro (for example Ubuntu ;)) in a multiseat setup with two different desktop environments. You don't need to emulate it, just use the second X server inside Xephyr, which improves your performance greatly (compared to emulating).
This way you can assign a separate mouse&keyboard to each screen and, for example, surf the web or play some games in GNOME while your friend does some writing in FluxBox, all on the same computer!

---

### Post by durand on 2008-08-25
Sorry, I thought you already setup dual screens. 

If you have an nvidia graphics card, you can just plug in your second monitor into the card and use nvidia-settings to configure the second monitor with twinview or separate x screens. With twinview, both screens share the same desktop while with separate x, you get two separate desktops where only the mouse is allowed to move between the two. 

If you want to use more than one keyboard and mouse to control the two screens separately, you should use Xephyr and the stuff mentioned above.

---

### Post by EnGorDiaz on 2008-08-25
> **bryonak said:**
> Hi engor.
First, please throw in some punctuation, because youre pretty cumbersome to read. This makes me (and I believe other people as well) reluctant to answer... but since I've done what you are asking for, I'll give it a try.

There are several kinds of dualscreen setups, the two most common are multihead (with big screen or cloned screen) and multiseat.

Multihead is what you saw at the beginning of the video: one OS using two screens ("heads") in either one big desktop (like in the video) or two screens showing the identical view (often used with beamers).

Multiseat is intended for two people ("seats") to work on one machine, or one person to have two working environments.
First you have to realize that this is only possible with emulation (like in your video), with one OS being the host and the other one playing guest.
One way to achieve this is to create a multihead big screen setup, then start an emulator (vmware, vbox, ...) and place it on one screen. This is what happens in the video.
You can then turn off the emulators window decoration (title bar, buttons and border) with compiz or simply maximize it (depends on the emulator).
You can also use Xephyr to separate the regions of your screen: for example start Xephyr on one screen, launch an emulator inside and bind a second mouse only to the guest OS. This also makes it easier to maximize the emulator, since it will be restricted to the Xephyr window.

One important thing is that you will not be able to move windows or drag&drop files from one OS to the other, but that's not possible with Windows XP/Vista either.

Also note that if you use an graphics adapter with two video outputs, you might not be able to go run 3D applications or play videos on both screens. This is heavily dependant on your graphics hardware, especially with older cards/chips.
You'll have less problems with two distinct graphics adapters, though that might be difficult to get with a laptop...

To get started and learn some basics, google for these keywords:
multihead, multiseat, vmware, xephyr


A more complex approach is to configure the X server to share its virtual terminal with a second X, which gives you a good multiseat setup because the desktops are completely separated (you can't move the mouse or windows from one to the other) and each user can use his own mouse&keyboard... but I think this is not what you want.

One more note on Xephyr: this software is especially powerful if you want to run the same Linux distro (for example Ubuntu ;)) in a multiseat setup with two different desktop environments. You don't need to emulate it, just use the second X server inside Xephyr, which improves your performance greatly (compared to emulating).
This way you can assign a separate mouse&keyboard to each screen and, for example, surf the web or play some games in GNOME while your friend does some writing in FluxBox, all on the same computer!

thank you i will give this a try and then try and make a tutorial on it :D

---

### Post by steveneddy on 2008-08-25
> **bryonak said:**
> hi engor.
First, please throw in some punctuation, because you're pretty cumbersome to read. This makes me (and i believe other people as well) reluctant to answer... 

+1

---

### Post by EnGorDiaz on 2008-08-26
sorry about the punctuation guy's.

---

### Post by EnGorDiaz on 2008-08-26
ive decide i will be working with ipcop is there a way to make the 2 os's working at once without vm?

---

### Post by PapaRaven on 2009-04-04
"... youre pretty cumbersome to read ..."

-- One loses count of such criticisms, conversely being devoid of the aforementioned proofreading.

---

