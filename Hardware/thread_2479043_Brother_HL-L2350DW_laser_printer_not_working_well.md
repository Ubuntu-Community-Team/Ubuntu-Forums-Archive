---
title: "Brother HL-L2350DW laser printer not working well"
date: 2022-09-13
forum: Hardware
---

### Post by Keith_Beef on 2022-09-13
Hello, all; it's been a long time since I last posted.

I recently bought a Brother HL-L2350DW laser printer (to replace an HP OfficeJet 7612 whose print head failed).

Yesterday, the Brother printer seemed easy to set up, connected to WiFi, printed the test page with no problem. This morning, I have a 16 page document to print and it is not working properly.

I'm using Ubuntu 20.04. Below, the info from CUPS.

Description:	Brother HL-L2350DW
Location:	Attic
Driver:	Brother HL-L2350DW series, driverless, cups-filters 1.27.4 (grayscale, 2-sided printing)
Connection:	ipp://Brother%20HL-L2350DW%20series._ipp._tcp.local/
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=two-sided-long-edge

When I print from a .odt file or from the .pdf generated from that file, all I get is a series of blank pages...

While the blankl pages are coming out, I see this in CUPS:
Brother_HL_L2350DW_series-26  	Unknown  	Withheld  	1k  	21  	processing since
Tue Sep 13 07:49:10 2022 
"Waiting for job to complete."

And in the command line:
```
# lpq -a
Rank    Owner   Job     File(s)                         Total Size
active  unknown 26      unknown                         1024 bytes

# lpstat -a
Brother_HL_L2350DW_series accepting requests since Tue 13 Sep 2022 07:49:10 CEST
```

I tried following instructions [here]("https://forums.linuxmint.com/viewtopic.php?f=51&t=322183") to fix the problem; no joy.

Deleting the printer didn't work; it was connected by WiFi and seemd to be reconnected automagically (because th eprinter broadcast its existence?), so I disabled WiFi on the printer, and connected using a USB cable. This automagically created two printers.

```
# lpstat -a
Brother_HL_L2350DW_series accepting requests since Tue 13 Sep 2022 08:11:48 CEST
HL_L2350DW_series accepting requests since Tue 13 Sep 2022 08:11:36 CEST
```

I could print a test page on HL_L2350DW_series but trying to print that 16 page .odt document gets the following message:

```
HL_L2350DW_series-31  	Unknown  	Withheld  	119k  	16  	pending since
Tue Sep 13 08:18:42 2022 
"No destination host name supplied by cups-browsed for printer "HL_L2350DW_series", is cups-browsed running?"
```

And yes, cups-browsed is running.

```
# ps -edf | grep "cups-browse"
root       87190       1  0 08:02 ?        00:00:00 /usr/sbin/cups-browsed
```


Any ideas?

---

