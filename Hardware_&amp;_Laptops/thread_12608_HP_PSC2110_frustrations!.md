---
title: "HP PSC2110 frustrations!"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by RJQuackQuack on 2005-01-25
In article <ct6caf$5q9$1@poblano.linuxprinting.org>, [email]RJQuackQuack@gmail.com[/email]
(Alex Nikolaidis) writes:
> 
> I looked at some error logs and found that the ppd file i had in
/etc/cups/ppd
> was wrong, missing some lines.	So I went through gnome's "add Printer" wizard
> again.	After this, my printer was fine.
> 
> I unplugged the printer from the computer's usb port to see what would
happen.
> and as soon as it was reconnected nothing would print again.  The ppd file
> checks out using the cupstestppd command, yet when I attempt to print
anything
> nothing happens at all.

I was looking through some things when i wound up at the hp page for linux
support.  I found and followed this(using the recommended hplip:
[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php).

Everything seemed to work, but I could not access the "add printer" button on
[http://localhost:printers](http://localhost:printers) (security reasons on ubuntu i assume).  Instead, I
followed the Computer>System Tools>Printing menus and set up the printer there,
trying to keep as many settings as close to those listed as possible.

So still nothing prints and I cannot access the hp device manager.  That
doesn't exist under Menu(Applications)>Accessories.

After installing all the hp software only to have nothing change, I am very
frustrated.  Any ideas or help would be most appreciated.

EDIT - if it's any help, when I try to use XSane(part of the hplip software) to scan an image with the same printer, I get the error "Device is busy."

---

### Post by hardcandy on 2005-01-26
How about adding root, 'sudo passwd root" , and then using the root and its password to log into cups?

---

### Post by RJQuackQuack on 2005-01-26
That did not work...anyone else?

---

### Post by hardcandy on 2005-01-26
I saw where you had "localhost:printers" for cups access. It is "http://localhost:631" and then manage printers.

---

### Post by gpierce on 2005-02-20
[QUOTE=RJQuackQuack]That did not work...anyone else?[/QUOTE]
 You can try installing the cupsys driver from deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) unstable main (just add this to your /etc/apt/sources.list file) and you will probably be able to log onto [http://localhost:631](http://localhost:631) as admin.  You, of course, will have to have a root account.

-Greg

---

