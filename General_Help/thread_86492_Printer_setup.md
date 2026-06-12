---
title: "Printer setup"
date: 2005-11-05
forum: General Help
---

### Post by canadianwriterman on 2005-11-05
Does anyone know what I need to do to make my Ubuntu Breezy "add printer" work the same way as Kubuntu? I took Kubuntu for a spin yesterday and like Ubuntu better. But Kubuntu worked fantastic with my printer and had a different setup utility.

---

### Post by Xian on 2005-11-05
Kubuntu uses the KDE Control Center which is not avail for Gnome. 
You have a couple of options. 

1. From the main panel:
System > Administration > Printing

2. Place this addy in your browser:
[http://127.0.0.1:631/](http://127.0.0.1:631/)

You really should always use method 2 as it is universal to 
almost any Linux desktop installation.

---

### Post by canadianwriterman on 2005-11-05
[QUOTE=Xian]Kubuntu uses the KDE Control Center which is not avail for Gnome. 
You have a couple of options. 

1. From the main panel:
System > Administration > Printing

2. Place this addy in your browser:
[http://127.0.0.1:631/](http://127.0.0.1:631/)

You really should always use method 2 as it is universal to 
almost any Linux desktop installation.[/QUOTE]

I hadn't seen that browser-based set up before. Only trouble is, it asks me for a username and password, and my normal ones (that I use to login to my Ubuntu desktop) do not work.

---

### Post by Xian on 2005-11-05
[QUOTE=canadianwriterman]I hadn't seen that browser-based set up before. Only trouble is, it asks me for a username and password, and my normal ones (that I use to login to my Ubuntu desktop) do not work.[/QUOTE]
You have to set a system UNIX password.
From the terminal:

```
$ sudo passwd
```

---

### Post by canadianwriterman on 2005-11-05
[QUOTE=Xian]You have to set a system UNIX password.
From the terminal:

```
$ sudo passwd
```[/QUOTE]

Thanks, that took care of the password. However, the utility still wants a username and my Ububtu username is not accepted. How do I set a username?

---

### Post by Xian on 2005-11-05
[QUOTE=canadianwriterman]Thanks, that took care of the password. However, the utility still wants a username and my Ububtu username is not accepted. How do I set a username?[/QUOTE]
It's my bad on this one. That function had been disabled in Ubuntu.
You'll have to go the route of method #1.

But hey, you have a shiny new UNIX password. :)

---

### Post by canadianwriterman on 2005-11-05
[QUOTE=Xian]It's my bad on this one. That function had been disabled in Ubuntu.
You'll have to go the route of method #1.

But hey, you have a shiny new UNIX password. :)[/QUOTE]

Oh dear. Okay, thanks. Just to retouch my original question. I understand that KDE utilities are used in Kubuntu and not in Ubuntu. However, the end result of setting up my printer in Kubuntu is that it works, but not in Ubuntu. I notice that there are lots of CUPS and Foomatic files in the repositories. Would any of them make the drivers in Ubuntu the same as in Kubuntu?

---

### Post by PuleX on 2005-11-05
Did you see that there's a whole page on the wiki listing printer models that other users have gotten to work under Linux? 
It's quite useful: 

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

---

### Post by Xian on 2005-11-05
[QUOTE=canadianwriterman]Would any of them make the drivers in Ubuntu the same as in Kubuntu?[/QUOTE]
The same drivers make your printer work in both Kubuntu & Ubuntu. You just need to configure it for the Gnome environment. So, are you saying then that when you goto System > Administration > Printing and begin a new printer session that your own hardware is not recognized? Or is it somehow not possible to complete the configuration?

---

### Post by trigg on 2005-11-05
[QUOTE=canadianwriterman]Oh dear. Okay, thanks. Just to retouch my original question. I understand that KDE utilities are used in Kubuntu and not in Ubuntu. However, the end result of setting up my printer in Kubuntu is that it works, but not in Ubuntu. I notice that there are lots of CUPS and Foomatic files in the repositories. Would any of them make the drivers in Ubuntu the same as in Kubuntu?[/QUOTE]


You can re-enable the root account (in order to configure CUPS from a browser) by typing this from a command line

```
 
sudo passwd root

```


then if you want to disable the root account again - type this

```

sudo passwd -l root

```

---

### Post by canadianwriterman on 2005-11-06
[QUOTE=Xian]The same drivers make your printer work in both Kubuntu & Ubuntu. You just need to configure it for the Gnome environment. So, are you saying then that when you goto System > Administration > Printing and begin a new printer session that your own hardware is not recognized? Or is it somehow not possible to complete the configuration?[/QUOTE]

Here's the situation:

[LIST]
[*]My Canon S300 is recognized by both Ubuntu and Kubuntu.
[*]However, there is no driver for the S300 in either Ubuntu or Kubuntu.
[*]The linuxprinting.org Web site recommends using the driver for the BJC8200.
[*]In Ubuntu, the BJC8200 driver works only for the black ink.
[*]In Kubuntu, the there are more drivers to choose from for the BJC8200 and one of them works perfectly for both black and colour ink.
[/LIST]
Also someone in this series of postings recommended [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters). The Canon S300 is listed and the recommendation is the S800 driver, but it renders the same black only, poor colour output.

So, I guess what I'm looking for is some way that Ubuntu can use the same driver options as Kubuntu.

---

### Post by Xian on 2005-11-06
[QUOTE=canadianwriterman]In Kubuntu, the there are more drivers to choose from for the BJC8200 and one of them works perfectly for both black and colour ink.[/QUOTE]
Which driver is it in Kubuntu that works?

---

### Post by canadianwriterman on 2005-11-06
[QUOTE=Xian]Which driver is it in Kubuntu that works?[/QUOTE]

Okay, I've narrowed down my problem. It's not that Kubuntu is different. When I set up the printer in K and printed a test page from the printer setup utility, it printed perfectly.

In Ubuntu, it's the same driver. This time, I went into Ubuntu's printer utility and printed a test page (which I hadn't done before) and it also prints perfectly.

Sooooo... the driver is fine in Ubuntu.

The real problem is that, when I print from any program, say from Firefox, black prints great, but the colour is very washed out. So, I'm wondering why there is a difference between printing a test page from the printer setup and printing from a program? Is there any setting I need to change?

Thanks, everyone.

---

### Post by kingcharles1666 on 2005-11-16
[QUOTE=trigg]You can re-enable the root account (in order to configure CUPS from a browser) by typing this from a command line

```
 
sudo passwd root

```


then if you want to disable the root account again - type this

```

sudo passwd -l root

```[/QUOTE]
Tried the CUPS browser tool with the root pass but still no joy

---

