---
title: "Compal FL90 X-windows installation problems"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by mfleming on 2007-08-09
Ubuntizens,

I'd really appreciate help getting Ubuntu 7.04 to work on my shiny new Compal FL90 lappy. This is a Santa Rosa system with an Nvidia 8600GT video card.

Initially the installation disk didn't get very far into the boot, failing with a "Busy box...tty.." etc message. I was able to get past that by including an all_generic_ide boot option. Now I get to the point of starting the X-server. The X-server is apparently trying to use an Nvidia driver from the installation image, and this driver doesn't work. An Nvidia driver, which I think would work, is available from the Nvidia website (this driver worked for my desktop 8800 cards, while the Nvidia driver from the Ubuntu distro did not).

So... it seems I have two options. One would be to modify the X config files so that the generic VGA driver is used instead of the Nvidia driver. But I don't know how to do that and I don't know how to restart the installation script with X once it is done.

The other option would be to use the alternate desktop installation CD, to install without X, then install the driver from the Nvidia website, and then configure the system for a graphical boot, gnome, etc as it would have been if the graphical installation had completed. But again I'm afraid I wouldn't know how to go about this.

I'd really appreciate advice as to which of the two approaches to follow and some specifics as to how to proceed with the recommended approach.

Thanks very much.

Matthew Fleming

---

### Post by corvy on 2007-08-10
I am going to test the daily gutsy cd now on the very same machine, fom here : [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/), might be using the new driver.

Will post more when I know more :)

---

