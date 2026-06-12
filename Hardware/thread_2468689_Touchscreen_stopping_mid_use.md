---
title: "Touchscreen stopping mid use"
date: 2021-11-08
forum: Hardware
---

### Post by wisg00 on 2021-11-08
Hello everyone,

We have just started using Ubuntu 20.04 LTS in our live environment. We was using windows 10 before with no issues.

Description of setup:
Computers in server room(USB to RS232) TO> Adderlink Silver CAT 5 extender (RS232 & VGA) TO> Touchscreen (3M microtouch)


Current issue:
I manually have to "xinput map-to-output" our touchscreens because USB to serial adapter doesn't see touchscreen automatically due to Adder link extender in-between them. But once mapped mid use / during operation it will stop working and we need to manually map the touchscreen again.

Attempted fix's:
adding input attach to rc.local folder
disabling USB power suspend/save
adding xinput map to start-up

The occurrence of the issue is more frequent in some of the computers then others but the hardware setup is all the same and we just use clean 20.04 LTS images I have really hit a brick wall with it and I don't want to really go back to windows. any help would be much apricated.

Thanks in advance

---

