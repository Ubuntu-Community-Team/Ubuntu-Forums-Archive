---
title: "access files on external ubuntu installation"
date: 2010-04-25
forum: Hardware
---

### Post by jan.naef on 2010-04-25
i had ubuntu installed on an IBM ThinkPad t41. this ThinkPad broke down, so i took out the hd and inserted it into an USB external hd case, in order to access the files on it. i run ubuntu 9.10 from a live cd and can viev the files of my old ubuntu installation the external hd. i can see my home partition, the partition with the linux files and the swap partition.

however, from the live-cd, i dont have the necessary permissions to view/backup all files of my old ubuntu installation... is there a way to do this? maybe i can mount my old home directory in the live-cd ubuntu or something. i know the root password ot he old installation.

---

### Post by davidpbrown on 2010-04-25
Have you tried logging in as superuser in the Live CD terminal? It's been a while since I tried but I think it's possible, though it allows that without password needed.

So [sudo -i] will give you persistent root that you can see through the permissions on the old disk. Then copy with -p to preserve the user permissions on files, if you want them retained.

---

### Post by jan.naef on 2010-05-02
cool! i run the ubuntu live cd, open a terminal and type.

sudo -i

i have all permissions on my old harddisk without even being prompted my old password... which is a bit weird... but it works.

solved.

---

