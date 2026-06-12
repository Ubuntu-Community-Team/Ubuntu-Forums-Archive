---
title: "Error with printer"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by ggastelum on 2006-07-10
Hello,

I am relatively new to Linux so maybe this has a simple solution. I have just added a network printer to my Dapper Drake install. It is a cannon 3300. Everytime I print a test page the printer errors out with the error that A4 paper is expected in the printer instead of letter size paper. I press a button on the printer that resets the printer and the test page is printed. Through the printer setting from administration on my laptop I change the paper size to letter but I still get the same error from the printer. When I look at the printer settings again I see the paper for the printer is set to letter. Then I checked the printer settings from the CUPS website on my laptop ([http://localhost:631](http://localhost:631)) and I see the settings for the printer still has the A4 paper default settings. So I change the settings and click on Set Printer Options but I was asked for a username and password. I put in my username and password (I do have sudo permissions) but was denied. I activated the root password and tried root and the password but was still denied. What do I need to do to get the paper settings to change?

Thanks for any help,
George

---

### Post by julioromano on 2006-07-11
Same problem here, thus I'd like to set A4 (gnome-cups shows A4) and CUPS is still set to "Letter".

Having an HP Color LaserJet 2600n

Bye
Marco

---

### Post by KernelKen on 2006-09-27
I am new to Ubuntu myself.  But I am currently setting up this printer and had the same problem.

Go to:

System 
Administration
Printing

Then right click your printer and choose properties.

This will allow you to change your printer settings.  Choose paper tab to change to letter size.

This is a good website for information [http://localhost:631/](http://localhost:631/) but it is easier to change your settings using your PC.

---

### Post by hikaricore on 2006-09-28
From my experience changing paper size from the Printers config often does no good.  Personally I can't seem to access the cups server on port 631, viewable yes....modifyable.... no.  :/

The cups server is showing A4 when the Printers config window is showing 11x17... *slaps forhead*

---

### Post by bristleburger on 2006-09-29
The use of localhost:631 to configure cups has been disabled on ubuntu (for security reasons I believe).

You should be able to set A4 paper via System->Administration->Printing - right click to edit printer properties. Applications such as eye of gnome will then use A4 paper size automatically. But firefox seems to have it's own set of printer defaults so you will also need to set A4 using the properties button in the firefox print dialogue.

If you use Gimp you will need to configure this separately as well. Gimp doesn't have a driver for my printer so I used Adode PS2 which seems to work.

---

### Post by hikaricore on 2006-09-29
No matter where I change the paper size it comes out wrong.  Sorry to be complicated but that's the way it's working out for me.

---

### Post by mitch.c on 2006-09-29
> **hikaricore said:**
> No matter where I change the paper size it comes out wrong.  Sorry to be complicated but that's the way it's working out for me.

What happens if you:
```
lpoptions -p printername -o PageSize=Letter #replace printername accordingly
```

---

### Post by hikaricore on 2006-10-03
> **mitch.c said:**
> What happens if you:
```
lpoptions -p printername -o PageSize=Letter #replace printername accordingly
```

i'll try this when i get to work in the morning :)  and let you know how it turns out.

---

### Post by hikaricore on 2006-10-04
Well it works.... but once again this only changes what is shown and not the document size that is actually sent to my printer.  I've tried this in both Raw and PS formats and still no dice.  Everytime it registers at letter and I have to change it manually on the print server.

---

