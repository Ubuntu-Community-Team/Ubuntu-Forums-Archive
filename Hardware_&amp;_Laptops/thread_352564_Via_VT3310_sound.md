---
title: "Via VT3310 sound"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by fbnts on 2007-02-03
Hi,

I have just got a new PC and installed Ubuntu again on it.  Everything is going ok, except I cannot get the sound card to work.

The card is a Via VT3310(UAA) integrated card.  When doing lspci I get:

Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

I have googled but theres very little info on this driver.

Has anyone managed to get this to work?


Tom

---

### Post by rojanu on 2007-03-13
have you solved your problem I have the same chipset and no sound
Thanks

---

### Post by fbnts on 2007-03-13
Hi,

Well kind of sorted it - It was indeed detected correctly but not using the standard speaker output.

Try plugging your speakers into the other sockets on the back (I think it was the black socket (bottom right when looking from the back))

I know theres a way to specify which channel to use when outputting audio but not quite sure yet, so this is definitely an interim solution.

Tom

---

