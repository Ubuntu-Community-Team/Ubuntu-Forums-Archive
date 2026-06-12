---
title: "Symbolic Link"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by JNowka on 2006-01-29
I was wondering if there was a way to create a symbolic link automatically for my modem at startup. It is annoying to have to make it everytime I boot up linux.
 
 Currently I have to type
 
 ls -s /dev/536ep0 /dev/modem
 
 If anyone can help it will be very appreciated.

---

### Post by el3ktro on 2006-01-29
You may have a look at

/etc/udev/rules.d/udev.rules

there you can define which devics UDEV should create during boot.

Tom

---

### Post by JNowka on 2006-01-29
First
I have no idea how to edit or interpret udev

Second here is a little more info:
I had to copy the Intel536ep.ko file to this directory
/lib/modules/2.6.12-9-386/kernel/drivers/char

And had to add Intel536ep to /ect/modules

---

### Post by el3ktro on 2006-01-29
Try to add a line like this:

KERNEL=="536ep0",          NAME="modem"

Alternatively, and probably easier would be to add the ln -s command to your startup scripts or to the Gnome/KDE autostart. if you use Gnome, go to System->Settings->Sessions and then choose "Autostart programs", there you can add the ln -s command

Tom

---

### Post by JNowka on 2006-01-29
Problem is when I use the ls command i have to use sudo with it.  Otherwise I get a permission denied

If i do it as an autostart will it not need the sudo command?

---

### Post by el3ktro on 2006-01-29
Um, that's true of course. I didn't think about this since I've disabled sudo passwords. You could disable sudo passwords for this one command, but it's still not really secure. Did you try to modify the UDEV rules?

Tom

---

### Post by JNowka on 2006-01-29
Yes the udev.rules thing works perfectly.  Thank you alot. \\:D/ 

BTW how do you disable individual commands for sudo?

---

### Post by el3ktro on 2006-01-29
You have to edit the file /etc/sudoers with the visudo command (You MUST not edit this file using an editor, you must use visudo!) So open a terminal and run

sudo visudo

You'll find a line that says something about user privileges for root. After this line, add something like this:

jack ALL=(ALL) NOPASSWD: ln

This would allow the user jack (and only him) to run the command 'ln' (and only this one) without a password, so you can type 'sudo ln -s ...' and are not prompted for a password.

Tom

---

### Post by Matchless on 2006-02-11
[QUOTE=JNowka]I was wondering if there was a way to create a symbolic link automatically for my modem at startup. It is annoying to have to make it everytime I boot up linux.
 
 Currently I have to type
 
 ls -s /dev/536ep0 /dev/modem
 
 If anyone can help it will be very appreciated.[/QUOTE]

Hi,
   I have just apdated the [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) include the symlink steps after doing my own Intel536 install in Breezy. This modem is much more stable in Breezy than the Smartlink one.
Hope this helps.

---

