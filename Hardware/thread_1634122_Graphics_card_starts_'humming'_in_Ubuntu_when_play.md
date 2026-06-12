---
title: "Graphics card starts 'humming' in Ubuntu when playing"
date: 2010-11-30
forum: Hardware
---

### Post by rizman on 2010-11-30
Hi there,

I've just recently setup a dual-boot system with Ubuntu 10.10 and Windows 7 on my Packard Bell notebook.It has an Nvidia GeForce GT 240M Graphics card with 1024MB of dedicated memory.

Now I'm a casual gamer and lately I've been playing some World of Warcraft. Under Windows, the game runs fine (using DirectX). Under Ubuntu, the game does also run fine (using OpenGL) although with some settings being unavailable. But I guess that's some options which aren't supported by the drivers. BTW I installed the recommended drivers under additional drivers. I guess those are the latest Nvidia drivers.

Anyway, what actually happens is when the game is running under Ubuntu, the Graphics card starts hummming. Like if there was some fan which is permanentely running. This does NOT happen under Windows. Or rather, it is more like a permanent electrical buzz. I hope you get what I mean.

I'd really like to play the game under Linux, because I'm planning to use Ubuntu as my main Desktop, having Windows running only to be able to update my iPhone through iTunes and other stuff which I think don't yet work under Ubuntu. But the humming concerns me as I'm afraid the card might break. 

Also, when watching a Video, the card is silent. It is really only when playing WoW. I haven't tested with any other game yet which uses 3D functionality.

Hope someone can suggest something

---

### Post by The Fiddler on 2010-11-30
Many video cards hum (electrical noise) when running intensive applications. This doesn't mean that your card is about to break (but it might imply that it is built with sub-par materials).

As a potential workaround, open nvidia's control panel (nvidia-settings), head to the GLX/OpenGL section and make sure the "vsync" setting is enabled. By limiting OpenGL applications to your monitor's refresh rate (60Hz), your system will run cooler and you will reduce those buzzing noises.

Alternatively, check for a "vsync" option in the 3d settings configuration inside WoW.

---

### Post by rizman on 2010-11-30
Hey Fiddler,
Thanks for the answer. However, I already set the vsync option both inside the game and inside the NVidia Settings with no change in behaviour.

I do understand that an electrical noise could be caused by sub-par materials. However, the noise is only audible when running the game under Ubuntu, not under Windows. Hence my concern. Maybe it is a driver related issue? Maybe the driver is somehow making the card run a max power under Ubuntu whereas under Windows the power/voltage whatever is better managed?

---

