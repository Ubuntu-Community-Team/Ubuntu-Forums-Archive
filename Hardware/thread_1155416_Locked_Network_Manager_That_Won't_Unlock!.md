---
title: "Locked Network Manager That Won't Unlock!"
date: 2009-05-10
forum: Hardware
---

### Post by k64 on 2009-05-10
On my Acer Aspire One AOA110-1545 with Ubuntu Netbook Remix on it, everything worked great until this: The application nm-applet (The Network Manager) locked itself, and the password I set for Ubuntu Netbook Remix won't unlock it! How do I get that dang thing unlocked?!?

---

### Post by kerry_s on 2009-05-10
locked itself? i didn't even know it could be locked, can you put a pic?

---

### Post by k64 on 2009-05-12
I mean... It comes up with an "Unlock Default Keyring" prompt; then, it won't unlock the keyring even if I used the password I created, and it also won't respond to the "Deny" button; I deny it, and the prompt still pops up.

---

### Post by kerry_s on 2009-05-12
edit your wireless connection, delete it and create again.

---

### Post by k64 on 2009-05-12
> Edit Your Network Connection, Delete It And Try Again And Exactly How do I do that with that nagging "Unlock Default Keyring" popup occurring with the Network Manager every time I log on?

---

### Post by kerry_s on 2009-05-12
in a terminal:
killall nm-applet

then look in your system menu for connections.

---

### Post by k64 on 2009-05-12
> in a terminal:
killall nm-applet

then look in your system menu for connections

I got up to the first step (killall nm-applet), but when I got up to the system menu to look for connections, the nagging popup reappeared for nm-connection-editor!

---

### Post by Scipio_Publius on 2009-05-12
From command line type 

```
Top
```

Note the PID of nm-applet

```
kill -Kill <PID>
```

Ignore the popup and open terminal

---

