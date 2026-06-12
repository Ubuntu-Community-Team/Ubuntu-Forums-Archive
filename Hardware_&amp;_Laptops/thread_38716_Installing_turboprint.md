---
title: "Installing turboprint"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by veelivar on 2005-06-01
Hello,

I'm very new to linux in general esp ubuntu so I hope this dosn't sound like a stupid question.

I've pretty much come to realise that the only chance of getting my printer (Canon PIXMA iP1500) working is to use turboprint.  So I'm trying to install it and missing something along the way.

What I have done is

put the extracted file from turboprint.de in /opt
cd into it and ran sudo ./setup
told it to use english
typed y(es) to install

it's now complaining that i don't have gtk, gdk, gmodule (twice)
I tried looking for them on synaptic and couldn't find them :(

Any ideas what I'm missing (I'm sure it is obvious).  I know that your probably thinking I should just go an buy a new printer. But I only got this one a few weeks ago as i needed a printer imediatly, so walked into PC world and bought one that wasn't epson (my old one wouldn't print b&w if the colour cartridge was out!! and they are very expensive).  This was before I decided to install linux or even knew about unbuntu,  I did assume that printers would just work though!  

hmm sorry about my rant :)

Could any one help please?

Cheers,
Dan.

---

### Post by DJ_Max on 2005-06-01
Howdy,
If your using Gnome, then you already have gtk, gdk already. You can search for them in synaptic. You just need the development files. Which would be: libgtk2.0-dev and gdk-imlib1-dev. As for gmodule, I can fine that, and not sure what it is.

---

### Post by veelivar on 2005-06-02
Thanks for the help.

I used synaptic to get them then ran the installation again and this time i got a gui installer.

I now have another problem :( which i think may be a bit more general.

Once a print job has finished it is not removed from the print queue.  So nothing will print unless I manually go and cancel it.  

The printer also seems very slow to respond as well, it takes a while for it to decide to actually print even when there is nothing in the queue.

Any ideas?

Thanks in advance,
Dan.

---

### Post by DJ_Max on 2005-06-02
I'm not familar with the printer you have, hows it connected to your PC?

---

### Post by veelivar on 2005-06-02
USB /usb/lp0 (i think, I could be wrong though).  It does actually print it's just that once the file has finished printing it stays in the queue saying that it's still printing, thus not letting anything else print.

regards,
Dan.

---

