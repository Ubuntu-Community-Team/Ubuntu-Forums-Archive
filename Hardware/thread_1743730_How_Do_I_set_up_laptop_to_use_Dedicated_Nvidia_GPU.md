---
title: "How Do I set up laptop to use Dedicated Nvidia GPU and NOT integrated GPU?"
date: 2011-04-29
forum: Hardware
---

### Post by Flanmaster on 2011-04-29
I am receiving an Asus Laptop for my birthday:

[http://www.amazon.com/N53SV-XE1-15-6-Inch-Versatile-Entertainment-Aluminum/dp/tech-data/B004KNVK84/ref=de_a_smtd](http://www.amazon.com/N53SV-XE1-15-6-Inch-Versatile-Entertainment-Aluminum/dp/tech-data/B004KNVK84/ref=de_a_smtd)

Upon reading I find that it has both integrated and dedicated GPU to facilitate powersaving when not requiring Highend GPU functions.

I use ubuntu but am not much more than an "end user".  Is there a way to force this laptop to use only the Nvidia Dedicated GPU for linux? i.e. to disable the integrated?  Or has ubuntu already figured out how to work with this without any configuring necessary?

Thanks

---

### Post by Flanmaster on 2012-01-04
This information is in case any one else has the same question.

No one answered my question in any of the linux forums so after much research I found the bumblebee project for opensource support of nVIda optimus.  you have to prefix the start of every 3d app with "optirun" but it provides some support to actually use the nVidia capabilities within linux.

the bumblebee proect has been changed to the Ironhide project

[https://github.com/MrMEEE/ironhide/](https://github.com/MrMEEE/ironhide/)

here are some links on installation and also some issues faced by others during process:

[https://github.com/MrMEEE/ironhide/issues/9](https://github.com/MrMEEE/ironhide/issues/9)

[https://github.com/MrMEEE/ironhide/issues/196](https://github.com/MrMEEE/ironhide/issues/196)

---

