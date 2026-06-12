---
title: "Stuck on login screen  LENOVO ideapad Y700 with Geforce GTX960 on ubuntu"
date: 2016-04-14
forum: Hardware
---

### Post by Victor_Lubchuk on 2016-04-14
Hey guys i got a big problem, i have try every thing that i found in internet and nothing helps me. 

[COLOR=#000000]I just by lenovo ideapad Y700 with geforce gtx 960, and my OP is UBUNTU 14.04.4[/COLOR]


After that i follow steps of this post of Jempa333   [http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316),
[COLOR=#000000] i'm stuck on login screen and can't login to desktop. always when i'm enter user and password in login screen, i'm returning to the same login screen and can't enter to the desktop.[/COLOR]
[COLOR=#000000] what can be a reason of this? Any body please help!
 thank's for advice[/COLOR]

---

### Post by mörgæs on 2016-04-15
How does it work in a fresh install of 16.04?

---

### Post by Victor_Lubchuk on 2016-04-15
> **mörgæs said:**
> How does it work in a fresh install of 16.04?


ubuntu 16.04??

whre can i get one?

---

### Post by bozhidar2 on 2016-06-01
> **Victor_Lubchuk said:**
> Hey guys i got a big problem, i have try every thing that i found in internet and nothing helps me. 

[COLOR=#000000]I just by lenovo ideapad Y700 with geforce gtx 960, and my OP is UBUNTU 14.04.4[/COLOR]


After that i follow steps of this post of Jempa333   [http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316),
[COLOR=#000000] i'm stuck on login screen and can't login to desktop. always when i'm enter user and password in login screen, i'm returning to the same login screen and can't enter to the desktop.[/COLOR]
[COLOR=#000000] what can be a reason of this? Any body please help!
 thank's for advice[/COLOR]

I have the same lap top and the same problem, have you managed to fix this?

---

### Post by aljosa2 on 2016-06-02
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]recently I've made a new clean installation of Ubuntu 16.04  [/COLOR]*(Lenovo Y700-17ISK*[COLOR=#000000]) and all went wrong while installing Nvidia driver via additional drivers (same problem on Asus notebook too).[/COLOR]
[COLOR=#000000]Here's how I solved this annoying problem:[/COLOR]

> [COLOR=#000000][I]sudo apt purge nvidia*
sudo apt autoremove
sudo reboot[/I][/COLOR]

> [COLOR=#000000][I]sudo apt update && sudo apt install -f
sudo apt upgrade
sudo apt dist-upgrade[/I][/COLOR]

[COLOR=#000000]BIOS settings:[/COLOR]
[COLOR=#000000]- switchable graphics[/COLOR]
[COLOR=#000000]- fast boot disabled[/COLOR]
[COLOR=#000000]- intel platform trust technology disabled[/COLOR]
[COLOR=#000000]- secure boot disabled[/COLOR]

> [COLOR=#000000]*sudo apt install nvidia-361 nvidia-settings nvidia-prime*[/COLOR]

[COLOR=#000000]By the way, something strange is happening on Lenovo website[/COLOR]
[http://support.lenovo.com/hr/en/prod...are&beta=false]("http://support.lenovo.com/hr/en/products/laptops-and-netbooks/ideapad-y-series-laptops/y700-17isk?tabName=Downloads&linkTrack=Mast:SubNav:Support:grin:rivers%20and%20Software|Drivers%20and%20Software&beta=false")
[COLOR=#000000]already 10-15 days it is impossible to find any BIOS (update) file.[/COLOR]

---

