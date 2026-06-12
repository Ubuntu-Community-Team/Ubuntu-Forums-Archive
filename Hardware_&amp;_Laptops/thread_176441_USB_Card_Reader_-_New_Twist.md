---
title: "USB Card Reader - New Twist"
date: 2006-05-14
forum: Hardware &amp; Laptops
---

### Post by markthecarp on 2006-05-14
I have read several threads here on problems with USB Card Readers but none quite match mine.

System background:

It's an "ibuiltit" AMD XP+2000 at 1.67G, 512 ram, some nVidia. Single boots Breezy upgraded from Hoary. I switched to Ubuntu upon the release of Hoary from Debian unstable. My user account has existed on this hard drive since installing Debian sometime in '04. I only retained data file directories while doing the Debian to Ubuntu switch.

Just for kicks I have KDE, fluxbox and Xfce installed.

Former nice behavior:

Three card readers and two cameras; Lexar2.0, Lexar1.1 and Ativa2.0. The numbers refer to the USB version they use not a model number. The cameras are an Olympus D-380 and a Sony P-92. Media includes SmartMedia, Sony MemStick, Sony ProStick and SD. 

Current ugly behavior:

All these combinations worked until very recently. I normally use a card reader once a week or so. Now I'm not getting a desktop popup in any environment. The devices and media are being recognized. But I cannot read them. A user level mount fails, sudo or su - root succeeds but there is still no desktop popup. I can read the files but I have to know exactly what device to mount for this to work. The cameras continue to work fine.

Tests:

I created a new user account named guest. It all works fine when I'm logged in as user guest. Reading /var/log/messages, and watching it with ```
tail -f /var/log/messages
``` reveals the same output regardless of which user is running an X session. It's the same if both users are running X sessions. I have not used anything other than Gnome with user guest.

The Big Question:

So what has happened? User mark I've had forever, doesn't have nice desktop with USB card reader popups. User guest, brand new, has nice desktop USB card reader popups.

-mark

---

