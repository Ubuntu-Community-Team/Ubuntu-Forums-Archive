---
title: "Newbie's day-6 question - ThinkVision display"
date: 2012-01-15
forum: Hardware
---

### Post by chenxinghao on 2012-01-15
Installed Ubuntu 11.10 several days ago on an IBM ThinkCentre A50P 8432-94U, with the dual-boot option - the master HD has the Windows XP Pro and half of the slave HD, while Ubuntu has the other half of the slave HD (both HDs are WD 300GB disks); used all default installation setting and no tweaks in my part.
 
Now just discovered that the IBM ThinkVision L170 display shows up in Dash -> Installed -> Display as a pp!France 17" unit, with a 1280x1024 (5:4) resolution setting.
 
The display seems to work just fine. Just that every time using emacs in a Terminal window, it would produce GTK related warning messages, though emacs functions seem not affected.
 
I have not used Ubuntu long enough to notice any display problems.
 
The question is why an IBM ThinkVision L170 display shows up in Ubuntu as a pp!France 17"? Any potential problem with this and what I need to do?

---

### Post by 2F4U on 2012-01-15
You can ignore the name of the monitor. My LG monitor is also not reported as that but works just fine.
With respect to the terminal error messages there have been reports about these on the forum. I don't know your exact error messages but if Emacs works fine they are most likely just warnings. You could post them here so that we have a look at them.

---

### Post by chenxinghao on 2012-01-15
The message after open emacs looks as the following:

chenxinghao@MyUbuntuSandBox:~$ emacs testpapge 

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",

(emacs:5640): Gtk-WARNING **: Unable to locate theme engine in module_path: "pix
map",


The "WARNING" doesn't seem to have effects on emacs functions.

I like to understand the meaning and why they were out every time I use emacs.

Thank you.

---

### Post by MG&amp;TL on 2012-01-15
As mentioned in your other thread, it is  Gtk2/3 compatiblity problem, not anything to do with your monitor.

Googling the error produces this: [http://yoodey.com/solving-gtk-warning-unable-locate-theme-engine-modulepath-pixmap](http://yoodey.com/solving-gtk-warning-unable-locate-theme-engine-modulepath-pixmap)

---

### Post by chenxinghao on 2012-01-15
Thanks for the new link and did the following in a Terminal window:

chenxinghao@MyUbuntuSandBox:~$ sudo apt-get install gtk2-engines-pixbuf
[sudo] password for chenxinghao: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gtk2-engines-pixbuf
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 127 kB of archives.
After this operation, 1,069 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe gtk2-engines-pixbuf i386 2.24.6-0ubuntu5 [127 kB]
Fetched 127 kB in 0s (127 kB/s)               
Selecting previously deselected package gtk2-engines-pixbuf.
(Reading database ... 157637 files and directories currently installed.)
Unpacking gtk2-engines-pixbuf (from .../gtk2-engines-pixbuf_2.24.6-0ubuntu5_i386.deb) ...
Setting up gtk2-engines-pixbuf (2.24.6-0ubuntu5) ...
chenxinghao@MyUbuntuSandBox:~$ emacs emacs-test


No GTK warning messages any more - clean emacs at last!

Thanks.

---

