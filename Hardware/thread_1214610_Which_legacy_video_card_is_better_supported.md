---
title: "Which legacy video card is better supported?"
date: 2009-07-16
forum: Hardware
---

### Post by blueturtl on 2009-07-16
Hi.

I'm building a computer from older parts and I have two video cards to choose from.

Candidate #1 is an nVidia RivaTNT2 with 32 megabytes of video memory from an unknown manufacturer.

Candidate #2 is a Matrox Millennium G400 with 16 megabytes of video memory (Matrox builds their own cards).

Reading reviews on the net I have come to the following conclusion:
The Matrox video card will have better 2D/3D image quality. 3D rendering speed is about equal (if it works), except that when more memory is used the TNT2 has the advantage.

I don't plan on doing anything 3D with these (although if that would work, I would count that a bonus). What I'm really interested in is Linux support. As I understand it, Matrox is supposed to have a working open-source driver. The TNT2 used to be supported by nVidia's propriatory driver, but probably isn't so any more.

So with this in mind I'm leaning heavily toward the Matrox card. Can anyone with either of these cards tell me if and how they work under Linux today?

Thanks.

---

### Post by blueturtl on 2009-07-17
Bump. Anyone?

Maybe this is the wrong place to ask. After all not many Ubuntu users probably carry this old hardware any more. In any case, I'm going to find out soon enough.

---

### Post by blueturtl on 2009-07-31
I went with Matrox.

Seems to work really well. Video playback gave me some trouble but after installing /dev/mga_vid that is also good.

No other configuration necessary and glxgears runs so I suspect OpenGL is good.

---

