---
title: "CUPS DNP DS-40 Printer finishing"
date: 2013-10-24
forum: Hardware
---

### Post by hxtWeXw on 2013-10-24
Dear Community,

first sorry if I have not the best english writing skills.

I fell in love with ubuntu sevrers for years, but now I have a problem which I can not solve myself.

I have installed a unbuntu LTS server with cups and installed a DNP DS-40 Photoprinter on it, with
the gutenprint driver the printer runs very well, excluding one very import function = finishing

The DS-40 can handle glossy finishing and matte finishing on the same paper.

I know from a MacBook with cups 1.7 that the parameter must be Finish=Matte (glossy is default)

I have set in both cups system the loglevel to debug. After a time I used a Ubuntu Desktop because
the Desktop has cups 1.7 too like the MacBook(fully works) I see in the log file on both Systems the same:

```
rastertodnp: Finish: Matte
argv[5]="document-name=TestImage Finish=Matte
```

On the MacBook it is working, but on the ubuntu system it will not make the photo matte.

I have no idea at the moment how it can be and how I can fix it.

I will be very glad for ideas or answers from the community, I don't want to install Windows Server to use it :)

Best regards and thank you,

Ben

---

### Post by aikishugyo on 2013-10-25
Hi, can you please post this on the gutenprint mailing list, where the developer is listening?
Lists:
[http://gimp-print.sourceforge.net/p_Mailing_Lists.php](http://gimp-print.sourceforge.net/p_Mailing_Lists.php)
Susbscribe and post to gimp-print-devel

Regards,
Gernot

---

