---
title: "Finding out what my hardware is called"
date: 2009-10-22
forum: Hardware
---

### Post by topbayder on 2009-10-22
Hello All,

Im trying to find out what ethernet device i have on my motherboard and also the name/brand/model of sound card and graphics card so i can get the specific drivers for them to work properly because although the hardware works on with ubuntu hard booting they dont on my newly installed xp hard drive in the same machine (this machine). i have no idea how i got them to work with ubuntu think it did it itself or my brother must have done it and he lives far far away.

I have opened the case up and looked at the hardware with my own eyes and cant seem to find anything of use on the boards themselves.

is there a way to perform some kind of search command in linux?

i tried hw info and to be honest i have no idea what that is going on about. somehitng more like:

ethernet = fastethernet xy123
graphics card = nvidia 1234
sound card = soundblaster 123

etc etc. is there any way to do this? this is blowing my mind! think i might have to start fisting myself into oblivion soon!

---

### Post by Ayuthia on 2009-10-22
Usually lspci (or lspci -nn) is used for your pci devices and lsusb is for your USB devices.

You can also look at lshal (or lshal|less for arrow key scrolling - press q to exit) for some information.

Hope that helps.

---

