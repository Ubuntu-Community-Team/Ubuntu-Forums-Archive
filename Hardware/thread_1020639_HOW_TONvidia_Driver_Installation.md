---
title: "HOW TO:Nvidia Driver Installation"
date: 2008-12-24
forum: Hardware
---

### Post by enarsee on 2008-12-24
THis is for first time ubuntu users like me. Finally i could use the nvidia card.

1)Firstly download the nvidia driver from [here]("http://www.nvidia.com/object/unix.html")

2)rename it and give it an easy name to remember (for eg nvidia.run)

3)Now place it on the desktop for easy access

4)Now restart ubuntu and start the recovery mode (can be accessed by pressing Esc before booting)
5)now in recovery mode use the root shell option
6)if it asks for root password type in your own password
if it still rejects then you'll hve to resume normal boot and type "sudo passwd root" in terminal and change the password
7) repeat steps 4 and 5 if u hve changed the root password
8) once logged in as root
type "sudo sh /home/(your username)/Desktop/(name of file for eg. nvidia.run)
9) Follow the instructions of the isntaller thereafter donot switch to telinit 3 and continue the setup

Well other ubuntu experts please correct me if i am wrong anywhere.

---

