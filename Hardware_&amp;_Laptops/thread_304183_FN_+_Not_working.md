---
title: "FN + Not working"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by mfmbcpman on 2006-11-21
Whenever I press FN + arrow keys it doesn't change my brightness and then ubuntu crashes. How do I get these FN + commands to work?

---

### Post by dentaku65 on 2006-11-21
> **mfmbcpman said:**
> Whenever I press FN + arrow keys it doesn't change my brightness and then ubuntu crashes. How do I get these FN + commands to work?

Do you have hotkey installed?

```
sudo apt-get install hotkeys
```

or try (but I don't have experienced)
```
sudo apt-get install hotkey-setup fnfx-client
```

---

### Post by mfmbcpman on 2006-11-22
michael@Michaellaptop:~$ sudo apt-get install hotkeys
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
michael@Michaellaptop:~$

I get that when I try this. I'm brand new so I don't know what I'm doing.

---

### Post by mfmbcpman on 2006-11-23
I do have both of those installed and it is still not working.

---

### Post by chele on 2006-11-26
> **mfmbcpman said:**
> I do have both of those installed and it is still not working.Please provide the details lindicated here: [https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch)

What should each of the keys do?

---

