---
title: "How to read CPU% in System Monitor"
date: 2008-08-27
forum: General Help
---

### Post by mooncaptain on 2008-08-27
I have been watching my system monitor Processes page and have noticed that some processes get a non-zero CPU% value and a Status of sleeping. Is this really happening and if so what does it mean or is this a GUI update/misrepresentation problem.

---

### Post by Tom--d on 2008-08-27
Do not use System Monitor as there is a bug with it (making the cpu work more than it should do).

Install Htop. Open up terminal (applications > accessiores > terminal) and type this in
```
sudo apt-get install htop
```
then once its finshed, in terminal, type htop and enter. now you will see the it :D

---

