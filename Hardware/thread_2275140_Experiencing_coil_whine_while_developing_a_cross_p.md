---
title: "Experiencing coil whine while developing a cross platform game (Geforce 750ti)"
date: 2015-04-24
forum: Hardware
---

### Post by jd.russell2006 on 2015-04-24
Hi, I posted here about a week ago when I first installed ubuntu, it gave me some issues because of UEFI and the graphics card trying to load drivers at boot (had to enable nomodeset). I have a repeating issue which I'm not sure is related but may be, on boot I get a message about ACPI PCC probe failed loading version 219. Maybe that's relevant to my problem.

I am a game developer, and recently I've been trying my hand at cross platform development with sfml. Now I am using the latest proprietary driver for my graphics card (750ti) if that is also relevant. The problem is that while running the game I am creating I get coil whine which I am pretty sure is coming from the graphics card. It does this specifically: when I move the images/textures/vertices of the objects being displayed into the viewport of the game I hear a faint high pitched buzzing or humming noise coming from the system.

Anyone have any idea what might be causing this and how to fix this? I can't very well publish a game that may have issues with people's graphics cards causing sound. I've read that coil whine is mostly harmless though.

Edit: I should also mention I'm using ubuntu 15.04

---

### Post by jd.russell2006 on 2015-04-24
Nevermind, sure enough this problem was solved the second I bothered to ask the question. Sorry, I don't know much about this type of hardware problem. Turns out for any other developer that may be reading this that limiting the framerate of the application fixed the problem. What was likely occuring is that my graphics card was being put under heavy load or even maxed out by rendering at a very fast unlimited framerate thus producing the coil whine.

---

### Post by Geert_Jalink on 2015-04-24
I concur with you, but know that something changed in the (k)ubuntu 15.04 drivers perhaps. In my case these drivers for my NVidia make the clock frequency of the video card stuck at maximum causing lots of overheating. So you might just be another case of someone experiencing unwanted high clockfrequency when it isn't necessary. This means it probably will return in the future untill NVidia releases a better driver. Unfortunately (k)ubuntu releases usually by stock are locked to a certain driver. And in this case a unlucky driver.

But just my experience with Kubuntu 15.10 overheating my laptop and NVidia card locked at maximum frequencies even when doing nothing. And yes that made a lot of noise, not coil whining but laptop FAN noise. For example I reinstalled Kubuntu 14.10 and the FAN isn't spinning. The temperatures are fine 43 degrees Celsius.

---

