---
title: "unable to install printers"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by lhtown on 2005-03-21
I am running hoary (upgrade from warty) on a laptop. 

Under warty my usb printer worked fine. Now, I am unable to install my printer. When I try to install it using the System-administration-printing dialog, it recognizes it corrrectly as an Epson Stylus C83, but when I click finish, it closes and no new icon appears in the printer folder and none of my programs recognize a new printer.

Also, in looking for the solution to that problem, I noticed that several of the packages that depend on ubuntu-base in my system do not have the little ubuntu symbol beside them in synaptic. I understand the symbol means that it is an officially supported packaged. How could a package depend on ubuntu-base and not be officially supported?

I am talking about programs such as hotplug, grepmap, and reiser4progs not to mention the linux kernel

Any ideas?

I have not removed ubuntu-base or ubuntu-desktop.

I have been using Hoary for a month of so and everything else works great.

---

### Post by cdhotfire on 2005-03-21
install cupsys-driver-gimpprint in synaptic, or apt-get
```
sudo apt-get update
sudo apt-get install cupsys-driver-gimpprint
```

that should add it.

---

### Post by lhtown on 2005-03-21
[QUOTE=cdhotfire]install cupsys-driver-gimpprint in synaptic, or apt-get
```
sudo apt-get update
sudo apt-get install cupsys-driver-gimpprint
```

that should add it.[/QUOTE]

Sorry, but it is already installed. It seems to recognize the printer fine. In fact, the whole install process *appears* to work flawlessly. The only problem is that it seems to do absolutely nothing and I am left unable to use my printer. It is as though there is a user/permissions problem or maybe two packages that are conflicting. Or maybe it is just a strange bug.

---

### Post by swoon on 2005-03-21
i'm having the same problem with my lexmark printer. it shows up fine, finds the driver- just doesn't print at all.

---

### Post by tweakerxp on 2005-03-21
[QUOTE=swoon]i'm having the same problem with my Lexmark printer. it shows up fine, finds the driver- just doesn't print at all.[/QUOTE]
I have never seen a Lexmark printer work in any Linux Distribution. I know that they show in the printer configuration, but I have never seen a Linux driver for any modern Lexmark printer.

 Do not try to print to a Lexmark printer under Linux unless you're absolutely certain that you have the correct drivers. I have found that Linux drivers / files can often modify the firmware on Lexmark printers, rendering them partially useless (certain functions will no longer work, others will.)This is especially common with all-in-one devices.

---

### Post by cdhotfire on 2005-03-21
for the epson printer do this to check connection
```
 escputil -i -u -r /dev/lp0
```

where /dev/lp0 should be replaced with the name of your printer port.

---

### Post by cdhotfire on 2005-03-21
[QUOTE=tweakerxp]I have never seen a Lexmark printer work in any Linux Distribution. I know that they show in the printer configuration, but I have never seen a Linux driver for any modern Lexmark printer.

 Do not try to print to a Lexmark printer under Linux unless you're absolutely certain that you have the correct drivers. I have found that Linux drivers / files can often modify the firmware on Lexmark printers, rendering them partially useless (certain functions will no longer work, others will.)This is especially common with all-in-one devices.[/QUOTE]

i second that

edit: i tried my lexmark z715, did everything couldnt get it to work, changed to epson c60 and worked flawlessly.

---

### Post by lhtown on 2005-03-21
[QUOTE=cdhotfire]for the epson printer do this to check connection
```
 escputil -i -u -r /dev/lp0
```

where /dev/lp0 should be replaced with the name of your printer port.[/QUOTE]


Here are the results:

root@ubuntu:/home/luke # escputil -i -u -r /dev/usb/lp0
Escputil version 4.2.7, Copyright (C) 2000-2001 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

           Ink color    Percent remaining
               Black     25
                Cyan     14
             Magenta     92
              Yellow     42

---

### Post by cdhotfire on 2005-03-21
seems, so its working.  What are you trying to print, because maybe its the program that is not sending it to the printer.

---

### Post by lhtown on 2005-03-21
[QUOTE=cdhotfire]seems, so its working.  What are you trying to print, because maybe its the program that is not sending it to the printer.[/QUOTE]

Obviously, the printer is being recognized. However, as I mentioned before, when I go through the install process, it seems normal, except that it does not produce an icon in the printing admnistration box and neither does it appear as an option in any of my programs.

Bottom line: It doesn't work for me.

Any other ideas?

---

### Post by lhtown on 2005-03-21
It's working!

I went into /etc/cups/ppd and found the .ppd driver for my printer. I checked the permissions and noticed that they were pretty anemic including group and root read and root write. I deleted that file (driver) from the command line and reinstalled the printer from the gui. It now works like a charm. It seems that it should have had "others" read permission. I suppose that I could also have added my user name to the group, but I just let it do its thing.

Thanks everyone.

Special thanks to cdhotfire for introducing me to the escputil utility. I didn't know there was a way to check my ink levels before which really made it a problem to know which cartridge was empty- I had to connect it to my windows box everytime I ran out of ink to figure out which of the four cartridges to change.

---

### Post by swoon on 2005-03-21
[QUOTE=cdhotfire]i second that

edit: i tried my lexmark z715, did everything couldnt get it to work, changed to epson c60 and worked flawlessly.[/QUOTE]

it worked really well under warty is the thing.

---

### Post by cdhotfire on 2005-03-21
[QUOTE=lhtown]It's working!

I went into /etc/cups/ppd and found the .ppd driver for my printer. I checked the permissions and noticed that they were pretty anemic including group and root read and root write. I deleted that file (driver) from the command line and reinstalled the printer from the gui. It now works like a charm. It seems that it should have had "others" read permission. I suppose that I could also have added my user name to the group, but I just let it do its thing.

Thanks everyone.

Special thanks to cdhotfire for introducing me to the escputil utility. I didn't know there was a way to check my ink levels before which really made it a problem to know which cartridge was empty- I had to connect it to my windows box everytime I ran out of ink to figure out which of the four cartridges to change.[/QUOTE]

Hehe no problem dude, take it ez.:smile:
Srry i couldnt help you out more.:-|

---

### Post by scr621 on 2005-04-26
[FONT=Century Gothic]I'm having the EXACT same problem with my Lexmark X75 Printrio.
I'm wondering if it's somehting to do with admin rights??
Can someone please tell me how u turn these off.  I AM the admin, but there are certain things I can't do for some reason.

Any help with admin rights & my printer would be very very much appreciated thanx

scr621   ](*,)

---

### Post by David Haas on 2005-04-26
Because you have, you say, the cupsys and foomatic packages installed (check Synaptic for this) and because the gimp-print ppd file for the Epson Stylus C83 is available in Ubuntu, your printer should work. Have you selected the gimp-print ppd file? It's located at /usr/share/cups/model/gimp-print/4.2 and it's listed as escp2-c83.ppd.gz. I have found--with my Epson Stylus C82--that if I make a mistake in selecting the printer or ppd file in the printer GUI, then it's best to start over and select "New Printer" before selecting the printer and ppd file in the printer GUI. So after you select your printer, click through the files to "4.2" to select your ppd file. Of course, once you select your Epson model, it should be listed in the printer GUI icon. If not, then more thought and help are needed.
David Haas

---

### Post by cdhotfire on 2005-04-26
[QUOTE=David Haas]Because you have, you say, the cupsys and foomatic packages installed (check Synaptic for this) and because the gimp-print ppd file for the Epson Stylus C83 is available in Ubuntu, your printer should work. Have you selected the gimp-print ppd file? It's located at /usr/share/cups/model/gimp-print/4.2 and it's listed as escp2-c83.ppd.gz. I have found--with my Epson Stylus C82--that if I make a mistake in selecting the printer or ppd file in the printer GUI, then it's best to start over and select "New Printer" before selecting the printer and ppd file in the printer GUI. So after you select your printer, click through the files to "4.2" to select your ppd file. Of course, once you select your Epson model, it should be listed in the printer GUI icon. If not, then more thought and help are needed.
David Haas[/QUOTE]

hehe, nice try sir, as u might notice he said he got the problem solved. But thanks for trying to help the man.:-?

---

### Post by David Haas on 2005-04-26
After choosing your printer, the Epson Stylus C83, in the Printer GUI, did you select the PPD file for it? It's listed in the Gimp-Print 4.2 directory, which you can click to in the printer GUI; it's at /usr/share/cups/model/gimp-print/4.2. The PPD file is escp2-c83.ppd.gz. I found that on mis-selecting files in the printer GUI, it was best to start over by selecting "New Printer." I assume that you have installed the cupsys and foomatic packages (you've probably checked this in Synaptic). CUPS won't send files to the printer unless they are correctly formated.

---

