---
title: "Help with task list and avant"
date: 2008-07-28
forum: General Help
---

### Post by env2156 on 2008-07-28
ok so im tryin gto setup avant i deleted the bar at the bottom so i can replace it when i go to transfer active applets there is nothing there to transfer, does anyone know what folder there in so i can set up the avant bar to have everything the orignal bar.

---

### Post by env2156 on 2008-07-28
i just need to know where the applets that are on the typical bottom task are so i can add them to avant i dont know where to find them

---

### Post by eightmillion on 2008-07-28
You need to install the awn applets. First you'll have to add the repository to your /etc/apt/sources.list  . Add this...
> 
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

Then run this command...
> sudo apt-get update && sudo apt-get install awn-extras-applets-trunk


---

