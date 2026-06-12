---
title: "VirtualBox Help"
date: 2008-10-24
forum: General Help
---

### Post by chr3681 on 2008-10-24
Okay, so I am trying to use VirtualBox to run Vista under Ubuntu 8.04.1 (or whatever the latest upgrade is). I downloaded the .deb from VirtualBox's site that they said would work for 8.04. I ran and installed with no errors, but now when I type "virtualbox" in terminal to launch the program, it says that it is not installed and gives me the suggestion to run "sudo apt-get install virtualbox-ose". I shouldn't have to do this though as I have already installed the software. Any ideas?

Thanks in advance for the help!

Chris

---

### Post by Elfy on 2008-10-24
The command is ```
VirtualBox
```note the case

There should also be a launcher in System Tools

---

### Post by chr3681 on 2008-10-24
Wow I feel dumb =P... Well that worked fine and then I get this error when accessing the "preferences":

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}


What is this error telling me? That my usb will not work? Any fixes?

---

### Post by Elfy on 2008-10-24
[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

You are using the PUEL version - just in case you're not sure

---

### Post by chr3681 on 2008-10-24
Thanks for the help and quick responses!

Lastly, if I wanted to convert my Vista partition to a VM to run in VirtualBox; 1. is it possible? 2. how do I do it if it is?

Thanks again!

---

### Post by Elfy on 2008-10-24
I don't believe that is possible, I did that once with an old win2k install - but I was using vmware at the time.

Once you do have it installed you will need to get the guest additions installed to get better resolution and to allow mouse to be used everywhere without releasing it.

It might well be worth getting hold of the manual - I found it helpful, it's on the download page

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by chr3681 on 2008-10-24
Yeah, reading through that seems like it's going to be very helpful! I'm excited about trying out seamless mouse and windows too, that looks pretty awesome. I'm going to leave this post unsolved for now in case I have anymore questions during my setup tomorrow!

---

