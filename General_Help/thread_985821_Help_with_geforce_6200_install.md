---
title: "Help with geforce 6200 install"
date: 2008-11-18
forum: General Help
---

### Post by h4ppydaze on 2008-11-18
I got Ubuntu 8.10 to run well with my intel integrated card (845g) once I entered the fail-safe and disabled compiz. However, I upgraded my graphics card and now I am having issues. 

I installed the newest nvidia x and changed my settings to boot from PCI instead of my poop integrated intel graphics. What happens is that the load bar for Ubuntu just freezes right before it gets to three bars. This happens in safe recovery mode too. 

this is my xorg.conf file

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

before I shut down to install my card, I changed one line, I changed it to this.

```

Section "Device"
	Identifier	"Configured Video Device"
        Driver          "nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

any ideas? I can't even get into the fail-safe terminal to figure things out. I changed my xorg back and reverted to my integrated to post up here for a solution

edit:

lspci | grep -i nvidia does not produce a line of text

---

### Post by h4ppydaze on 2008-11-18
I am going to reinstall ubuntu and see if that will fix it. This problem is making me go nuts, I had such a time just getting integrated to work.

---

### Post by easoukenka on 2008-11-18
sudo dpkg-reconfigure xserver-xorg

you can also run envy which will automatically get your drivers for you and help you out

sudo apt-get install envy-gtk
then run envy -t 

now uninstall all old drivers with that tool then try the automatic installation


Also try booting up to the live cd and grabbing a copy of /etc/X11/xorg.conf email it to yoruself then bootup and try that file. 

good luck

---

### Post by h4ppydaze on 2008-11-18
thanks for the help I will try that and get back to you guys. one thing though, on the envy site it doesn't say that intrepid is supported. That's not going to cause problems is it?

---

