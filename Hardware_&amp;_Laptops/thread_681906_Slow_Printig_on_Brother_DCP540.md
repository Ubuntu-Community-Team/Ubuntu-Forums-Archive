---
title: "Slow Printig on Brother DCP540"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by SimSys on 2008-01-29
Hi all,

I bought a Brother DCP540CN Printer and installed it with Brother drivers like described in different HowTos. Now I can scan and print as expected... BUT the printer prints very very slow. That's not quite correct: he prints some lines fast and then I hear a curious noise and when looking inside the printer I see a LED scanning the paper. I guess that the printer evaluate which paper is in. He looks, prints, looks again, prints, looks... and  hence printing is very slow.

Additional remark: When I try to do change the general printer settings (KDE) I get errors like (sorry it's german):
- "Laden eines passenden Treibers für Drucker DCP540CN ist nicht möglich. Fehlermeldung des Verwaltungsprogramms: /tmp/479ca1d30801e(Zeile 1): syntax error, unexpected OPTION" or 
- "Laden eines passenden Treibers für Drucker DCP540CN ist nicht möglich. Fehlermeldung des Verwaltungsprogramms: /tmp/479ca1fd0d687(Zeile 1): syntax error, unexpected '/'" or sometimes
- "Laden eines passenden Treibers für Drucker DCP540CN ist nicht möglich. Fehlermeldung des Verwaltungsprogramms: /tmp/479ca237a02cb(Zeile 1): syntax error, unexpected QUOTED" 

All KDE-applications, Openoffice or Firefox can change settings and print. I use Kubuntu 7.10 on my box. With windows OS, the printer is as fast as I expect.

Thank you for Your assistance

SimSys

---

### Post by oldsoundguy on 2008-01-29
try experimenting with different cups drivers.  I have one printer on one machine that is really slow, but if I access the printer via my network with a Windows machine, it flies.  So it HAS to be the driver.  I Experimented and found the fastest of about 1/2 dozen options for the printer .. it is faster than the default driver, but still slower than it should be. 
Cups is constantly updating drivers in your updates, so sometimes it pays to go looking again.

---

### Post by SimSys on 2008-01-31
1) The driver was downloaded from the Brother's Linux homepage ([Brothers Linux Hompage]("http://solutions.brother.com/linux/en_us/index.html")). As I understand what happens, no cups driver is involved.

2) I see not alternative to the used driver. This driver is specific to the printer I have.

Thanks for Your endurance.

regards
Simsys

---

### Post by S.Tokarev on 2008-02-07
I'm using HP3030 via D-link DP-301P+ external print server.
Windows prints fast but Ubuntu CUPS is lagging extremely.
Printserver shows good performance getting the data from client but it pushes it into printer very slow.
Spooling bytes counter grow fast but printing bytes counter goes up by 32000 every 2-3 seconds.
May be there are some escape codes that make printer print fater.
Again Windows print very fast.

---

