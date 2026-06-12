---
title: "High Ram Usage on startup!"
date: 2008-07-16
forum: General Help
---

### Post by Javawag on 2008-07-16
Hi,

Since the day before yesterday, my Ubuntu has been starting up strangely. Once I get to the desktop after logging in, there's a lot of hard drive activity, and open checking gnome-system-monitor, I notice that nautilus is using over 1GB of swap, 400MB of RAM (out of my 512MB) and >70% CPU. This happens for about a minute or so, at which point nautilus drops to using 3.4MB of RAM and 80MB of swap (normal). Any ideas what's causing this?!

- Javawag

---

### Post by danwood76 on 2008-07-16
What processes are using all the RAM and Swap?
You can find out using 'top' in the terminal.

---

### Post by Javawag on 2008-07-16
They all were using the normal amount of RAM, except "nautilus". I didn't even have nautilus open browsing folders or anything, but I assume it runs to display the desktop too (Sorry, I'm a windows user so I'm still not 100% on the workings of Ubuntu yet! I'm just assuming nautilus does the same as explorer by showing the desktop)

- Javawag

---

### Post by danwood76 on 2008-07-16
Do you have any network drives you mount on startup?
Or do you have any drives that mount on startup?

It must be doing something odd, is your system up to date?

---

### Post by Javawag on 2008-07-16
I don't have any network drives mounted, and the only volumes mounted are my ext3 root filesystem and my ntfs-3g windows partition, but they've been there since I installed Ubuntu... the only thing I can think of come to mention it is I did install samba to try and browse Windows PCs on my network workgroup... with little success... I'll try uninstalling that and restarting and tell you what occurs!

- Javawag

---

### Post by Javawag on 2008-07-16
OK... uninstalled samba, and same problem!! I've installed an extra 512MB of RAM today so i now have 1GB, but it still fills it on startup.... help!!

- Javawag

---

### Post by danwood76 on 2008-07-17
On startup, after its calmed down, can you post the output of the following command in the terminal:
```

dmesg

```
It may shed some light as to whats going on.

---

