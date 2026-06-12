---
title: "Memory usage problem"
date: 2008-07-31
forum: General Help
---

### Post by ittayd on 2008-07-31
Hi,

I have a laptop with 2GB memory, which is almost full. The reason is that apps take too much memory (rss):
Thunderbird - 150M
Firefox - 215M
Eclipse - 410M
X - 460M
And the rest is taken by other applications.

Does someone here know why these apps take so much memory and how it can be investigated & reduced? Esp. X?

Thank you,
Ittay

---

### Post by sdennie on 2008-07-31
The output of "free -m" might be useful here.  There are various ways of reporting how much memory is used and some of them can be very misleading.  If you aren't seeing any swap usage, you probably don't have anything to worry about.

---

### Post by chrisccoulson on 2008-07-31
You might also find this useful when trying to understand Linux memory management: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

---

### Post by mali2297 on 2008-07-31
Do you use desktop effects?
What is your graphics card? 
Do you know if you have the correct driver for it?

---

### Post by ittayd on 2008-08-02
Thank you all,

Free -m shows 400MB free. All I have are 5 applications running: Firefox, Thunderbird, Eclipse, OpenOffice and Gnome Terminal. With 2GB I would have expected a lot more free memory. The swap takes 1.1GB, which I feel, because all applications are sluggish. 

Listing applications sorted by RSS shows this:
  PID   RSS    SZ CMD
....
....
4170 18024 79784 gnome-terminal
30107 49464 147584 /usr/lib/openoffice/program/soffice.bin -calc file:///tmp/Build-NG.xls -splash-pipe=5
 5333 115624 182048 /usr/lib/firefox-3.0/firefox
 6752 373816 489260 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7
15117 400744 925592 /usr/bin/eclipse -vmargs -Xmx512m -client -Djava.net.preferIPv4Stack=true -XX:PermSize=64M -XX:MaxPermSize=128M
20678 415648 548648 /usr/lib/thunderbird/thunderbird-bin

It also looks to me that applications just take more memory in Linux than in Windows. I have a Windows XP computer with 1GB memory only, running the same set of applications. Why?

Thank you,
Ittay

---

