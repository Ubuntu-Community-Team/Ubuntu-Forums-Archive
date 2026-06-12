---
title: "geforce4 drivers question"
date: 2009-04-30
forum: Hardware
---

### Post by 900donuts on 2009-04-30
my cpu doesn't support sse so I use an old set of drivers and a geforce 4400ti. when 8.10 first came out I saw on the official download page that the official geforce4 drivers weren't supported so I didn't upgrade. Has any thing changed since then? do the drivers for geforce 4 work now in 8.10 or 9.04?

---

### Post by garythegoth on 2009-04-30
Dosent 96.xx work with GeForce 4 based cards in 8.10?

According to nVidias driver section on their site, 96.xx supports the GeForce 4 MX, which is basically a rebranded GeForce 2 Ultra.

---

### Post by 900donuts on 2009-04-30
when 8.10 first came out 96 series drivers didn't work. What I want to know is if I upgrade to 8.10 or 9.04 would I have 3d acceleration even with my non-sse athlon cpu

---

### Post by garythegoth on 2009-04-30
> **900donuts said:**
> when 8.10 first came out 96 series drivers didn't work. What I want to know is if I upgrade to 8.10 or 9.04 would I have 3d acceleration even with my non-sse athlon cpu

I really dont see what SSE has to do with your GeForce 4. Care to explain in a little more detail?

---

### Post by 900donuts on 2009-05-01
as far as I know all drivers after 96.xx require a cpu that supports sse (I forget what it does look it up on wikipedia) my cpu is a athlon tbird (a.k.a. OLD)

---

### Post by garythegoth on 2009-05-01
> **900donuts said:**
> as far as I know all drivers after 96.xx require a cpu that supports sse (I forget what it does look it up on wikipedia) my cpu is a athlon tbird (a.k.a. OLD)

But AMD chipsets have 3DNow! Which is the equivalent of SSE.

Hell my cousin has a K6 with a GeForce 5200 running Intrepid with the 173 drivers. I really dont see why there would be an issue with a Thunderbird and a GeForce 4.

---

### Post by 900donuts on 2009-05-01
is he doing any 3d graphics?

blender, screensavers, games? 

trust me when I used the latest drivers on my rig I would get back illegal instruction errors when I tried to do any thing that uses 3d graphics.

K6 is like a P1 isn't it? what distro is he running cause I've i've bben look in for a win 95 replacement.

---

### Post by garythegoth on 2009-05-01
> **900donuts said:**
> is he doing any 3d graphics?

blender, screensavers, games? 

trust me when I used the latest drivers on my rig I would get back illegal instruction errors when I tried to do any thing that uses 3d graphics.

K6 is like a P1 isn't it? what distro is he running cause I've i've bben look in for a win 95 replacement.

No its more like a slightly more powerful Pentium II, and yeah he can use 3D for some games (nothing to heavy obviously). Screensavers yeah but theyre **SLOW**.

---

### Post by 900donuts on 2009-05-01
> No its more like a slightly more powerful Pentium II, and yeah he can use 3D for some games (nothing to heavy obviously). Screensavers yeah but theyre SLOW

hmm wierd 

well its the weekend so I guess I can fire up clonezilla back up my hard drive and try upgrading

---

### Post by garythegoth on 2009-05-01
> **900donuts said:**
> hmm wierd 

well its the weekend so I guess I can fire up clonezilla back up my hard drive and try upgrading

Good luck.

---

### Post by ofb on 2009-05-02
900donuts, please report back on this thread to let us know how it worked out.

For others, here's the 8.10 release note about Nvidia and SSE.
[http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

There's nothing about that in the 9.04 notes, but it seems addressed to people who could go to 8.10.

3DNow! is not equivalent to SSE in this case.

With my own Duron 950 with GeForce4 MX440SE I got display failures during install of 8.10. Took a while to find out about the legacy Nvidia issue, and revert to 8.04. The 8.10 LiveCD had worked fine.

Legacy Nvidia issues can be a mixed bag, depending on hardware. For instance I've tried a minor upgrade to FX5200 in 8.04 and lost 3D capability on this box.

---

### Post by ofb on 2009-05-10
Installed Jaunty on a P3 (has SSE) Geforce2 MX400 with no trouble. GoogleEarth 5 works fine. Pulled that drive and placed it in a Duron (no SSE) with Geforce4 MX440SE, and GoogleEarth still works fine. Both are using the 96.x driver.

So far so good. Next I have to find my FX5200. The Duron with MX440SE or FX5200 would not even boot a fresh 8.10 install. The Duron with MX440SE runs 3D on 8.04 fine, but the FX5200 would crash on 3D apps.

So yes, 9.04 has at least some improvement for the 8.10 problem of legacy Nvidia sans SSE.

---

### Post by ofb on 2009-05-19
Found the FX5200. Put the Jaunty drive in the Duron box, enabled the recommended 173.x driver, and got 1000 fps.

The older, slower MX440SE using its recommended 96.x driver gets 1600 fps, just like it does under 8.04.

So while arguably there's some improvement, as 8.04 will not do 3D at all with the FX5200 & Duron, the framerate has dropped to *less than half* what it should be.


I was going to try an ATI 9600XT as well, but a search through the forums reveals ATI has similarly jetisoned support for legacy drivers. Including hardware that is only three years old.


EDIT -

For kicks I put the FX5200 in the P3 450, which has SSE.

9.04
4950 frames in 5.0 seconds = 989.949 FPS
4945 frames in 5.0 seconds = 988.956 FPS
4949 frames in 5.0 seconds = 989.773 FPS
4947 frames in 5.0 seconds = 989.398 FPS

8.04
5156 frames in 5.0 seconds = 1031.116 FPS
5236 frames in 5.0 seconds = 1046.995 FPS
5249 frames in 5.0 seconds = 1049.722 FPS
5237 frames in 5.0 seconds = 1047.353 FPS

The much older Geforce2 MX400 that box had got around 700fps. There's no way the FX5200 should be so low. What did Nvidia do to the 173.x driver?

---

### Post by 900donuts on 2009-05-19
oh crap sorry about not reporting back (very bad habit of mine)

I managed to upgrade successfully turns out all they did was change the name of the driver packages. geforce4 cards work fine with their recommended 96.x driver because it doesn't require sse unlike the recommended drivers for geforce5 and up.

> The much older Geforce2 MX400 that box had got around 700fps. There's no way the FX5200 should be so low. What did Nvidia do to the 173.x driver?
"according to Wikipedia" geforce5 card especially the 5200 are inferior to geforce4 cards in terms of muscle

---

### Post by 900donuts on 2009-05-19
sorry for the double post but I have a question about the drivers that need sse

is 3d acceleration the only thing that is broken? does 2d and opengl still work? 

The reason I ask is that I have an OLD slotA athlon 800mhz on my workbench and I'm trying to turn it into a crude dedicated boxee box. the only spare card I have that has video-out and OpenGL is a Geforce FX 5200. On that old processor 3d acceleration isn't going to work, but I'm wondering if tv-out and 2d acceleration would still work?

EDIT: never mind all opengl is disabled without sse one drivers that require sse

---

### Post by ofb on 2009-05-20
Wikipedia is generally correct. Exception here is the MX440SE was the low-end GeForce4, similar to how the FX5200 is the low-end of its line. Under Windows, which doesn't care about SSE, I've found the FX5200 is definitely the faster of the two for 3D gaming.

I *think* when I tried the FX5200 under 7.10 it was around 2200fps, but that's memory.

Anyway, back to now: 3D sans SSE technically works on the legacy nvidia drivers as of 9.04. It's just very poor for the FX5200. OpenGL sans SSE works on the 96.x driver for the GeForce4.

I'll add that the liveCDs of PCLOS 2009 and minime 2008 won't even boot the P3 with that FX5200. Mandriva liveCD boots, but cannot see the card. I've never had anything but great video detection from that distro family before. Add all the unhappy posts about FX5200 for various distros, and I'd suggest you ask around locally to see who has an old GeForce4 they can give you instead.

---

