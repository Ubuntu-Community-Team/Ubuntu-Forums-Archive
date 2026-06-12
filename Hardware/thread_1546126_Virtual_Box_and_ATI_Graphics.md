---
title: "Virtual Box and ATI Graphics"
date: 2010-08-04
forum: Hardware
---

### Post by handyguy33 on 2010-08-04
Hi all. I know this is a Windoze type thing so please just hold the criticism until after it's solved and then ream me to your hearts content.

First of all, I have an Acer Aspire 5551. I installed Ubuntu 10.04 on it and it performs wonderfully. I need Windoze for school so I put XP in virtual box and again, slick as anything. my problem is this: there are no XP drivers for the video card in this laptop. It's an ATI Mobility Radeon 4200 HD. I've tried all the Windoze related sites and forums but I'm still stumped. I'm just hoping somebody can point me towards a solution.

Thanks...

---

### Post by waynefoutz on 2010-08-04
> **handyguy33 said:**
> Hi all. I know this is a Windoze type thing so please just hold the criticism until after it's solved and then ream me to your hearts content.

First of all, I have an Acer Aspire 5551. I installed Ubuntu 10.04 on it and it performs wonderfully. I need Windoze for school so I put XP in virtual box and again, slick as anything. my problem is this: there are no XP drivers for the video card in this laptop. It's an ATI Mobility Radeon 4200 HD. I've tried all the Windoze related sites and forums but I'm still stumped. I'm just hoping somebody can point me towards a solution.

Thanks...



You don't need to install a video driver, it will use your Linux driver. To get the most out of it, start XP in Virtualbox, click on "devices" and "install guest additions." This will update the XP driver and let you change resolution and video settings. Also, you need the version from virtualbox.org and not the crippled version found in the repositories in order to do this.

---

### Post by handyguy33 on 2010-08-07
Awesome! Thanks for the quick response.
:)

---

