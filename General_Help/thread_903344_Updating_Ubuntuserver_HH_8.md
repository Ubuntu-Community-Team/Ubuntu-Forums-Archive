---
title: "Updating Ubuntuserver HH 8"
date: 2008-08-28
forum: General Help
---

### Post by gpb on 2008-08-28
I've managed to connect my Ubuntu Server box with DSL to the internet. What command (CLI) do i give in order to update the server??? thanx

---

### Post by silverglade00 on 2008-08-28
sudo apt-get update && sudo apt-get upgrade

The first part updates the package listings. The second part upgrades any packages that have a newer version available.

---

