---
title: "Xubuntu with no monitor"
date: 2008-10-09
forum: General Help
---

### Post by GXice on 2008-10-09
Hi all, I'm just looking to get some advice on this matter because I have no idea what to do.

I've got a system built which is just a box, no monitor, keyboard or mouse. I want to operate it remotely through a far better computer running Vista Ultimate and the Xubuntu one will just be used as a torrent box.

I understand I can use VNC or a KVM switch. VNC requires no hardware, so that's my first preference. What are the programs I'll need to successfully be connectible from my Vista compy?

A guide or something would be best, as I have no idea what steps to take.. :(

---

### Post by _sAm_ on 2008-10-09
Try NX([http://www.nomachine.com/](http://www.nomachine.com/)), its very fast, easy to install and very secure. Clients for Windows and you can download a deb file for the server to install there.

Have fun:-D

---

### Post by GXice on 2008-10-09
Hmm.. it looks good but what do I do with it?

Which one needs to be client, which one server? Do I get the deb file for the Ubuntu and get a Client for Windows for the Windows one?

---

### Post by _sAm_ on 2008-10-09
Download the deb file for Xbuntu/http://www.nomachine.com/download-package.php?Prod_Id=6), and install it(this is the server). 

Download the exe file for Windows([http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)). 

On Windows you can open NX to connect to your Xbuntu box, and get the desktop from it.

Cli solution would bee ssh on Xbuntu and perhaps putty on Windows.

---

### Post by GXice on 2008-10-09
Ah, excellent! I will try this tomorrow morning, thanks very much :D

---

### Post by GXice on 2008-10-09
Out of interest, what other alternatives do I have?

Ideally, I'd like to operate the Linux computer from Vista with no lag. I read that programs like UltraVNC lag quite badly. Does NX lag as well?

---

### Post by GXice on 2008-10-10
Bump? :'(

---

### Post by llebegue on 2008-10-10
For no lag you should operate it through SSH ans a command line interface.

Install openssh-server (you will need a monitor for this) on Xubuntu.

Use "putty" on your windows computer to connect to your xubuntu computer.

---

### Post by _sAm_ on 2008-10-11
NX use ssh and its even better since they compress the signal.

---

