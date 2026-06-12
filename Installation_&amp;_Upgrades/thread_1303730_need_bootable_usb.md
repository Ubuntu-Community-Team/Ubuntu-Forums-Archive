---
title: "need bootable usb"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by cliffk on 2009-10-28
i have a dell inspiron 630m (pentium m 740) laptop. the cd drive currently doesn't work, but bios allows me to boot from usb.

as i understand it, i don't need an iso image, i need a flash image. [this]("https://help.ubuntu.com/community/GettingUbuntu") page tells me where. the [page for flash installations]("http://www.ubuntu.com/getubuntu/download-netbook") for this only lists netbook images, which apparently require an atom processor, which [as far as i can determine]("http://developer.intel.com") is not the same thing as a pentium m.

i found some mentions of [http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org) which upon some searching provides an [image for 8.04]("http://ubuntu-rescue-remix.org/node/44"), but the gz link gives back a russian language 404. this page also has information for making the usb bootable, but it is for linux users. my thought was to take the ubuntu rescue image and use the windows installation page from ubuntu to burn it. but i must be missing something....

i would have thought flash images are available on the ubuntu site, but i can't find them. i would have thought my need is fairly commonplace: making a bootable usb from a windows platform. i apologize if i'm missing the obvious. i don't like posting a question until i've tried everything, but that's where i am. i searched the forums for information on this but most threads deal with people that already have bootable usbs. i can't even get that far.

i do have another laptop btw with working cd drive, in the event an iso image is the only way to go. but i haven't been able to get (atheros) wireless to work and kind of given up on that for now. it seems that the usb boot problem would be the easier one to solve.

i had several embedded links above, but this tool seems to wipe them out, whether or not parse links into text is on or off. in case they are useful to the problem at hand, here's the plaintext links:[INDENT]http://developer.intel.com
https://help.ubuntu.com/community/GettingUbuntu
http://www.ubuntu.com/getubuntu/download-netbook
https://help.ubuntu.com/community/Installation/FromImgFiles
http://ubuntu-rescue-remix.org/node/44
http://ubuntu-rescue-remix.org/node/149
[/INDENT]

---

### Post by dabl on 2009-10-28
> **cliffk said:**
> 

as i understand it, i don't need an iso image



No, that's not correct -- you start with an ISO image, and then there are multiple ways to go about making the bootable USB device. For example, "unetbootin" is one such way, if you start with a Windows PC connected to the internet:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


But, even better IMHO, this is a lot of material, but if you will follow the guidance I can assure you I've used it multiple times, successfully:

[http://kubuntuforums.net/forums/index.php?topic=3089474.0](http://kubuntuforums.net/forums/index.php?topic=3089474.0)

:p

---

### Post by GGTutor on 2009-10-28
I found this site helpful


[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by cliffk on 2009-10-29
thanks. i've got linux running off a usb flash!

along the way...  [http://kubuntuforums.net/forums/inde...opic=3089474.0]("http://kubuntuforums.net/forums/index.php?topic=3089474.0") seems intended for a linux installation, and i only had a windows system available

i tried both 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
and [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)
on a multi-partition flash i had, but it wouldn't boot (i was reluctant to experiment with wiping it). but i bought a new flash and it worked fine.

i used [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)
because it 1) specified a provision for vista to re- "Run as administrator.." the bootable step and 2) had a [page on making the cdrom writable]("http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/") for data file transfer off old windows fs (i had corrupted os). the procedure didn't actually work, but i realized i could transfer as sudo su, onto /cdrom and see it anywhere, which suited my needs.

fyi.. unetbootin *might *have issue with the vista "feature" mentioned as 1 above, but i haven't tried it with the new flash. the advantage i see there is that unetbootin is more flexible about which build to use (pendrivelinux has a bat file called U904p, so i was reluctant to hybridize that procedure by introducing a different iso). i will probably try unetbootin to see if i can get the new ubuntu 910 for kicks.

again, many thanks

---

