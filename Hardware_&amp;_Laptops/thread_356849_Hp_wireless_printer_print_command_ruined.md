---
title: "Hp wireless printer print command ruined"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by gozzerd on 2007-02-08
Now you did it. Now I'm mad. Someone wrote a script or something that is changing my print command from what worked to something totally bogus. 

I have an HP photosmart c6180 all-in-one. I bought it specifically to have something compatible with Ubuntu and get an all-in-one with scanning and faxing.  I bought a wireless router because my wired router died. It is a  USR 5461A MaxG wireless with usb print server. It is running some embedded linux for its firewall and firmware. And it is open source. I am not using the usb port. My printer is networked wirelessly.

But my HP was recognized nicely by the system, was set up easily. I used the hplip site's Ubuntu directions for installing their current package. The Ubuntu repository package was too old and wouldn't work.

So the configuration that worked was choose HP JetDirect as the connection type and specify

socket://192.168.2.2

as the address. The port was unnecessary, as everyone found each other and they were all happy, but 9100 seemed to work if specified,  and scanned as being open. 

By the way, it was really cool the way Cups browser based management, Gnome printer management, and the hp-toolbox management all talked together nicely. That was brilliant. I could set stuff in one, and the others would check and find the changes too. Nice.

But today, I am waiting for my Jennifer to finally successfully print a document on the new printer after setting everything up for her on Ubuntu, and I find that the configuration has changed to 

CUPS printer (ipp)

ipp://hp:/net/Photosmart_C6100_series?ip=192.168.2.2

This would have been fine if it worked. But it doesn't.

I checked my machine, and it was configured

hp:/net/Photosmart_C6100_series?ip=192.168.2.2

and printed one test page successfully, then it appended ipp:// to the beginning and wouldn't print any more either. Or let me change it. If I try to change the address to the socket form, or remove the ipp:// it adds them back. I can't reach my printer any more and the machine is writing its own print commands. And they  don't work. And she has an order confirmaton document that she wants printed sitting in the queue waiting to print. How do I reconfigure the printer and print the document? If I delete the printer and start over, the document is gone.

Who did this?

my machine is a dual p3 1ghz with 1 gig ram. via apollo motherboard, I think. old nvidia gforce2 mmx running with 3d acceleration enabled in the nvidia driver  using that script from the forum.  



Geoff

---

### Post by gozzerd on 2007-02-09
Oops.  Never mind. It is resolved now, and, as usual, the person who did it was me. I had let hplip install from the desktop on her machine. Today I trashed the hplip folder thinking it was just a left over archive, not needed any more. The documentation said it would install to /usr, but apparently hplip  still needs the extracted folder. For some bizarre reason,  gnome or cups or hplip  tried to make up for the lack of configuraton info, or lack of hpiod or whatever and adjusted the print command to a CUPS form by appending ipp. How my hpiod or something(?) was convinced to change the command on my machine too I have no idea. But after re-downloading the hplip installer from the hplip sourceforge site and running it on her machine, and deleting and re-installing the printer on my machine, all is well.

---

