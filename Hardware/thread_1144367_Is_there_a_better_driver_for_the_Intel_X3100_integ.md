---
title: "Is there a better driver for the Intel X3100 integrated graphics chip?"
date: 2009-04-30
forum: Hardware
---

### Post by Noise... on 2009-04-30
I know the Windows drivers are fairly advanced - allowing the chip to run some really graphic-intense games like TESIV: Oblivion. However, the Linux version of the drivers are terrible, lacking even DirectX 8 support, and having serious trouble with DirectX 7, and even OpenGL.

Is there a better driver out there that's more comparable to the Windows driver? My games should all work in Wine, but crash due to the graphics not being supported by the chip.

---

### Post by stchman on 2009-04-30
> **Noise... said:**
> I know the Windows drivers are fairly advanced - allowing the chip to run some really graphic-intense games like TESIV: Oblivion. However, the Linux version of the drivers are terrible, lacking even DirectX 8 support, and having serious trouble with DirectX 7, and even OpenGL.

Is there a better driver out there that's more comparable to the Windows driver? My games should all work in Wine, but crash due to the graphics not being supported by the chip.

Linux drivers do not do DirecX at all.  You can play some DX games through WINE, but that is really hit or miss.

The x3100 is mainly designed for laptops.  The x3100 is not what you call a gamers card.

For Linux openGL implementation on that card use Mesa instead.

If you are a hardcore gamer that plays lots of Windows games I do recommend you stick with Windows.  You can dual bootand use Windows for gaming and Ubuntu for everything else.

There are a lot of cool native Linux games like Nexuiz, Open Arena, Alien Arena that look and play great.

---

### Post by Noise... on 2009-04-30
That's the thing - I'm not a hardcore gamer. I basically want to play TES III:Morrowind, and a few Steam games (HL2, HL2:DM, Garry's Mod). Morrowind is installed, and starts just fine, but once I get just past the beginning of the game, it crashes (I'm guessing because it can't render the water...)

HL2 starts, and is playable, but does get pretty low FPS at times.

DM also starts and runs, but lags pretty severely.

Gmod will start, but will only display a black screen.

Is it only the driver for the X3100 that can't display Direct X, or is Direct X just not available in Linux at all?

---

### Post by stchman on 2009-04-30
> **Noise... said:**
> That's the thing - I'm not a hardcore gamer. I basically want to play TES III:Morrowind, and a few Steam games (HL2, HL2:DM, Garry's Mod). Morrowind is installed, and starts just fine, but once I get just past the beginning of the game, it crashes (I'm guessing because it can't render the water...)

HL2 starts, and is playable, but does get pretty low FPS at times.

DM also starts and runs, but lags pretty severely.

Gmod will start, but will only display a black screen.

Is it only the driver for the X3100 that can't display Direct X, or is Direct X just not available in Linux at all?

WINE takes care of DX rendering as Linux does not support DX at all being that it is a Microsoft proprietary rendering.  So DX is emulated since the WINE folks do not have the source code to DX.

As I said if you want to play Windows games and WINE does not support them, run Windows!!!  I don't know what else to tell you.

Remember the ability to run native Windows software on Ubuntu is quite a feat.  The problem is is that now people expect that WINE should run 100% of Windows apps 100% perfectly.

If you had a Windows machine would you expect to be able to run native Linux software?!!!!

---

### Post by hardyn on 2009-04-30
Not really; Wine might be getting close like said above hit or miss.

DirectX is not an open standard, its Ms's 3D library.  

Like said above, if you are gaming you might want to think about a dual boot. Linux is not a windows replacement.

---

### Post by Noise... on 2009-04-30
Meh. I guess my Windows partition stays for now. :(

---

### Post by stchman on 2009-04-30
> **hardyn said:**
> Not really; Wine might be getting close like said above hit or miss.

DirectX is not an open standard, its Ms's 3D library.  

Like said above, if you are gaming you might want to think about a dual boot. Linux is not a windows replacement.

That seems to be totally missed by most new folks.

Ubuntu != Windows

I sometimes wish WINE was never invented as there are TOO MANY people that judge Ubuntu solely on it's ability to run Windows apps.

---

### Post by hardyn on 2009-04-30
I think wine is great, but it has to be respected for what it is.

I have had very good luck running some basic little appies; things like micro controller development suits etc. small programs.  I have had very limited luck running anything like a game.

i am happy to see that a few of the smaller game design houses are starting to include native linux builds in the lineup.  I bought a game for the first time in many many years a few weeks ago; a native linux build. 




> **stchman said:**
> That seems to be totally missed by most new folks.

Ubuntu != Windows

I sometimes wish WINE was never invented as there are TOO MANY people that judge Ubuntu solely on it's ability to run Windows apps.

---

### Post by Noise... on 2009-04-30
> **stchman said:**
> That seems to be totally missed by most new folks.

Ubuntu != Windows

I sometimes wish WINE was never invented as there are TOO MANY people that judge Ubuntu solely on it's ability to run Windows apps.

Don't get me wrong - I'm not judging Ubuntu on it's ability to run a few games that were made for Windows. I love Ubuntu, it's performance, and stability. Not to mention the fact that everything about it just works. I want the few games to work because I want to switch to Ubuntu 100% - not because I'm trying to judge Ubuntu based on how it runs Windows programs.

---

### Post by hardyn on 2009-04-30
Totally understand that... it just becomes a point of contention when people bring up MS proprietary technologies and ask why not under linux.  

How well wine does work however is pretty mind-blowing... reverse engineering the windows API successfully is pretty amazing, straight up.

gaming for the foreseeable future will remain the domain of windows and more-so consoles.  and in all honestly you well get better performance running the games under windows anyway.


> **Noise... said:**
> Don't get me wrong - I'm not judging Ubuntu on it's ability to run a few games that were made for Windows. I love Ubuntu, it's performance, and stability. Not to mention the fact that everything about it just works. I want the few games to work because I want to switch to Ubuntu 100% - not because I'm trying to judge Ubuntu based on how it runs Windows programs.

---

