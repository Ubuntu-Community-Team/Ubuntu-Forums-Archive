---
title: "Would my drivers work If: AMD Mobility Radeon HD 4225/4250 Driver"
date: 2013-11-25
forum: Hardware
---

### Post by samgabbay on 2013-11-25
if i install xubuntu or a xfce desktop. would my drivers work fine?

---

### Post by Bashing-om on 2013-11-25
samgabbay; Hi !
With that graphics card your options are limited.
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

What it boils down to is you use the open source drivers OR install version 12.04.1 to use the proprietary drivers.

Sad but;
[INDENT][INDENT]that is the way it is
[/INDENT][/INDENT]

---

### Post by samgabbay on 2013-11-25
Were can i find ubuntu 12.04.1?

---

### Post by Bashing-om on 2013-11-25
samgabbay;
Version 12.04.1 is available :
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
continued support 'till 2017 !

Just bear in mind, you may "upgrade" that kernel to the kernel with in raring and later, in your case do not. To run the proprietary drivers you must keep that X-server version installed in 12.04.1

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

