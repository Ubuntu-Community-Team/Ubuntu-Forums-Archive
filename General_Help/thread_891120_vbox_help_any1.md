---
title: "vbox help any1?"
date: 2008-08-15
forum: General Help
---

### Post by Howitzer777 on 2008-08-15
1st problem: when i go to settings i get 
```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}


3rd problem.

my xp resolution only give me 800-640 or something like that and 1024-700 (somehitn like that) its only fills up 40 percent of my screen. how can i change this/

 
```

how do i fix this for usb devices to work?

2nd problem. how can i get files from xp(guest) back to ubuntu?

---

### Post by mikewhatever on 2008-08-15
Check out the FAQ on USB [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
> USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

/etc/init.d/mountdevsubfs.sh start


If you don't use usb in vbox, disable it.

---

### Post by dje on 2008-08-15
good guide [here]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html"), follow it right through and it should fix your problem

dje

---

### Post by Howitzer777 on 2008-08-15
still no dice


i did everything on that guide, but i still get the same error when i go to settings. 

it could be that when i was configuring it. it said that it had found the old virtual box files and wanted to know if i should back it up or save it. i chose backit up

---

