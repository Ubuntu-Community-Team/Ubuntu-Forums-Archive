---
title: "Exfat on SDXC cards"
date: 2012-11-10
forum: Hardware
---

### Post by AllenGG on 2012-11-10
Want to use the exfat system on a new SDXC  memory card,
This works, came from here: 
[http://superuser.com/questions/436368/how-to-open-exfat-ssd-in-ubuntu-12-04](http://superuser.com/questions/436368/how-to-open-exfat-ssd-in-ubuntu-12-04)

     
   
                           exFAT is a proprietary file system  developed by Microsoft, and implementing it requires accepting a very  restrictive license from Microsoft. However, there is a FUSE [implementation]("http://code.google.com/p/exfat/") of exFAT for linux.
  Since you are on a Ubuntu system, you can install the above-mentioned exFAT implementation from their [PPA]("https://launchpad.net/%7Erelan/+archive/exfat").
  
[LIST=1]
[*]Add the PPA to your sources list by running
  sudo add-apt-repository ppa:relan/exfat   in your favourite terminal emulator
[*]Install the fuse-exfat and the exfat-utils packages:
  sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils
[/LIST]
  Now you should be able to use the SSD
 
                         (please refer to Superuser.com )
It worked instantly on my  Asus Zenbook  UX31 E  (Mexico version)
agg:cool:

---

### Post by dominictorreto87 on 2013-01-21
Gracias Amigo!
):P
It worked like a charm

Thread should be Called BIG HELP FOR SDXC CARDS on UBUNTU :)

---

### Post by union two levers on 2013-01-26
Brilliant, works perfectly and even i could follow the instructions, thanks so much.

---

### Post by AllenGG on 2013-04-24
**Note !!! ** when you upgrade in Ubuntu, you must repeat the above process.
Yes, re-install "fuse" using the instructions proved by "Superuser",
It does not happen auto-magically.
agg[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

