---
title: "[SOLVED] Closing LID -&amp;gt; Do Nothing"
date: 2008-12-28
forum: Hardware
---

### Post by Vernum on 2008-12-28
I want my notebook to do exactly nothing, when i close the lid.
To achieve that i tried to rename lid.sh and make it unexecutable. (chmod -x lid.sh)

But if i close the lid, it ****** (sorry) does a standby. Why? Best part is, i cant wake it up from standby. 

So, i just want kubuntu to do NOTHING, when the lid closes. How do i do that?

---

### Post by sigurnjak on 2008-12-28
Do you have a little switch on the bottom of your sceen and laptop body . If you do it is mechanical way of shutting down a screen . You may have to somehow disable it  or go into bios to see is there a way to bypass it .

---

### Post by Vernum on 2008-12-28
My god. I am so stupid. I just used the ordinary KDE energy-options and i could choose "ignore" on this event.
I was so accustomed to edit config files and scripts, lol.

Thanks anyways. ;)

---

