---
title: "Marvell 88SE9128: live CD does not work from IDE CD drive"
date: 2010-06-02
forum: Hardware
---

### Post by unprovoked on 2010-06-02
I have a ASRock X58 Extreme 3 motherboard with Marvell 88SE9128 SATA3 controller.  

The IDE controller is also controlled by the 88SE9128.  When I try to run the live CD from an IDE CD drive attached to the 88SE9128, the live CD hangs, even in failsafe mode.  The error is always:

[INDENT]"Unable to find a medium containing a live filesystem"[/INDENT]

The same disc works on a different system, so it is not a burning error.  The same error occurs on my ASRock with different IDE cables, different CD drives, and with all other storage devices unplugged.  

I was able to install Windows 7 and play recent 3D games on this machine, so I know the machine is OK.  But I cannot run the ubuntu live CD.

There are other people with the same motherboard with the same problem.  See: [http://www.asrock-users.com/post-893.html](http://www.asrock-users.com/post-893.html) for further discussion.  Best guess is a missing inbox driver for the Marvell 88SE9128.  

Does anyone know of a workaround?  Or perhaps it will be supported in the future?  I'm sorry if I posted this to the wrong board.

---

