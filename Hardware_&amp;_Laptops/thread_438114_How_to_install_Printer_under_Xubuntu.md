---
title: "How to install Printer under Xubuntu?"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by jjalocha on 2007-05-09
I just bought a printer that is know to work well under Linux, an Epson Stylus CX3900. I am trying to make it work under Xubuntu Feisty, but I think I don't have a clue, since this is my first printing experience under Linux.

This is a multifunctional, but for now, I am just trying to print. There's a thread about [getting the scanner to work]("http://ubuntuforums.org/showthread.php?t=410220"), with which I will deal later.

The [Hardware Support Components Printers Epson]("https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson") Wiki page says that the printer should work out of the box, but under Xubuntu it doesn't work for me.

The [Xubuntu Desktop Guide]("https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html") (only for Dapper) says that I have to "add the printer", which I can do with a browser, or a terminal. Since I've had to setup wifi, graphics, sound and others in the past, I tried the command line method.

[FONT="Fixedsys"]lpinfo -v[/FONT] seems to detect my printer when plugged into USB:

```

direct hal:///org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_printer_noserial
direct usb://EPSON/Stylus%20CX3900

```

But I have no idea what parameters I should add to [FONT="Fixedsys"]lpadmin[/FONT], to actually get it work. (I think it's the printer name, device name and driver name).

So I tried to use the web-browser method. First, I have to make the web interface available. So, in the Users&Groups Manager I should add the 'cupsys' user to the 'shadow' group. But this group doesn't exist!

I would really appreciate if someone with a little bit of experience could give me some guidance through this labyrinth. Thank you very much.

---

### Post by jjalocha on 2007-05-09
OK, I finally found out that when I plug in the USB printer, [FONT="Fixedsys"]/dev/usblp0[/FONT] appears. Supposing that the [FONT="Fixedsys"]-p[/FONT] option is just a fantasy name, and that the driver I need is 'stcolor.ppd', I tried the following:

```

$ lpadmin -p EpsonStylus -E -v usb:/dev/usblp0 -m stcolor.ppd
lpadmin: Unable to copy PPD file!

```

Does anybody know why the error message? 'stcolor.ppd' DOES exist under '/usr/share/ppd/cups-included/Epson/stcolor.ppd'. 'sudo' doesn't help either.

What am I doing wrong?

---

### Post by jjalocha on 2007-05-09
OK, according to various posts elsewhere, I tried the following variants without success (both with and without 'sudo'):

```

$ lpadmin -p EpsonStylus -E -v usb:/dev/usblp0 -m /usr/share/ppd/cups-included/Epson/stcolor.ppd

```

```

$ sudo ln -s /usr/share/ppd/cups-included/Epson/stcolor.ppd /usr/share/ppd/stcolor.ppd

```

```

$ sudo cp /usr/share/ppd/cups-included/Epson/stcolor.ppd /usr/share/ppd

```

Anyone knows how to help, please?

---

### Post by jjalocha on 2007-05-09
bump.

Help, please.

I am really out of ideas now!

---

### Post by takayuki on 2007-05-10
Hi,

i'm sitting here trying to install a printer on xubuntu 6.06.

i don't know what i'm doing either, but here's where I'm at...

1. installed cups via the terminal:

sudo apt-get install cupsys*


2. then, in firefox, go to:  [http://localhost:631/admin](http://localhost:631/admin)


3. click the Administration tab.  Hopefully your printer will be recognized.  


Here's where I'm stuck.  i found the driver (a "ppd" file) here: [http://www.linuxprinting.org](http://www.linuxprinting.org).  but when i try to load it via [http://localhost:631/admin](http://localhost:631/admin), i get a can't authenticate error.  i'm googling on that now...

note: fixed the authenticate error by entering the following line into the terminal:
sudo adduser cupsys shadow

now my print jobs load, but don't actually print.  i get a "/usr/lib/cups/filter/foomatic-rip failed" error.  googling that now...

that ain't much, but misery loves company.

takayuki

---

### Post by jjalocha on 2007-05-10
Thanks, takayuki!
I didn't realize that in Xubuntu Feisty I was already able to enter the administration page 'http://localhost:631/admin'. There was NO NEED to set any users, groups or passwords to enter the administration tool. Later, when asked for a password for "CUPS at http://localhost:631", I just entered my login name and password, and everything went fine.

Actually, my model (Epson Stylus CX3900) is not listed when I try to add my printer, but the test page printed with the CX3700 driver looks perfect to me.

Now, I am trying to install the (official?) CX3900 driver from [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html).

---

### Post by PhilJ on 2007-05-12
[http://howto.gumph.org/content/use-smb-printer-in-xubuntu/](http://howto.gumph.org/content/use-smb-printer-in-xubuntu/)


some info on this page

philj

---

### Post by strabes on 2007-05-12
Going to localhost:631 and then addinng the printer using the interface doesn't work?

---

### Post by jjalocha on 2007-05-13
Thank you both, PhilJ and strabes, for your answers. As I said in my post #6, I didn't realize that I was already able to enter 'localhost:631' without changing any user/group permissions. When a user/password window pops up, I just use my personal name/password, which works fine.

On my system (Xubuntu Feisty), the 'Users and Groups' tool doesn't even display the 'shadow' group, and there's no 'show all' checkbox (or whatever else). So it seems to be useless here. But I can set the correct permissions through the command line, as suggested in [your link]("http://howto.gumph.org/content/use-smb-printer-in-xubuntu/"):

```

$ sudo usermod -G shadow -a cupsys

```

Since my CX3900 printer is not in the drivers list, I am using the CX3700 driver, which seems to work fine, so far.

---

### Post by venzie on 2007-12-29
Is it really this hard to install things on Xubuntu? I'm a newbie and I really get turned off when I have to do things terminal (read: complicated) way. I just moved to Xubuntu, and I must say installing printer drivers in windows and mac weren't this complicated.

---

### Post by jjalocha on 2007-12-29
Don't worry, at least in Xubuntu Gutsy, installing this printer was easy: just plug'n'play! :)

---

### Post by MartijnNL on 2008-01-16
> **jjalocha said:**
> Don't worry, at least in Xubuntu Gutsy, installing this printer was easy: just plug'n'play! :)

Well, I tried installing my Deskjet 950 under Xubuntu Gutsy (using settings -> printing). It recognized the printer fine, and found the driver as well. But when I clicked apply it asked for my password, and kept doing so everytime after I gave it and clicked ok. I had no choice but to cancel the install, as the pop-up just kep asking for my password.

Any workaround for this?

Martijn

---

### Post by MartijnNL on 2008-01-16
I think I found a workaround myself. I did some other administrative task first, which required my password. Immediately after that I installed the printer without need for my password. But I did this with another useraccount, so I can´t say for sure this is a workaround.

Anyway, it did the job.

---

