---
title: "CUPS service not starting"
date: 2010-08-13
forum: Hardware
---

### Post by Anoobis on 2010-08-13
Ubuntu 10.04, the CUPS service is not starting on boot.
Currently I'm using
```
sudo /etc/init.d/cups restart
```
to get the printing going.
What can I do to avoid typing this into the terminal each time I want to print?

---

### Post by eqqfooyoung on 2010-08-13
Hello,

I had a similar problem a while back. Take a look at my post and see if the solution works for you.

[http://ubuntuforums.org/showthread.php?t=1416651](http://ubuntuforums.org/showthread.php?t=1416651)

---

### Post by Morbius1 on 2010-08-13
Try this:
[COLOR=Blue]EDIT: IF the post above is not the issue.[/COLOR]

> **Morbius1 said:**
> If you can't resolve this by removing and adding  the printer and if the problem is that you have to restart cups at  every boot then I would suggest the following:

Create a script:[FONT=sans-serif]
[/FONT]```
gksu gedit /etc/network/if-up.d/cups
```With this content:
```
#!/bin/sh
service  cups restart

```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups
```Reboot

---

### Post by Anoobis on 2010-08-14
> **Morbius1 said:**
> Try this:
[COLOR=Blue]EDIT: IF the post above is not the issue.[/COLOR]

This worked perfectly. thanks very much

(first solution didn't work - i already had that text in that file)

---

