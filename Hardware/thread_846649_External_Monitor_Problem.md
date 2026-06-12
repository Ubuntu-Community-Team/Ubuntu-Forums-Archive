---
title: "External Monitor Problem"
date: 2008-07-01
forum: Hardware
---

### Post by matix on 2008-07-01
Hi, I'm new here and i wanted to ask for a bit of help with an external monitor, i have a laptop dell xps m140 and im trying to connect and external monitor Dell E172EFPB to it. my laptop recognizes the monitor, and the moment i put the setting to expend the monitor at the settings tab in display the monitor turns on and shows me my background of my laptop but after 2 second the screen goes black but the button where you see if the monitor is on stays green indicating on...anyone know why the screen goes black and how to fix it? am i missing something? your help would be much obliged...

---

### Post by acron1 on 2008-07-01
It sounds like a refresh rate problem. You can edit your xorg.conf file and use a lower vertical refresh rate ( be conservative if you don't know the right one for you external monitor ex try 60Hz).
Good luck

---

### Post by matix on 2008-07-01
> **acron1 said:**
> It sounds like a refresh rate problem. You can edit your xorg.conf file and use a lower vertical refresh rate ( be conservative if you don't know the right one for you external monitor ex try 60Hz).
Good luck

how do i edit that?:confused: I'm sorry if I'm being a nuisance, it's just i don't know much about computers...:(

---

### Post by matix on 2008-07-01
yeah i tried doin tha but, it still stays of, it's in 60Hz, what should i do?

---

### Post by acron1 on 2008-07-01
> **matix said:**
> yeah i tried doin tha but, it still stays of, it's in 60Hz, what should i do?

I am not sure I am following you. Did you edit your xorg.conf file and set the external monitor to 60Hz?
While the monitor is showing a black screen press the menu bottom on your monitor and read which v:(rate) is in and report back to us.

---

### Post by matix on 2008-07-01
> **acron1 said:**
> I am not sure I am following you. Did you edit your xorg.conf file and set the external monitor to 60Hz?
While the monitor is showing a black screen press the menu bottom on your monitor and read which v:(rate) is in and report back to us.

when i go to the setting tab in display u can set it up there to 60Hz, but it's already at that, and even if i press the menu button on my monitor it stays black:(

---

