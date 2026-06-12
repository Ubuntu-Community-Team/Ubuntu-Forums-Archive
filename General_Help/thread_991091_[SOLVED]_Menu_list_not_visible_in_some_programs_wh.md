---
title: "[SOLVED] Menu list not visible in some programs when compiz active."
date: 2008-11-23
forum: General Help
---

### Post by clyde9999 on 2008-11-23
Not able to see menu items (with some programs like aMsn, and NoteEdit) when compiz is active. Menu lists are viewable when compiz is not active. The images to the left of the missing menu names are present, but that is it. It may be a simple fix, but I have not discovered how to make the menu items visible while running compiz.

Ubuntu 8.10 Intrepid Ibex
IBM NetVista 2.4 Gig P-4 cpu
768 meg, ram
Video Card: Nvidia Model P-73

---

### Post by clyde9999 on 2008-11-24
Here is a link to a photo with a visible representation of the problem.
[http://ubuntuforums.org/picture.php?albumid=717&pictureid=2392](http://ubuntuforums.org/picture.php?albumid=717&pictureid=2392)

---

### Post by jhutton on 2008-11-24
I'm having the same problem.  Add to the list kdenlive.

This thread: [http://ubuntuforums.org/showthread.php?t=977745&page=3]("http://ubuntuforums.org/showthread.php?t=977745&page=3")
helped with getting menu and title bars back for most other apps.

We may have to turn off desktop effects.  :(

---

### Post by clyde9999 on 2008-11-26
> **jhutton said:**
> 
We may have to turn off desktop effects.  :(

I have had to do that just to get my work done, I compose music and my music program menu's are not visible with compiz, kind of a bummer since I LOVE compiz.

clyde9999

---

### Post by binbash on 2008-11-26
did you play with compiz plugin > workarounds ?

---

### Post by clyde9999 on 2008-11-26
> **binbash said:**
> did you play with compiz plugin > workarounds ?

I am looking at it right now. Will let you know the effect.

clyde9999

---

### Post by clyde9999 on 2008-11-26
:popcorn: Okay, I did the work around and SUCCESS!!! I am now up and running. Thank you Thank you Thank you. For those with this issue, make sure to do everything on the work around, including adding the following to xorg.conf

> In section "Device" we add line:

Option "RenderAccel" "0"

Wonderful to be up and running again.

clyde9999 (jack)

---

### Post by jhutton on 2008-11-26
Great!  That seems to fix it for me too!  Thanks.
> In section "Device" we add line:

Option "RenderAccel" "0" 

I had read somewhere else that RenderAccel should be set to "TRUE"... but the 0 works for me.  Thanks.

---

### Post by clyde9999 on 2008-11-27
> **jhutton said:**
> I had read somewhere else that RenderAccel should be set to "TRUE"... but the 0 works for me.  Thanks.

I wonder if I should have tried that first, then if it did not work do the rest!!!

Great fix, happy it is working for both of us for sure.

clyde9999:)

---

