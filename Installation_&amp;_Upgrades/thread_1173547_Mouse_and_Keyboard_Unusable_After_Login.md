---
title: "Mouse and Keyboard Unusable After Login"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by radioraheem on 2009-05-29
I did a direct upgrade of 8.10 to 9.04 and everything seemed to go smoothly except for one HUGE problem.

Mouse and keyboard work fine on the login screen (I did notice it won't select different options in the sessions menu, but tab/enter works fine) but as soon as I have ANY windows open once logged in to gnome the mouse goes haywire, and occasionally the keyboard.

Keyboard is wired ps/2, mouse is a pretty run of the mill logitech wireless.

The only thing that will give me back regular mouse control is if I right click like crazy randomly all over the screen.  One time I managed to open the trash in nautilus before it went crazy, but then it interpreted _every single_ mouse click as me wanting to open a new window.  I started closing them with ctrl+f4 after about 40 appeared.

I know a lot of people have reported problems with the Xorg to HAL transition, and I'm still learning the ropes of hal myself.

lshal | grep mouse 

> access_control.type = 'mouse'  (string)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
  info.product = 'Macintosh mouse button emulation'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  battery.type = 'mouse'  (string)
  access_control.type = 'mouse'  (string)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)

obviously I'm not using a macintosh mouse with this desktop, but I'm not sure if those settings are relevant to my problem either.

I plugged in a wired mouse and that really seemed to confuse it.  the pointer worked but the clicks would register elsewhere, and double clicking seemed to lock in this effect.  If I double click a blank line in a terminal I can just move the mouse, double click anywhere else on the monitor, and you can see the line in the terminal re-highlight itself over and over, etc etc etc.

If It wasn't completely killing my desktop use right now I'd almost admire it because I've never seen anything like it before.

Anyone have any advice while I continue to google things frantically?  :D

Thanks

---

### Post by radioraheem on 2009-05-30
I hate to bump, but well, bump.

i'm on the verge of just clean formatting with 8.10 again.  If anyone could provide some suggestions or info I would be forever grateful.

Thanks.

---

### Post by radioraheem on 2009-05-30
Wow, this is bad.  Same thing happens when using a Live CD.

So much for a clean install working correctly.

Back to 8.10 I go, sadly.

---

### Post by MrLogistiX on 2009-12-22
I have the same issue using a Logitech MX1100 mouse on clean install of Ubuntu 9.10. Found a workaround, but no fix: when the mouse stops responding (usually after switching back to the KVM port the Linux box is connected to), I power the mouse off using the switch on the bottom, then wait 5 secs or so, power back up. Has worked every time so far. I was THIS close to scrapping Karmic for, I dunno, anything? until I tried this.

---

### Post by MrLogistiX on 2009-12-27
UPDATE: My 'workaround' stopped working, and after running software updates in a misguided attempt to cure the issue, I only get a black screen after bootup. Tried installing Kubuntu, after reading many posts suggesting it was less problematic, got the same, unresolved issue. Going to try loading the 64-bit version in a VM on my Dell T5400, freshly loaded w/ Win7. Can't afford to risk replacing Win w/ this, and not in the mood to play w/ a 2xBoot config on my production mule, especially given the results so far. Somedays I love computers...just not today...guess I'll get on the bus w/ the rest of the 8.10 back-revvers. Kind of reminds me of something Microsoft users went through w/ Vista, & sticking w/ XP...hmmm, maybe next release will be better?

---

