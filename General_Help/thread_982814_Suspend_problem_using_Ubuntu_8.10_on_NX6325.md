---
title: "Suspend problem using Ubuntu 8.10 on NX6325"
date: 2008-11-15
forum: General Help
---

### Post by Prankie1 on 2008-11-15
Hi
I switched to Ubuntu few days ago and so far it have been working pretty good. However there is a minor glitch that is quite annoying. 

1. After I return from suspend mode my computer backlight is only on half so everything is quite dark. I have been trying to find a permanent fix for that with no luck. Uncomment the Double console switch in /etc/default/acpi-support didn't help.

2. Another way of doing it was switching to virtual console and back using hot keys CTRL ALT F2 and then F7 back. It works sometimes but mostly I can't even access virtual console, it's just completely blank. When I switch back to x it's still half dimmed backlight. 

3. If all else fail I use the ctrl alt backspace which force my to restart all program I'm using. But now that isn't working either. 

I'm running the ATI/AMD proprietary FGLRX graphic driver if it has anything to do with it. I'm quite new to ubuntu so I was hoping someone could help my here.

---

### Post by iponeverything on 2008-11-15
right click on the panel and go to "Add Applet" add the Brightness Applet and see if that allows you to turn the brightness back up.

---

### Post by Prankie1 on 2008-11-15
I have no control of brightness. It's always on max.

---

### Post by Prankie1 on 2008-11-15
After I deactivated ATI/AMD driver both brightness control and suspend problem were solved. :)

Is this problem only on ATI catalyst 8.11 or is it on earlier version as well?

---

