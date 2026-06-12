---
title: "Epson AcuLaser CX16 (AL-CX16) doesn't print"
date: 2011-05-06
forum: Hardware
---

### Post by Finlandia on 2011-05-06
Hi;

I have Ubuntu 11.04.

I bought Epson AcuLaser CX16. Ubuntu recognized it but doesn't have a printer driver for it. Also via Epson/Avasys website I found only a CX11 driver. I'm tried to install the CX11 driver and some other Epson drivers + a Generic PCL driver. With all of them I will get the same result:

- Driver sends test pages and other files to printer.
- They appears to printer queue.
- After a short time files disappears from the queue.
- But: the printer will not print. It doesn't do anything.

I'm sure that all cables are connected and power is on.
My previous printer (Canon Pixma MP520) worked fine.

I have CUPS installed.

By localhost:631/admin -> Error log I can find the following error messages:

- Returning IPP client-error-not-possible for CUPS-Add-Modify-Printer (ipp://localhost/printers/Epson-AL-CX16) from localhost
- Returning IPP client-error-not-possible for CUPS-Add-Modify-Printer (ipp://localhost/printers/AL-CX11) from localhost
- Returning IPP client-error-document-format-not-supported for Send-Document (ipp://localhost:631/printers/EPSON_AL-CX16) from localhost
- [CGI] Unable to scan "@LOCAL"![FONT=Verdana]

[/FONT]Any ideas; what's wrong?
Or can I found the right CX16 driver or a good replacement from any website?

Thanks forehand!

- Finlandia.

---

### Post by Finlandia on 2011-05-21
Hi again;

I got the following answer from Avasys Corporation Customer Care:

---[COLOR=Navy][I][B]
Unfortunately, Epson Aculaser CX16 does not support the printing function 
on Linux. The scanning function is not supportted on Linux, too.
Sorry we couldn't be of any further help.[/B][/I][/COLOR]
---

So:

1) - Can I install Windows drivers to Linux with Wine? Works it or is it unstable/impossible?

2) - Is it likely that the Linux printer function (mentioned on the Avasys answer) will be improved so the CX16 could work (for example, with Generic driver) although the Avasys gave up?


-Finlandia.

---

### Post by wandalalakers on 2011-05-21
[http://linuxhcl.com/](http://linuxhcl.com/)

---

### Post by Finlandia on 2011-10-17
Will an upgrade to Ubuntu 11.10 solve my problem?


-Finlandia

---

### Post by Finlandia on 2011-12-20
Hi again everybody!

Can I install Windows drivers with Wine?
Works it? Will it make my system unstable?

Thanks,


Finlandia

---

### Post by sabax on 2012-03-05
Hi, for printer al-cx16 and aculaser c1600 Epson you can use konica minolta driver -> Magicolor 1600w 
It's already in ubuntu.

---------------


Ciao, per la stamopante epson aculaser AL-CX16 puoi usare il driver già incluso in ubuntu della Konica Minolta -> Magicolor 1600w.

---

### Post by pacolinus on 2012-03-26
> **sabax said:**
> Hi, for printer al-cx16 and aculaser c1600 Epson you can use konica minolta driver -> Magicolor 1600w 
It's already in ubuntu.

---------------


Ciao, per la stamopante epson aculaser AL-CX16 puoi usare il driver già incluso in ubuntu della Konica Minolta -> Magicolor 1600w.

Hi all,
2 days ago i bought a Epson Aculaser c1700...does anyone know where I can find its drivers?
in the mean time I'll have a try with Komica Minolta...

thank you

---

### Post by TurinTuramba on 2012-04-12
> **sabax said:**
> Hi, for printer al-cx16 and aculaser c1600 Epson you can use konica minolta driver -> Magicolor 1600w 
It's already in ubuntu.

---------------


Ciao, per la stamopante epson aculaser AL-CX16 puoi usare il driver già incluso in ubuntu della Konica Minolta -> Magicolor 1600w.

Hi sabax,

thanks a lot, for this hint. I can confirm it works with the Konica Minolta Magicolor1600w driver in IPP mode.

And again 3 hours of wasted life time ;-(

---

### Post by Finlandia on 2012-04-22
Yes,

CX16 works with Konica Minolta Magicolor 1600w drivers.
Thanks!

In my case, it was required to make changes by [http://localhost:631](http://localhost:631) address. Ubuntu 11.10 & Gnome gui didn't found the correct drivers. (I don't know why.)


-Finlandia.

---

### Post by frank cox on 2012-08-25
Hi:

 If I purchase a Konica Minolta magicolor 1600W which versions of Ubuntu will find the driver automatically? It seems to be a good deal.
Thanks












> **sabax said:**
> Hi, for printer al-cx16 and aculaser c1600 Epson you can use konica minolta driver -> Magicolor 1600w 
It's already in ubuntu.

---------------


Ciao, per la stamopante epson aculaser AL-CX16 puoi usare il driver già incluso in ubuntu della Konica Minolta -> Magicolor 1600w.

---

### Post by sabax on 2012-11-08
The epson printer is not a  Konika-MInolta, so it cannot be recognized automatically.

You must to manually choose the driver...

It's better than nothing :P

---

### Post by Finlandia on 2012-11-16
Hi again, folks!

I changed to a new laptop with Ubuntu 12.10. The driver with my Epson is:

KONICA MINOLTA magicolor 1600W Foomatic/foo2lava (recommended)

But now the printer prints only B/W pictures every time. The only expection is if I will print the test page from the Ubuntu Settings. The test page is always colorful. I was tried to change many options from print properties, such as Printing Quality, Color Mode, Halftone Algorithm, ICM Color Profile and so on, but my own prints are only B/W in any case.

Why the test page is printed in color every time?
Why the all other pages are B/W every time?

Thanks for your suggestions and solutions!

-Finlandia.

---

