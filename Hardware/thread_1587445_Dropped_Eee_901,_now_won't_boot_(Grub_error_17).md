---
title: "Dropped Eee 901, now won't boot (Grub error 17)"
date: 2010-10-03
forum: Hardware
---

### Post by probably pebkac on 2010-10-03
Oops. I dropped my Eee. Now I need help :(

It fired up fine immediately after dropping it. Then whilst in Firefox the screen suddenly went black (though still illuminated). Shut it down and rebooted. Message: "GRUB Loading stage1.5. GRUB loading, please wait... Error 17". Ohnoes! And I can't get past that.

I've tried the following:
- shutting off all available devices (LAN, WLAN, camera, Bluetooth) in the Bios
- removing the 16GB slave SSD in the Bios
(Neither of the above have any effect)
- removing the 4GB master SSD in the Bios
(This just prevents anything happening)
- booting from the USB stick with which I originally installed Ubuntu (this is 9.04 by the way)
(This gets to the point of starting to display the desktop, then locks up)

One odd point is that on powering on the machine the speaker now makes two clicks. No idea what that might infer.

Does anyone have any idea as to anything useful I might try? I've no problem with reinstalling the OS but - inevitably - I've got some non-backed-up stuff on the 16GB SSD (yay, go me).

Thanks.

---

### Post by ajgreeny on 2010-10-03
It may not be possible, but if you can remove the SSD from the machine, and then refit it again, you may be lucky.  It sounds as if it has become dislodged, and therefore disconnected from the system.  At least it is an SSD, so it should still have all your files on it even if something else in the machine has broken, so you should be able to get the files back, I would think, without too much trouble.

You're perhaps lucky it wasn't an ordinary spinning disk!

---

### Post by probably pebkac on 2010-10-03
Thanks. As it turned out I think I'm now OK.

I turned off 'quick boot' in the Bios and it started crashing on the memory check. By some bizarre stroke of luck I'd bought a replacement memory module ages ago but never got round to fitting it... So thin seemed like a good time to try. And, bingo. Booting from the SSD still fails but I have at least managed to boot from the stick and get the files I wanted. Remains to be seen whether the SSD boot error will be fixed by reinstalling Ubuntu or whether that's hosed as well - but at least I've got my data :)

And yes, as it rebooted after hitting the floor I did think "hmm, glad I bought the SSD one instead of the HD version" - and it was at that point that it hung. I think it must have heard me thinking recently about buying a larger netbook...

---

