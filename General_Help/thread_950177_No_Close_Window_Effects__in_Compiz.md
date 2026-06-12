---
title: "No Close Window Effects  in Compiz"
date: 2008-10-16
forum: General Help
---

### Post by Spartacus84 on 2008-10-16
I can't get compiz to initiate the close window effect. However, the open and minimize effects work fine, as well as all other effects. Every time I close a window, it just does the fade effect, instead of what I set it to. When I type compiz into the terminal, it says Xgl is not present.

Also, How do I get compiz to start automatically when I boot up?

---

### Post by Genius314 on 2008-10-16
Not sure about the close windows thing, but try disabling the "Fading Windows" plugin.

To get Compiz on bootup, install fusion-icon.
> sudo apt-get install fusion-icon
Then go to System>Preferences>Sessions, add a new one to the list, with the command "fusion-icon" (without the quotes).

Hope that helps. :)

---

### Post by Spartacus84 on 2008-10-17
> **Genius314 said:**
> Not sure about the close windows thing, but try disabling the "Fading Windows" plugin.

To get Compiz on bootup, install fusion-icon.

Then go to System>Preferences>Sessions, add a new one to the list, with the command "fusion-icon" (without the quotes).

Hope that helps. :)

I have tried disabling all effects but animations, an dit still doesn't work.

Thanks for the help on automatic boot though.

---

### Post by Spartacus84 on 2008-10-18
Anybody?

---

### Post by Spartacus84 on 2008-10-19
In case anybody needs them, here are my specs:

Ubuntu 8.04 (32 bit)
Compaq Presario F756NR
NVidia GeForce 7000M
AMD Turion 64 X2 Mobile Processor

---

### Post by armageddon08 on 2008-10-19
> **Spartacus84 said:**
> In case anybody needs them, here are my specs:

Ubuntu 8.04 (32 bit)
Compaq Presario F756NR
NVidia GeForce 7000M
AMD Turion 64 X2 Mobile Processor

Try changing the backend.

---

### Post by LordIshamael on 2008-11-24
hey i had a similar problem, got it fixed here
did you try it this way?
[http://forum.compiz-fusion.org/showthread.php?t=10011](http://forum.compiz-fusion.org/showthread.php?t=10011)

says:
then go to the animations plugin (and make sure it's activated)

then under the 'open animation' and the 'close animation' tabs you can add an effect

just click 'new', choose the effect as 'Burn", set your duration to how long you want the animation to last for and set your window match to the windows you want this to apply to



he also says if you want to apply the effects to all windows, then type 'all' as your window type, however, it didnt work for me, id suggest simply copying your current effect's window type (ie you have fade now so the window type listed under fade) into the new effect

---

### Post by dariusdwtt on 2008-11-30
try clearing all the animation fields with the little brush. then reselecting your animations, sounds lame but worked for me.

---

