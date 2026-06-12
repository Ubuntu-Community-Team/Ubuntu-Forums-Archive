---
title: "[SOLVED] creating a dialog box in script"
date: 2008-08-08
forum: General Help
---

### Post by WallyWest on 2008-08-08
Hello,

I have been trying to convert a fairly simple script and in the process enhance it. Its main function is to automate some Telnet commands that I run all the time. I wanted to create a dialog box to display command options that would enter them into the telnet after being selected (mouse or otherwise). My curses lib is completely up to date as far as I can tell; yet I still cannot seem to make one appear. I used this example 

[http://linuxhelp.blogspot.com/2005/10/make-your-bash-scripts-user-friendly.html](http://linuxhelp.blogspot.com/2005/10/make-your-bash-scripts-user-friendly.html)

I copied it exactly into gedit but still it wouldn't work.

---

### Post by cszikszoy on 2008-08-08
Maybe you want to use Zenity instead.

There's a couple of good examples at this site:

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

Something more pertinent to you, look for the section that says: 
**How to create [B]zenity** entry **dialog**?[/B]

---

### Post by x1a4 on 2008-08-08
Hi,
Do you have the **dialog** package installed?

---

### Post by dexter.deepak on 2008-08-08
you can try either
1. dialog - for a terminal base dialog
2. Xdialog - gives you a new window , similar look and feel of dialog
3. GtkDialog - uses Gtk libraries, much better in looks, but slightly difficult.
4. zenity - much simple and better, uses gtk

---

### Post by WallyWest on 2008-08-11
> **x1a4 said:**
> Hi,
Do you have the **dialog** package installed?

Thanks.... I didn't even know that was a package i needed. I will try that.

---

### Post by WallyWest on 2008-08-11
....and it works....go figure that a package "dialog" is needed for the command dialog. But this is why the forum is here I guess. THanks.

---

