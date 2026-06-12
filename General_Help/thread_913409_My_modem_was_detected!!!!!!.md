---
title: "My modem was detected!!!!!!"
date: 2008-09-07
forum: General Help
---

### Post by junojpeg on 2008-09-07
I typed in sudo wvdial and this is the message I got


junojpeg@junojpeg-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
-
-> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.


I think it is great that my modem is now workable, but how do I add that "valid" phone #, login name, and password that the message is asking for?

---

### Post by Shazaam on 2008-09-07
Modify /etc/wvdial.conf....
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)

From here...
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by junojpeg on 2008-09-07
Ok, what do I type in once I get to this screen?

---

### Post by Shazaam on 2008-09-08
Where you see things in brackets (<  >) put your info there. Delete the brackets too. So instead of this...
```
<5551212>
```
it would just be...
```
5551212
```

---

### Post by junojpeg on 2008-09-11
I tried typing in my information(and deleted the <>). Do I have to type ctrl-o then enter to save it, because that is what I am doing and it is still telling me I have no ISP info configured.

---

### Post by Shazaam on 2008-09-11
One thanks is plenty :)
```
Saving and Exiting
^O 	save contents without exiting (you will be prompted for a file to save to)
^X 	exit nano (you will be prompted to save your file if you haven't)
^T 	when saving a file, opens a browser that allows you to select a file name from a list of files and directories 
```
From here...
[http://mintaka.sdsu.edu/reu/nano.html](http://mintaka.sdsu.edu/reu/nano.html)

---

### Post by Shazaam on 2008-09-11
I went through some of your earlier posts and I have a question- Is this an internal or an external modem you are trying to set up? And do you have gnome-ppp installed?

---

### Post by junojpeg on 2008-09-11
It is an internal modem, and I tried typing in

sudo apt-get install gnome-ppp

but it did nothing, I will post a screen shot of what happends when I type it in.

---

### Post by junojpeg on 2008-09-11
Here is the screenshot

---

### Post by Goombie on 2008-09-11
Looks like you don't have your "Universe" repository enabled, which is where gnome-ppp is located. To enable the Universe repository:
-Go to System > Administration > Software Sources
-Under the tab "Ubuntu Software" check the box labeled "Community Maintained open-source Software (universe)"
-Click Close. You will be prompted to reload your information about available software. Click Reload.
-Now you should be able to install gnome-ppp. Good luck. :)

---

### Post by junojpeg on 2008-09-11
Actually I just checks my settings and (universal) is enabled, I even opened up the terminal and typed gnome-ppp install again to make sure, and it still didn't install. It gave me the same message  from the screenshot.

---

### Post by Goombie on 2008-09-12
Did you make sure to reload your package information? You can also open up Synaptic and click the "reload" button to do that. If that doesn't work, I don't know what to do, since gnome-ppp is in the universe repository.

---

### Post by junojpeg on 2008-09-22
Can I get gnome PPP from somewhere else? Download it onto my pin drive and upload it myself?

---

### Post by Goombie on 2008-09-23
I'd try at [http://packages.ubuntu.com/](http://packages.ubuntu.com/). You can download the .deb file from there, then install it yourself.

---

