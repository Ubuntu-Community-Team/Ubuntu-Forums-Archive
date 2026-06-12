---
title: "Funky printer issue (bottom 3/4&quot; of every page cut off)"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by mr love and justice on 2006-11-07
I'm trying to use my Brother HL 2040 laser printer with Edgy, the manufacturer's LPR driver, and the manufacturer's CUPS wrapper. It appears that the printer doesn't start printing at the top margin, but begins about 3/4 of an inch too late. The result is that the bottom 3/4 of my page is cut off. Anybody know a fix for this besides adjusting the margins manually in openoffice? It seems like it would be an easy calibration adjustment but I don't know where to start.

Thanks,
MLaJ

---

### Post by mr love and justice on 2006-11-13
Just plugging this one as I still haven't fixed it. Maybe nobody has this printer?

---

### Post by tebbendj on 2006-12-13
I don't know if this will help, but I had a simular problem that seems to be fixed now.  First, I have a Brother 2070N printer and I installed the dirver from Brother.  My margins too were offset about 3/4 inch from the top.  I reinstalled the drivers--didn't help.  I looked at the printer settings in under System->Administration->Printing and then under the page setup for this printer.  It was set to letter size--as it should be.  Then I went to [http://localhost:631](http://localhost:631) and checked the page settings there.  It was set to A4, so Ubuntu was reporting one page size and CUPS itself was reporting another.  Once I fixed that problem it printed fine.  I hope this helps.

---

### Post by Quark Green on 2007-05-19
Dear tebbendj, I had a similar problem and your post helped me to solve it. Thank you. For the benefit of others, the problem was that Brother multifunction printer MFC-215C kept cutting off the top line of the page and printing the second line very high on the page. As if there was no top margin or very little. Hence also the bottom margin was much bigger than the setting. The following 3 places have to have the same setting:
(1) System->Administration->Printing->Printer Properties->Paper->Paper size.
(2) System->Administration->Printing->Printer Properties->Advanced->PageRegion
(3) [http://localhost:631](http://localhost:631) -> Manage Printers->Set Printer Options->Media Size.
In my case, 1 was 'A4' and 2 and 3 were 'letter'. The problem was fixed when I set them all to 'A4'.

---

### Post by bean77 on 2007-07-05
I have this issue too and did everything in the above post.  All three were set to the same.  How else can I fix this?

---

### Post by AustinSchuh on 2007-10-02
I was having the same problem as described here, and I managed to fix it by fixing the paper size.  I run Debian, but what I did should work almost exactly the same.

I edited the /usr/local/Brother/inf/brHL2070Nrc file and edited the 7th line.  I changed it from
```
PaperType=A4
```
to
```
PaperType=Letter
```
and now the printer prints my paper in the correct spot on the page.

---

### Post by Vardigon on 2008-06-17
Hi guys.

I'm using a Brother HL-5250DN printer, and I had the same problem, although I use Gentoo.  Thanks for the remedy.  Someone should note this somewhere as it seems to be a prevalent issue >.>.

Edit: And I'm back again.  I tried changing the settings in all the different menus (in XFCE) when I wanted to use Duplex on my printer, and I found that changing settings in any of the menus did NOT work.  I had to change the setting in /usr/local/Brother/inf/brHL5250DNrc to:

```

Duplex=DuplexTumble

```

When I did this, Duplex worked :).

---

### Post by zenerian on 2008-06-18
Hi
Similar problem but I´ve got a Brother MFC425CN running the MFC210C driver on a network and I also had the top of my page being chopped off and a big margin at the bottom.
I was trying to print A4 paper size and it looked like it was printing on a Letter size.
I had changed all the printer settings in Administration Printing and also in CUPS but it didn´t make any difference to the output.
Thanks to the posts above it gave me the right lead. I think because I´m running a network printer I had to change the files in /usr/Brother/inf/brMFC210Cfunc (for my driver) and also /usr/Brother/inf/brMFC210Crc .
I changed any reference to Letter to A4 and it fixed my problem.
I don´t know if I needed to change both but I did anyway.
BTW I needed to edit the files as superuser by using terminal and 
sudo gedit     then opening the 2 files, changing them, and saving them again
I´m running Hardy 8.04
Thanks to the posters above for heading me in the right direction
Still bumbling along but you sure get a great sense of achievement when you finally figure out even the smallest problems
I think Linux is great :biggrin:

---

