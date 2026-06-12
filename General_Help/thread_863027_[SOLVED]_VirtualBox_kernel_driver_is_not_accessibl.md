---
title: "[SOLVED] VirtualBox kernel driver is not accessible to the current user"
date: 2008-07-18
forum: General Help
---

### Post by Rickzkm on 2008-07-18
Hi guys,

just to let you know i am a total newbie to linux and i have tried to install Vbox from repository but got some error, I looked it up on interent and followed instructions, but now i have a different error:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Can anyone help please?
Thanks.

---

### Post by Elfy on 2008-07-18
Open users and groups in sys admin menu

Unlock if you are using hardy - then manage groups, find vboxusers - properties and enable your user and reboot

---

### Post by Rickzkm on 2008-07-18
Wow, that worked and is easy, thank you so much for your help I am now installing XP.

---

### Post by Elfy on 2008-07-18
You're welocome  - a lot of the time the system will tell you what you need to do - it's the understanding what it's saying which can take the time :)

Can you mark thread solved please.

---

