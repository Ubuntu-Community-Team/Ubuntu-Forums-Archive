---
title: "Graphic BIO's"
date: 2012-02-27
forum: Hardware
---

### Post by UltimateCat on 2012-02-27
Anyone know if the BIO's for the graphics card keeps a log?

And if so...where on the OS might that log be located?

I am investigating graphics issue's ( crashes and freeze's that are not hardware or driver related)  and doing research.
 Any help is greatly appreciated :D

---

### Post by UltimateCat on 2012-03-14
Log found in the /dir/var/logs
Might find more in the Xorg.conf as well but I know for certain that the log is not in the system BIOS because Graphics has it's own BIO"S and chip.

I have learned that the adapter's BIO's takes the form of a read-only memory (ROM) chip containing basic instructions that provide an interface between the video/graphic's adapter hardware and the software running on the system.

The software that makes calls to the video BIOS's can be a stand alone application an OS or the main system BIO"S.

Feel free to chime in or elaborate as I am still racking my brain; studying Linux and other computer books to find out just how graphics that crash can be repaired/restored.

---

### Post by UltimateCat on 2012-03-22
Digging deep into the details of a particular graphics card and determining what type of memory a particular card uses is difficult!

But I have learned that even finding out the above information doesn't always explain why graphics crash.  In some cases it is the fact that the card is not able to handle the memory (UMA)  Universal Memory Architecture

Since their are several different types of memory types and definitions it's hard to tell-
Most cards are 512 MIB.  3D require more memory used for the 3 buffers.

Anyone know;  How do you test a card for it's top performance w/o causing a crash?

Or how do you look at the properties sheet for the card?

---

