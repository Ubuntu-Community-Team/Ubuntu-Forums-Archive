---
title: "Software Sources will not open"
date: 2008-08-16
forum: General Help
---

### Post by drgnrave on 2008-08-16
For some while now, I can not open Software sources under System > Administration > Software sources (in Gnome, Ubuntu Hardy). I know you can manually add to /etc/apt/sources.list, but I still want to fix this error.

I also ran: 

gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

and got as output

/home/drgnrave/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'

How would I go about fixing this? Thanks.

--drgnrave

---

### Post by dje on 2008-08-16
try running this from terminal and posting output:
```
software-properties-gtk -m
```
and also:
```
cat $HOME/.gtkrc-2.0
```

dje

---

### Post by drgnrave on 2008-08-16
Ok I ran it and got back:

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 35, in <module>
    gtk.gdk.threads_init()
SystemError: error return without exception set

---

### Post by drgnrave on 2008-08-16
Forgot... The second one gave:

gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0

---

### Post by dje on 2008-08-16
umm try:
```
mv $HOME/.gtkrc-2.0 $HOME/.gtkrc-2.0.bak
```
the try starting software sources again

dje

---

### Post by drgnrave on 2008-08-16
I tried that, but still no go. Logged out and Logged in also. The

--desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

still gives the same error.

---

### Post by dje on 2008-08-16
ummm try:
```
sudo apt-get install --reinstall software-properties-gtk
```

dje

---

### Post by drgnrave on 2008-08-17
Still no luck. The password dialog does show up, but I do not get directed to Software Sources.

---

### Post by drgnrave on 2008-08-22
any one out there?

---

### Post by drgnrave on 2008-08-30
bump

---

