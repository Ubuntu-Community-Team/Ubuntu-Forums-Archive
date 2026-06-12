---
title: "Media buttons"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by danbert on 2006-09-14
I recently installed Ubuntu on my college laptop.  Linux has always been a pain on it since I have no idea what actual hardware is in it most of the time, and it's from a computer manufacturer called Tangent.  Fortunately it does have centrino, and I was surprised at how well Ubuntu ran everything.

Anyways, I digress.  The issue I have had a problem with is getting the media buttons on the front of my laptop to work.  They don't generate any keystrokes, as I have tried to record what number they return.  What I do know is that the Windows program is called EasyButton which apparently is a common name for any button program for laptops, so I haven't been able to locate the program's origin.  However, I do know that the buttons can work in linux.  The laptop has an IOMP which is linux based and exists on an ext2 partition.  The buttons work fine in this, so I assume they can work under any linux environment.

Any help would be appreciated, not that this is a critical function, but it would be a major convenience factor.

---

### Post by UltraMathMan on 2006-09-15
Have you tried mapping them in System->Preferences->Keyboard Shortcuts?

---

### Post by danbert on 2006-09-16
Yes, I have, but as I said, the buttons do not return keystrokes, and the operating system does not consider them part of the keyboard at all.  I believe they are totally software powered.

---

### Post by Melcar on 2006-09-16
Have you tried setting other keyboard layouts?

---

### Post by danbert on 2006-09-18
I don't think you understand, I tried logging the codepoints that the keys returned.  They did not return any codepoints.  As in the operating system doesn't recognize that they are keyboard keys.  I don't know how to map them without software support or some sort of other way to see what they keys are returning.

---

### Post by CrunchyDoodle on 2006-09-18
Just a wild guess here . . . . these buttons may operate through a hardware port in I/O or memory space. In Windows you may be able to notice a port in the Device Manager that seems unusual or is named oddly. This may be how it interacts with Windows and not be emulating key strokes.

Bye.    :cool:

---

### Post by danbert on 2006-10-05
I figured out some more information.  The laptop is apparently a re-branded compal/toshiba based laptop.  The model is probably a satellite though I don't know what the equivallent version is.  The compal easybutton.exe is only available in windows.  Is there any way to emulate this using wine, because I cannot find any way to record the system response to these keys.

---

