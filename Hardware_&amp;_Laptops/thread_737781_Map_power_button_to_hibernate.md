---
title: "Map power button to hibernate?"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by randomperson83 on 2008-03-27
I'm looking for a non-hacky way of making the computer hibernate after hitting the power button. I don't want to use GNOME power manager or any other GUI way of doing it, since I'm not always running those on the computer at any given time. I just want it to work, no matter what. 

Currently, I've modified /etc/acpi/powerbtn.sh and added the following lines to it:

```

/etc/acpi/hibernate.sh
exit

```

and this does exactly what I wanted. However... it really feels like a hack. Is there a better way of doing this? Oh, I'm using Hardy also, btw.

---

