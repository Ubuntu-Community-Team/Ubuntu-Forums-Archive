---
title: "Printer driver for Canon Pixma MP280"
date: 2011-08-16
forum: Hardware
---

### Post by Lhypha on 2011-08-16
My computer is not recognising the printer. I need to know where to find a printer driver to install on Ubuntu for my Cannon Pixma MP280.

---

### Post by jerrrys on 2011-08-16
is this what your looking for?

[http://software.canon-europe.com/software/0040266.asp?model=](http://software.canon-europe.com/software/0040266.asp?model=)

---

### Post by PapaGary on 2011-08-16
Or, you can try this:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

Whoops, they don't list a MP280 so maybe not.

---

### Post by demonipuch on 2011-08-16
Hello

This [ppa](https://launchpad.net/~michael-gruz/+archive/canon) provides many Canon PIXMA drivers. Here is how to install your printer :

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-mp280series
```

---

### Post by corncob on 2011-08-16
[http://support-nz.canon.co.nz/contents/NZ/EN/0100301402.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100301402.html)

---

### Post by PaddyIndigo on 2011-08-19
I'm having the same problem with a Canon Pixma MP282,  which seems to use the same MP280 series driver. Can we share ideas?  [click here ]("http://ubuntuforums.org/showthread.php?p=11166301#post11166301")to see what I've tried.

Regards
Pat

---

### Post by Lhypha on 2011-10-11
> **jerrrys said:**
> is this what your looking for?

[http://software.canon-europe.com/software/0040266.asp?model=](http://software.canon-europe.com/software/0040266.asp?model=)
Thanks Jerry I haven't been back to this site since I posted my request thanks for your reply, I will give it a try.

---

### Post by Lhypha on 2011-10-11
> **PaddyIndigo said:**
> I'm having the same problem with a Canon Pixma MP282,  which seems to use the same MP280 series driver. Can we share ideas?  [click here ]("http://ubuntuforums.org/showthread.php?p=11166301#post11166301")to see what I've tried.

Regards
Pat
Will let you know, if you haven't already solved it already. I have not been back to this site since August. I have not tried anything yet!! Having to print from the other MS OS at the mo.

---

### Post by digitaljeannie on 2011-10-11
I have a Pixma MX360 and downloaded the print drivers and scanner drivers from Cannon's Europe site and both functions work perfectly. Was able to set up, print and scan so I can verify that, at least for my model, the drivers off that site work perfectly.

You first have to install the "common" drivers and then the model-specific driver.

---

### Post by ezramorris on 2011-10-11
I don't know if this helps anyone, but I have an MP220. When I plug it in, Ubuntu doesn't find a driver for it, but when I go to Printing, and manually add it as a new printer, the driver is there.

---

