---
title: "VirtualBox USB error"
date: 2008-08-31
forum: Hardware
---

### Post by mitasjp on 2008-08-31
Olá,

I have the following error when starting Sun xVM VirtualBox and I can´t have access to usb in my WinXP guest. The VirtualBox USB icon is also grey, what I have to do to use it.

;-)


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x00004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {f95c0793-7737-49a1-85d9-6da81097173b}[/B][/B]

---

### Post by eggdeng on 2008-08-31
If you installed the OSE version (from the repos), it does not support usb. You need to remove it & download & install the PUEL edition from [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")
There is a how-to for enabling usb at [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

---

