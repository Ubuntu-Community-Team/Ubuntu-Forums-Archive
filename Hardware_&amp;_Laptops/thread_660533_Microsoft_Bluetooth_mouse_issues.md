---
title: "Microsoft Bluetooth mouse issues"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by tstack77 on 2008-01-06
I have the notebook optical mouse 5000 and when i try to connect I get:

"obex://[00:15:5a:69:91:14]"
is not a valid location.

So my next try/result was:

tstack@desktop:~$ sudo hidd --connect 00:12:5A:69:91:14
[sudo] password for tstack:
**Can't create HID interrupt channel: Connection refused**

What is going on here?

---

### Post by linuxwizard on 2008-01-06
At the bottom of this page  Troubleshooting

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by tstack77 on 2008-01-07
Thanks, but it didn't work for me:

[B]sudo apt-get install gnome-vfs-obexftp

Although this gives "Couldn't display "obex://[xx:xx:xx:xx:xx:xx]"." for some.[/B]

I am one of the "some" this happens to and it still won't work. I'm thinking the obexftp only works for phones.

I am stumped...could this be a bug?

---

### Post by tstack77 on 2008-01-07
bump for luv :-k

---

### Post by Ares139 on 2008-02-09
I did a "sudo hidd --search" while my Microsoft mouse was set to "discoverable" and it worked right off the bat.  I'm just on a LiveCD at the moment so I haven't tested whether it is persistent or not, but yeah.

Found that here:
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

---

### Post by drusifa on 2008-02-28
this didn't quite work at first, but thanks Ares for pointing me in the right direction.

did the following to get my mouse going after all else failed. 

I followed what ug suggested but with a couple of minor changes. new to ubuntu, so forgive if i'm stating the obvious with my changes, but thought it would be good for a novice like myself.

the following command to pop up GEdit

sudo gedit /etc/bluetooth/hcid.conf

You may be asked for your password, this is because we used sudo.

At the end of the file, add the following (replacing KEYBOARD_ADDR and MOUSE_ADDR for the keyboard and mouse MAC addresses as found earlier)  *- if you dont have a keyboard like me, just put this in...*

device MOUSE_ADDR {
name \u201cMicrosoft Mouse\u201d;
}

Now you need to restart the bluetooth subsystem so that it refreshes it\u2019s configuration file.

sudo /etc/init.d/*bluetooth* restart

---

### Post by CanadianNorth on 2008-04-09
thanks!!

that did the trick for me

---

### Post by Spokecrasher on 2008-05-05
[QUOTE=Ares139;4303136]I did a "sudo hidd --search" while my Microsoft mouse was set to "discoverable" and it worked right off the bat.  

WOW, that worked for me right away.........
Thanks for the great tip ;-)

---

### Post by greywolf73 on 2008-06-05
If you can get it using hidd but not through the bluetooth manager and you are using Gutsy. Then you need to execute the following command:

sudo apt-get install gnome-bluetooth


Apparently there are three missing components. They are:

 gnome-bluetooth 
 libbtctl4 
 libgnomebt0

After, this is installed you will be able to add and trust your mouse.

Hopes that help!

---

