---
title: "HOWTO: iPod synchronization working under Ubuntu 6.06"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by rsk on 2006-07-25
Ok guys after getting a lot of great feedback from you all and others I finally got my freaking iPod nano working under Ubuntu. This probably seems second nature to a lot of you, for you guys, this tutorial is probably retarded. For people just starting out on Ubuntu and are frustrated by RhythmBox (aka: the thing that opens up when you plug your iPod in) not being able to really handle the iPod and not sure what to do, this tutorial is for you:

Well after my long-winded first week with Ubuntu outlined [here]("http://www.breakitdownblog.com/2006/07/22/ubuntu-606-long-term-review/") I got a ton of excellent feedback from folks on how to make my life easier. This post covers one of the tips which was how to get my iPod working with linux using [Amarok 1.4.1]("http://amarok.kde.org/"). It turns out that using Amarok 1.4.1 is going to be the only real way to get this working, real here meaning “usable in an everyday setting”. Rhythmbox, while able to play the music, cannot handle basic podcast subscriptions aparently and definately cannot handle synchronization with the iPod.
 Here’s what I did:[LIST]
[*]Follow the instructions on [this]("http://kubuntu.org/announcements/amarok-1.4.1.php") page
[*]Pop open your software properties dialog:
[[IMG]http://www.breakitdownblog.com/wp-content/uploads/2006/07/software_properties.thumbnail.png[/IMG]]("http://www.breakitdownblog.com/wp-content/uploads/2006/07/software_properties.png")
[*]Add a custom repository that represents the arguments: *deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main*
[[IMG]http://www.breakitdownblog.com/wp-content/uploads/2006/07/kubuntu_repository.thumbnail.png[/IMG]]("http://www.breakitdownblog.com/wp-content/uploads/2006/07/kubuntu_repository.png")
[*]Refresh your repositories
[*]Search for, select and install Amarok 1.4.1 (not the 1.3.9 version from Dapper repository):
[[IMG]http://www.breakitdownblog.com/wp-content/uploads/2006/07/install_amarok.thumbnail.png[/IMG]]("http://www.breakitdownblog.com/wp-content/uploads/2006/07/install_amarok.png")
[*]Go ahead and click through all the unauthorized warnings
[*]Fire up Amarok, click on *Settings > Configure Amarok > Media Devices*
[*]Click *Add Device…* and configure your iPod device, then hit OK:
[[IMG]http://www.breakitdownblog.com/wp-content/uploads/2006/07/configure_ipod_device.thumbnail.png[/IMG]]("http://www.breakitdownblog.com/wp-content/uploads/2006/07/configure_ipod_device.png")
[*]Add some podcasts:
[[IMG]http://www.breakitdownblog.com/wp-content/uploads/2006/07/add_podcasts.thumbnail.png[/IMG]]("http://www.breakitdownblog.com/wp-content/uploads/2006/07/add_podcasts.png")
[*]Select the episodes you want to put on your iPod and click *Transer to Media Device*
[*]Switch to the *Media Device* tab and transfer those items to your device
[*]Enjoy![/LIST]Original Article: [http://www.breakitdownblog.com/2006/07/24/get-ipod-podcast-synchronization-working-on-ubuntu-606/](http://www.breakitdownblog.com/2006/07/24/get-ipod-podcast-synchronization-working-on-ubuntu-606/)

---

