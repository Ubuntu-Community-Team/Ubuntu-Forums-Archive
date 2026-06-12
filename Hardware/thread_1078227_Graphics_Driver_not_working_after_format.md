---
title: "Graphics Driver not working after format ?"
date: 2009-02-23
forum: Hardware
---

### Post by robcornes on 2009-02-23
Hi Everyone,

Ok so ive been doing some more work in ubuntu lateley and love it however the only snag or confusion i have is that i cant get the desktop effects to work,

I have gone to appearance and tried to enable Extras however i get the message "cant enable desktop effects"

I have 64 bit ubuntu on Toshiba Satelitte M305-S4848 this has worked fine before and i have installed compiz etc however it doesnt work since a format. i believe its an intel graphics card however if someone could help me check that i would appreciate it. I beleive its a driver issue as google earth wont load either, can someone please point me in the right direction a) the correct driver i need or b) do i need to change some otger settings.

Many thanks in advance

Rob

---

### Post by 73ckn797 on 2009-02-23
Go to Applications/Accessories/Terminal and enter into terminal:

```
lspci
```You will find info on the graphics card listed there.

Have you tried System/Administration/Hardware Drivers? If there are any restricted drivers needed for your graphics card, it would be listed there. Use the recommended driver.

---

