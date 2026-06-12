---
title: "Cairo-dock problems..."
date: 2008-10-14
forum: General Help
---

### Post by Superbuddy2007 on 2008-10-14
Ok..im kinda new to the cairo-dock app...how do i get rid of the rectangle around the dock?:(:(

---

### Post by overdrank on 2008-10-14
> **Superbuddy2007 said:**
> Ok..im kinda new to the cairo-dock app...how do i get rid of the rectangle around the dock?:(:(

Hi and welcome, are you using compiz? If not you may look here
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by Superbuddy2007 on 2008-10-15
Yes i have compiz fusion but i dont know how to activate it for the dock or any of the plug-ins

---

### Post by MickS on 2008-10-15
You only have to have Compiz running, Cairo looks after itself from then on, least that's how it is on mine.

Mick

---

### Post by Superbuddy2007 on 2008-10-15
ok, i tried using avant windows manager, but when i activated the dock through Alt+F2 i ran it through a terminal and i got this message.

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by ChimpofDOOM on 2008-10-16
Yeah, what it's essentially saying is that you need to start up compiz.

If Compiz is installed run the following command in terminal:
> 
compiz-tray-icon

That should place a Compiz icon on your taskbar. Right click that icon and select GL Desktop to run it.

Chimp

---

### Post by accaflacca on 2009-10-14
i had the same problem. go under right click the dock>Cairo-Dock>Configure and click on the "system" icon. at the bottomof the page, check "Emulates composition with fake transparency?" box and all should be well, even without compiz

---

