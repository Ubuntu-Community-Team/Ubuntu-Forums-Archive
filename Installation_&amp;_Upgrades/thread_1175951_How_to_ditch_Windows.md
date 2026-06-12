---
title: "How to ditch Windows?"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by Paperfairy on 2009-06-01
I have my system partitioned or both XP and 9.04. I really only have Windows for:

Starcraft
MediaMonkey
Office 2007
iPod support

While I am aware that the first three can be done with a VBox/VMWare, I often hack around with my iPod, and it is seemingly impossible to jailbreak the iPod with XP inside Ubuntu, because of how USB works (jailbreaking involves the rapid dis/reconnect of the iPod, but USB must be TOLD to connect...) - can that be fixed so that I can start using VMWare? Also, if I manage to fix that, would simply copying the Windows partition, file for file into the VirtualXP recreate all my settings?

---

### Post by madverb on 2009-06-01
I'm not sure if there is a fix for the USB problem.
Copying the Windows files across won't work. You might be able to get it working but VBox/VMWare will have different drivers for their "hardware".

---

### Post by Paperfairy on 2009-06-01
What can I do in order to keep as many settings as possible?

---

### Post by Mark Phelps on 2009-06-02
> **Paperfairy said:**
> What can I do in order to keep as many settings as possible?

Since you have to install XP afresh in VMWare anyway, you could use  Windows Easy Transfer to save your settings from XP, and then when you install again, import those same settings.

This won't handle programs, of course.  You'll have to install all of those from scratch.

---

### Post by LepeKaname on 2009-06-03
It was that a commercial??? (It is not even for Linux!!!!!!!)

You can also run Starcraft in wine (much better than VMWARE).

---

### Post by Paperfairy on 2009-06-03
Starcraft is very laggy in wine, but runs perfectly in a box....

Thanks guys.

---

### Post by gamblor01 on 2009-06-03
You could just try to convert your physical machine to a virtual image and then run it with VMware.  Try their free converter:


[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)



Also, Starcraft is probably laggy in wine because you haven't set enough of the options.  I can play HL2 based games such as Portal and TF2 with over 100FPS -- if the system is properly tweaked.  I have never tried Starcraft but if Wine can handle TF2 it should certainly be capable of handling Starcraft.

But hey, if you don't mind running it through a VM then just do that!

---

### Post by matthewbpt on 2009-06-03
What kind of ipod do you have? what generation as well

---

### Post by LepeKaname on 2009-06-03
I have played Starcraft and Age of Mythology in wine without performance loss. You may try the svn version of wine or tweak it, as gamblor01 said. But anyway, if you are happy playing it inside vmware, its fine I think.

> You could just try to convert your physical machine to a virtual image and then run it with VMware. Try their free converter:

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

I didn't know about that... I will give it a look (just curiosity). I used to run my physical Windows installation inside vmware, but now I don't run windows at all...

---

### Post by Paperfairy on 2009-07-05
> **matthewbpt said:**
> What kind of ipod do you have? what generation as well

iPod Touch, second generation.

> **LepeKaname said:**
> I have played Starcraft and Age of Mythology in wine without performance loss. You may try the svn version of wine or tweak it, as gamblor01 said. But anyway, if you are happy playing it inside vmware, its fine I think.

How would I go about tweaking wine?

---

### Post by LepeKaname on 2009-07-05
> **Paperfairy said:**
> How would I go about tweaking wine?

What game/application do you want to run with wine? The way to tweak it can be very different according to which app / game you want to run.

This is the usual way to run wine apps / games inside Ubuntu:

I will assume that you already tried with the wine stable version (default repositories) and it failed.

If so, try installing the last version of wine:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

You also have to give it a look to the wine [ApplicationDatabase]("http://appdb.winehq.org/") to see what can you expect of the game or application you are trying to run under wine.

One way to tweak it is through the wine configuration GUI, you can find it in you menu: 

Applications -> wine -> Configure wine

There you could load native windows libraries, change video settings, etc.

---

### Post by gamblor01 on 2009-07-06
> **LepeKaname said:**
> What game/application do you want to run with wine? The way to tweak it can be very different according to which app / game you want to run.

It definitely depends on the game that you are using.  I specifically had to tweak Steam/HL2 based games to run and that mainly involved me passing arguments to Steam when it starts (to use a larger amount of RAM for the game's heap as well as forcing it to use DirectX 8.1 instead of 9.0).  Visiting the appdb and searching for the game you wish to play (Starcraft?) as LepeKaname suggested is definitely a good start.  They may have information there about how to make the game run more smoothly.

You could try using winecfg to set some of DLL files as native/builtin, but I have never found that helpful.  In fact, it always seem to hurt performance on my system.  In fact, installing DirectX 9.0c in my wine prefix totally hosed my performance in Team Fortress 2.  Sticking with the original implementation from Wine has been much better on my system.

Finally, you can run "wine regedit" and try adding the Direct3D key.  Try adding the registry keys one by and one and try the different values to see if it helps performance or not.  You might try changing DirectDrawRenderer, OffscreenRenderingMode, VideoMemorySize, etc.

See [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) for more information on the registry keys.

---

