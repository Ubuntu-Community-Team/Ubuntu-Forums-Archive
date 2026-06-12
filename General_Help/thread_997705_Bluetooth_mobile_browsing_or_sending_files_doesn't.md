---
title: "Bluetooth mobile browsing or sending files doesn't work"
date: 2008-11-30
forum: General Help
---

### Post by Kolinop on 2008-11-30
Hello!

I'm having problems with Bluetooth browsing of my Mobile Nokia XM5610.

I get the following error when trying with Blueman:

[I]Could not display "obex://[00:00:00:00:00:00]/".

Error: Method "CreateBluetoothSession" with signature "sss" on interface "org.openobex.Manager" doesn't exist

Please select another viewer and try again.[/I]

Can anyone help me with this?

I suspect it is a bug but i want to be sure before I fill in a report.

---

### Post by fragos on 2008-11-30
It looks like the phone isn't paired with the desktop or needs to be specificaly selected. Alao make sure gnome-bluetooth is installed. Are you running 8.04? I haven't yet seen a release of bluemon for 8.10.

---

### Post by Kolinop on 2008-12-01
Hello!

I'm running 8.10 Intrepid, 2.6.27-9-generic.

I think the phone is paired at least in Blueman because I can connect to it by bluetooth when i'm using mobile broadband.

I had the same problem with Bluetooth-applet. Ocasionally it let me look to my files on the phone but i couldn't copy or paste anything. I think the error was "Operation not supported by backend".

---

### Post by fragos on 2008-12-01
In my personal experience I've found differences in how individual bluetooth devices are supported even past that relating to supported protocols. For example my Palm E2 could recieve but not send via bluetooth where my Nokia N810 is completely supported. I've noticed that in 8.10 the right click send to doesn't work but send to with the applet icon does. Not sure why so I adapted to what works.

---

