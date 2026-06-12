---
title: "Laptop Sound"
date: 2009-05-14
forum: Hardware
---

### Post by daichimajumdar on 2009-05-14
I'm a newbie on the Linux platform and I have recently installed ubuntu 8.0 on my laptop. My problem is that the laptop speakers aren't working in Linux. They aren't even detected by the OS. But it is running smoothly in Windows XP. Can anyone suggest a solution??

---

### Post by FirstTimeMan on 2009-05-14
> **daichimajumdar said:**
> I'm a newbie on the Linux platform and I have recently installed ubuntu 8.0 on my laptop. My problem is that the laptop speakers aren't working in Linux. They aren't even detected by the OS. But it is running smoothly in Windows XP. Can anyone suggest a solution??


I may not be able to help, but I would advise you to post a little more info so others can better assist you.

details like-

Brand of Laptop
Type of sound card etc.

If you can find out these things.



-FTM

---

### Post by steve01832 on 2009-05-15
Right click on the speaker icon. Make sure the speakers are selected there. You will also need to select preferences. Double click the selections and make sure the boxes are ticked. So you'll need to do 2 things. Open Volume Control, uncheck mute if ticked, make sure laptop speakers are online and volume is not muted, then go to preferences.

Steve

---

### Post by Kevbert on 2009-05-15
If steve01832's post doesn't work please enter the following command in Applications-Accessories-Terminal and post back the reply:
```
lshw -C multimedia
```
(list hardware - multimedia sound). The command is case sensitive.

---

