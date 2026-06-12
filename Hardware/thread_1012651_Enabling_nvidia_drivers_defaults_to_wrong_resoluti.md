---
title: "Enabling nvidia drivers defaults to wrong resolution/frequency"
date: 2008-12-16
forum: Hardware
---

### Post by ForABetterWorld on 2008-12-16
I've configured and installed my computer in another place with better Internet and accidentally they had better monitors :). 
When I came home with my box it suddenly wasn't working with my monitor, monitor was behaving as if the resolution or frequency was too high.
I went into recovery mode tried to fix xserv - it restored it to default drivers and default resolution of 800x600 and after restart it worked.
But when I try to enable nVidia drivers again - it again have a not working monitor. I think that it remembered resolution and frequency with which it was first time configured and now after enabling nVidia drivers it's by default with wrong resolution and/or frequency.
Is there a way to fix it?

---

### Post by ForABetterWorld on 2008-12-24
Now I've found how to change xorg.conf so that initial login will show up, but strangely after login it looks like resolution is changed and it again disappears. What is the problem, why after login nvidia changes resolution?

---

