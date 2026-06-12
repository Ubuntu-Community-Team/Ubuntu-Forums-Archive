---
title: "Suspend help"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by z-two on 2007-05-26
Hi, I've just got a new laptop (Asus A8Js) and installed feisty (amd64).
I'm trying to get the suspend to ram working. From searching the internet I am getting more than a little confused.

Out of the box ubuntu would give me a plain black screen (with cursor) when restoring from the suspend. I installed the package uswsusp and suspend2-userui.

Doing this meant I could successfully suspend using "s2ram -f". Unfortunately the suspend button within gnome still gives me the black screen.

I have now also installed the package powersaved, allthough I'm not entirely sure what this is doing at all.

Thanks for any help you could give me. Maybe someone wouldn't mind giving me a brief idea of what each of these packages are actually for, as it really has confused me.

Thanks again.

Matt.

---

### Post by Pragmatist on 2007-05-26
First see if these help:

[https://wiki.ubuntu.com/FeistySuspendOverview?highlight=%28suspend%29](https://wiki.ubuntu.com/FeistySuspendOverview?highlight=%28suspend%29)
[https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto)

There are some other wiki entries listed here:
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles)

---

### Post by z-two on 2007-05-26
Ahhh thankyou. Somehow I had managed to miss the first link you posted. I do feel that I've gained a bit more of an understanding for the system.

I guess my question now has changed a little. What i need to do is get control of suspending and hibernating in gnome handed over to uswsusp. 

[https://wiki.ubuntu.com/FeistySuspendOverview?highlight=%28suspend%29](https://wiki.ubuntu.com/FeistySuspendOverview?highlight=%28suspend%29) shows the selection process, but I don't know how to prevent it from allways using powermanagement-interface.

I'm tempted to try and edit the hal scripts for suspending and hibernating. I'd quite like to see if there are any better options though?

Thanks

Matt

---

