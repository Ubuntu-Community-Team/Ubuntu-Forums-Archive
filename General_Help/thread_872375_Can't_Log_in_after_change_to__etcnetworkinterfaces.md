---
title: "Can't Log in after change to  /etc/network/interfaces"
date: 2008-07-27
forum: General Help
---

### Post by Lucid Dreams on 2008-07-27
Hello:

I'm new to Linux/ubuntu and have only used it for a couple of days.  It's been fun so far.

I wanted to change the MAC address of my broadcom wireless networking card. (bcm43xx). First, I used the macchanger utility.  After failing to change the MAC of my wlan0 in any way failed, I discovered the macchanger-gtk (same thing but with an interface).  This simplies everything but I still couldn't get it to work.  I tried some fconfig commands but they didn't work either.

At any rate, finally I tried this as suggested on another forum:  >  edit your /etc/network/interface file


Code:
sudo gedit /etc/network/interfaces  add this line right above the line containing "auto eth0" (again, assuming your using eth0)

Code:
hwaddress ether XX:XX:XX:XX:XX:XX  Now it should connect using the new MAC address automatically at startup.


As a result, ubuntu now permenately freezes everytime immediately after I enter my password to try and log in.  I have Windows XP on another partition but it cannot write to the Linux partition.  I loaded another instance of ubuntu from the Live CD, and navigated to the file to undo what I did.  I was denied due to not having permission to change my file.

What is the best way to undo this small but paralyzing change?

Thank you in advance.

---

### Post by Mister.Vash on 2008-07-27
Have you logged in at the terminal prompt?  When the login page appears, instead of entering your username and password press Crtl + Alt + F1 and try a logon from there.

---

### Post by Aearenda on 2008-07-27
I would try this:
1. Reboot the machine, and press <ESC> to enter the boot menu when it says so.
2. Use the up and down cursor keys to choose the second Ubuntu entry, which should say 'recovery mode' alongside; then press <Enter>
3. Lots of text will fly past, then it will stop asking what you want to do. Choose the root command line option.
4. At the command prompt type this:```
nano /etc/network/interfaces
```
5. You should now be able to move down to the offending linde and delete it.
6. Press <CTRL>and X and then y and then <Enter> to save the file.
7. Now press <CTRL> and d to exit from the command prompt.
8. Choose the option to continue starting Ubuntu.

That should be it! However, you may find that the /etc/network/interfaces file is corrupt in some way - make sure the following entry is present:
```
# The loopback network interface
auto lo
iface lo inet loopback

```


EDIT: If you can log in to a terminal as Mister.Vash suggests, you can use ```
sudo nano /etc/network/interfaces
``` to fix the file, and then reboot.

---

### Post by Lucid Dreams on 2008-07-28
Aearenda, that did the trick, thanks!

---

### Post by Aearenda on 2008-07-28
Glad to be able to help. I suspect the reason was that the interface settings became unusable, and for X Windows at least the loopback network setting has to work. Also if DNS does not work there can be delays of 30 seconds while it times out.

I suspect your edit > sudo gedit /etc/network/interfaces add this line right above the line containing "auto eth0"assumed that the 'auto eth0' came AFTER the 'iface eth0 ...' line, whereas in fact the auto line can come first - so you probably set the MAC address on the 'lo' interface, in practice! Now you know how to rescue things, you could try adding the MAC address after the 'iface eth0 ...' line.

---

