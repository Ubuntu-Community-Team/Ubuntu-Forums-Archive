---
title: "Boot problem when mirrored to new partitions"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by alakin on 2009-05-16
I moved over to the *buntu movement about 6 months ago. Prior to that I tended towards Slackware based distros e.g. Vector. I never had a problem using rsync to mirror my exisiting installation prior to upgrade, should the worst happen I would always have a my old installation in full working order and could try again.

Given this background I have taken a similar approach with Xubuntu but cannot get the mirrored copy to boot. The /etc/fstab has been appropriately updated. Grub goes through Stage 2 and the kernel is detected and then I see the initrd being loaded into ram. At the point of looking to load the root filesystem it loses its way i.e. cannot do it. I am only guessing, but is the initrd that was created for my original installation expecting to find the root filesystem in a particular place i.e. I have now moved it to a new place and it does not know this. If this is the case how do I recreate a fresh initrd from my existing installation that will work with the new installation? If not, any idea what is going wrong?

Thanks.

Alan

BTW Just noticed that my details are not up to date - I am using Intrepid and looking to upgrade to Juanty.

---

