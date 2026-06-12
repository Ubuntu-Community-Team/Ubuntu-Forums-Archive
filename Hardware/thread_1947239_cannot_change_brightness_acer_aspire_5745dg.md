---
title: "cannot change brightness acer aspire 5745dg"
date: 2012-03-26
forum: Hardware
---

### Post by mariades on 2012-03-26
Hello guys hi to everyone!!!.I am new in this forum of ubuntu:)I have an  acer aspire 5745dg laptop and i have also a very serious problem!!My  brightness is always at maximun and i cannot change it with the fn keys  or from the power management.Thats my problem and i need your help  guys!!!!:(In my windows partition brightness works perfectly only in  ubuntu i have this serious and annoying problem!!!!Please reply to my  message i'd appreciate that!

---

### Post by x-shaney-x on 2012-03-26
This seems to be an issue with a lot of Acer laptops, including the 5742 that I have been using the past day or two.

For me, it was fixed like this:

```
gksudo gedit /etc/default/grub
```
Look for this line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Then add the following to it:  acpi_backlight=vendor

So after the edit, the line will look like this: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

Afterwards, in a terminal, run this: ```
sudo update-grub
```
Then reboot and see if it helps.

For me, this got brightness controls working, with the on-screen notifier AND auto dimming when running on battery.

---

### Post by mariades on 2012-03-27
Hi and thanks for the reply.I did what you told me to do but nothing happened.I've hearted something about acer-wmi do you know what is it?Can you tell me anything else to try?

---

