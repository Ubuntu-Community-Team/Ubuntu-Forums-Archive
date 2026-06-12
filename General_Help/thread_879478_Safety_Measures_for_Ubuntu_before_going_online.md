---
title: "Safety Measures for Ubuntu before going online"
date: 2008-08-04
forum: General Help
---

### Post by deepakOne on 2008-08-04
I have recently installed Ubuntu 8.04LTS and planning to go online using same (currently using VISTA for that)
So are there any software's like Firewall, Anti virus etc. need to install before going online.
Current internet browsing ratio of Ubuntu and Vista is 10:90 and planning to make 60:40. Major purpose of browsing is 
download using torrent (uTorrent on Wine), so please comment. Also comment on performance of uTorrent on Ubuntu will really help.

---

### Post by cpetercarter on 2008-08-04
The short answer is that you do not need any special anti-virus or firewall software. Linux is inherently more secure than Windows and is not affected by Windows viruses. Ubuntu contains a built-in firewall the default settings for which are very conservative. You can download Firestarter to configure the firewall if you wish, but for the uses you mention this is not really necessary. There are numerous posts in the security section of this Forum which explain more about security in Linux/Ubuntu systems.

---

### Post by jasex on 2008-08-04
uTorrent runs alright... but a custom gcj compiled Azureus, or Transmission would be better, as it would be one... native to the system, and two in reasoning with the gcj compiled azureus... custom fit to your system.

---

### Post by mb_webguy on 2008-08-04
As previously mentioned, you don't have to worry about anti-virus programs on Linux -- for the most part.  Linux is inherently more secure than Windows, but if you're using some method to run Windows programs on Linux, you may open yourself up to Windows' security flaws.  If you run Windows in a virtual machine, for example, you can get viruses in the VM.

If you want to go online with Linux, just do it, and smile and wave as the viruses pass you by.

I love uTorrent on Windows, but *Linux isn't Windows*.  There are equivalent applications on Linux that are just as good if not better.  Running a program on Linux that is designed to run on Linux is fairly obviously going to be better (faster, more secure, etc.) than running a program on Linux designed to run on Windows.

Ubuntu comes with the Transmission torrent client, which is pretty decent.  But if you want something more like uTorrent, look into Deluge.  It has a similar interface, and all of the features you're used to having in uTorrent.

---

### Post by adult swim on 2008-08-04
i just learned earlier tonight that the firewall for hardy is by default not enabled.  firestarter used to work with iptables but now the ubuntu firewall is the uncomplicated firewall, ufw.  to turn it on you can do ```
sudo ufw enable
``` i must say i liked iptables with the firestarter gui much better!
EDIT: what i learned tonight!
above is wrong.  by default the firewall is on.  ufw is merely a way to control IPTables.  while ufw is initially disabled, the firewall is working.  when you enable ufw you are enabling it to manipulate the firewall.  Firestarter still does the same thing, but it hasnt been updated in a while and it doesnt look like it is going to be.

---

### Post by tinny on 2008-08-04
> **adult swim said:**
> i just learned earlier tonight that the firewall for hardy is by default not enabled.  firestarter used to work with iptables but now the ubuntu firewall is the uncomplicated firewall, ufw.  to turn it on you can do ```
sudo ufw enable
``` i must say i liked iptables with the firestarter gui much better!

Configuring your firewall to work correctly with the torrent applications you plan on using will be a real PAIN!!! I advise you stay away from the firewall.

The torrents will work but the performance of your downloads will be capped (limited ports). You can get around this, but it is a more advanced firewall setup than what I sense you are prepared to take on.

---

### Post by cariboo on 2008-08-04
You may want to install clamav if you are planning on using whatever you download on windows. Ubuntu may not be affected by viruses, but windows seems to be a virus magnet You may want to have a look here:

[http://ubuntuforums.org/archive/index.php/t-318091.html](http://ubuntuforums.org/archive/index.php/t-318091.html)

The tutorial is a little bit old, but should still work.

Jim

---

### Post by Sef on 2008-08-04
> i just learned earlier tonight that the firewall for hardy is by default not enabled. firestarter used to work with iptables but now the ubuntu firewall is the uncomplicated firewall, ufw. to turn it on you can do

That is incorrect.  IPTables are installed by default and working.  ufw is simply a gui to use it instead of using the command line.

---

### Post by adult swim on 2008-08-04
> **Sef said:**
> That is incorrect.  IPTables are installed by default and working.  ufw is simply a gui to use it instead of using the command line.

so ufw is a commandbline gui? does firestarter still control iptables?

---

### Post by tinny on 2008-08-04
> **adult swim said:**
> so ufw is a commandbline gui? does firestarter still control iptables?

UFW is a simplified command line tool for configuring IPTables. Firestarter configures IPTables, its a GUI tool.

---

### Post by hyper_ch on 2008-08-04
no antivirus needed
no twinkering with the firewall needed

in some cases you might want to run antivirus and/or firewall

---

### Post by robert shearer on 2008-08-04
For a boots and braces approach you could try Guarddog. It is in the repositories and, after downloading and installing, it needs to be started from the terminal using" gksudo guarddog". This brings up the gui configurable as superuser.

See the guarddog website for a very helpful manual for use and setup.

Once configured on dialup I had this report a 'true stealth ' result from the Gibson Research Group test site.
Of course, using dsl the router/modem is seen by the testing utility and reports many more ports but guarddog stands between this and the computer and maintains its configuration.

---

