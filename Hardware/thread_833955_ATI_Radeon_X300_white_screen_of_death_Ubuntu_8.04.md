---
title: "ATI Radeon X300 white screen of death Ubuntu 8.04"
date: 2008-06-19
forum: Hardware
---

### Post by Esarge on 2008-06-19
Hi,
I recently installed Ubuntu 8.04 on an IBM T43 laptop which has an ATI Radeon X300. On startup I get the login screen then, when I login, I get a gently yellow screen with nothing at all displayed. I believe this is known as the white screen of death.

All I can manage to get is to change the session to Restricted terminal.

In my efforts to solve this problem I have:
1. Disabled the Composite extension in xorg.conf
2. Followed the instructions in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to install the fglrx driver. Unfortunately I followed the 7.04 instructions which has installed Jockey.
3. Followed the same instructions for 8.04.

Nothing about this problem has changed.

I will post my xorg.conf and the log very shortly.

Note that this happens to be installed on a USB drive but I doubt that makes a difference.

Thanks for any help.

Update: Files attached

---

### Post by treecheetahdolo on 2008-09-04
When i had the white screen problem i found a solution that worked for me. 
I **uninstalled** [COLOR="Red"]**fglrx**[/COLOR] and [COLOR="Red"]**Xserver-xgl**[/COLOR]

Works like a charm now ;)


My problems with ATI Radeon X300 video card were "Cant change screen resolution, slow 3d graphics, and white screen when loggin in)

---

