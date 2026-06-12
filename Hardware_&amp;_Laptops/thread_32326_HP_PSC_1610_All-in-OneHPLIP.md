---
title: "HP PSC 1610 All-in-One/HPLIP"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by Calgarian on 2005-05-07
I installed this several times under SuSE with no issue. I dropped SuSE for other issues. I'm now trying this in Kubuntu. I followed the Debian path of the HP instructions. I'm not a Linux techie, but I've used it for a few years. I get these messages on my "make install" command. I know foomatic is installed and I can't locate the other modules at all. Can anyone offer some assistance? TIA

make[3]: *** [install-foomatic] Error 2
make[3]: Leaving directory `/home/dick/Documents/LinuxDocuments/HP-All-in-one/hplip-0.8.8/prnt/hpijs'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/dick/Documents/LinuxDocuments/HP-All-in-one/hplip-0.8.8/prnt/hpijs'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dick/Documents/LinuxDocuments/HP-All-in-one/hplip-0.8.8/prnt/hpijs'
make: *** [install-recursive] Error 1
root@cm-85-152-80-253Canuck:/home/dick/Documents/LinuxDocuments/HP-All-in-one/hplip-0.8.8 # /etc/init.d/hplip restart
bash: /etc/init.d/hplip: No such file or directory

---

### Post by kleeman on 2005-05-07
The hplip package is in the universe repository. I remember reading that installing hplip fro source is not a good idea. So do

sudo apt-get install hplip

I think it removes ubuntu-desktop but apparently this is only an issue when upgrading a distro.

---

### Post by Calgarian on 2005-05-08
I thought I had done that, but I guess I missed it. That worked fine. Now I can't locate the PSC 1610 in the device selection list when I do device configuration. I tried the 2110 just to see what happens and that worked for printing. Now I try to get the HP Device Manager up by running /usr/lib/hplip/toolbox so I can configure the scanner in this box and I get nothing. If I try it in a console I get some startup messages and then it just hangs there. I'm sure I've done something silly to screw it up, but I'd sure like to get this working. It worked fine on my old SuSE 9.3, but setup was much more difficult there. Thanks in advance for the help.

---

### Post by kleeman on 2005-05-08
Did you follow the instructions from here

[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

for installing a new printer with hplip?

---

### Post by Calgarian on 2005-05-08
I did follow these. Just to make sure I did all the steps again. When I open the browser to get [http://localhost:631](http://localhost:631) I get a connection refused message. I can't get to it with Firefox.

---

### Post by kleeman on 2005-05-08
OK I can (get 631 to open in firefox). Do you have the cupsys package installed?

---

### Post by Calgarian on 2005-05-08
I do - it's cupsys 1.1.23-1 from the ubuntu repository.

---

### Post by kleeman on 2005-05-08
I am not a cups expert but from what I can gather you should be able to access this address if you have the cups server running properly. Try restarting the cups daemon with

sudo /etc/init.d/cupsys restart

Also try entering NAME:631 in the browser address bar where NAME is the name of your computer.

---

### Post by Calgarian on 2005-05-08
I did a hard reboot and finally got localhost:631 to work. I selected manage printers and asked to add a printer. I got a request for a user id and password for cups. My user id didn't work, root with my password didn't work, and leaving it blank didn't work.

I really appreciate all your assistance with this. I've used Linux for a number of years, but never this far under the covers. It's a learning experience.

---

### Post by Calgarian on 2005-05-08
When I canceled the request for a password I got - Unauthorized
Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing).

Should I use the KDE print manager instead?

---

### Post by kleeman on 2005-05-08
Yeah I would. I have always found kprinter the best wizard for setting up printers as it is very comprehensive. Cups is quite complicated  :smile: Every difficult linux experience has a silver lining in the future  :)

---

### Post by kleeman on 2005-05-08
BTW you may wish to set a root password to get admin rights under cups. To do this open up a root terminal (Applications--> System Tools --> Root terminal) and then enter passwd at the prompt.....

---

### Post by Calgarian on 2005-05-09
I used the KDE Printer Manager and added the entry for my printer. (Now it has announced the colour cartridge is out - this setup is jinxed). I ran hplip_toolbox and got the following output in a console:


dick@cm-85-152-80-253localhost:~$ hplip_toolbox
 HP Linux Imaging and Printing System (ver. 0.9.2)
 Toolbox/Device Manager ver. 2.0
 Copyright (c) 2003-4 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Running new hpguid instance...
python: can't open file '/usr/share/hplip/hpguid.py': [Errno 2] No such file or directory
Traceback (most recent call last):
  File "/usr/bin/hplip_toolbox", line 57, in ?
    time.sleep(0.5)
KeyboardInterrupt

I moved a copy of the missing file from /usr/lib/hplip to /usr/share/hplip and tried again and got:

root@cm-85-152-80-253localhost:/home/dick # hplip_toolbox
 HP Linux Imaging and Printing System (ver. 0.9.2)
 Toolbox/Device Manager ver. 2.0
 Copyright (c) 2003-4 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Running new hpguid instance...
Traceback (most recent call last):
  File "/usr/share/hplip/hpguid.py", line 99, in ?
    from ui.form1 import Form1
ImportError: No module named form1

In looking around I might have a mix of hplip-0.8.8 and 0.9.x. I think I'll remove anything that looks like hplip and do a clean start.

---

### Post by Calgarian on 2005-05-09
Slow and steady progess - I hope? I deleted all the HPLIP modules and reinstalled the 0.0.2 version. Now the toolbox works, but it can't see any devices. I added the printer with the KDE print manager because I can't get root access through localhost:631. It is not a cupsbackend device so it isn't seen. I guess I need to find out how to get root access through the browser and add it there? Is there an alternative?

---

### Post by Calgarian on 2005-05-09
I added a printer in the system->settings->peripherals->printers. I added it as the drop down HP->PSC 1600 hpijs. toolbox doesn't see this as it is not an HP-backend printer. I've tried several ways to get into the backend with no success. Any tips for that?

---

### Post by Calgarian on 2005-05-09
:grin: Well yahoo, but don't ask me how. As stated above I cleaned out hplip, reinstalled from the latest version (source install from HP), added the printer to KDE Print Manager and had no luck at all. I deleted and added the rpinter several times and did system restarts several times. Finally I created a root password from the Ubuntu HowTo. I ended my session and tried to login as root and was told I couldn't do that. I logged in again as me and there was the printer in the HP Device Manager. The scanner works, the printer works, and I haven't tried the photo cards yet.

---

### Post by kleeman on 2005-05-09
Bloody hell that sounds like torture! Congats anyway!

---

