---
title: "Ubuntu not sending print jobs to canon pixma G660"
date: 2023-07-25
forum: Hardware
---

### Post by blort on 2023-07-25
I'm running Ubuntu 22.04.

I have a Canon G660 megatank. 
If I send print jobs to it from a desktop mac then the printer accepts the jobs and prints without problems.

Earlier today I started sending print jobs to the pixma from Ubuntu. After three documents were printed, the printer stopped responding. In ubuntu settings->printer I could see that jobs were pending.
But no information was presented anywhere on why the jobs would not print. 
No errors, no warnings.

After troubleshooting with canon support first told me that poor wifi signal might be an issue. So I ran out and bought a cable.
After connecting with the cable, ubuntu 'settings'->'printer' shows two printers. But sending jobs to either of them from any any application (inkscape, browser, libreoffice) results in "pending" tasks that will not print.

I did a purge and reinstall of cups.
After a reboot, setting could still see two printers. Both of them would still accept print jobs. The print jobs would sit as "pending" and they would not actually print.

I removed the printers from settings ('settings'->'printers'-> cog icon -> 'remove printer').
One would dissapear upon removal. The other would remain.

From the cups web interface I can see the following:

[IMG]https://i.imgur.com/pa4uOu4.png[/IMG]

How many of my neighbours and in which order do I need to sacrifice in order to get ubuntu to resume printing?

---

### Post by gezzer2 on 2023-07-26
not sure if this will help but its the Linux drivers for your printer it cant hurt to give them a try ...

[https://www.canon.com.au/printers/pixma-g660-megatank/support](https://www.canon.com.au/printers/pixma-g660-megatank/support)

---

### Post by brian_p on 2023-08-01
Installing the Canon drivers should be completely unnecessary. A weak wireless signal is unlikely to be a cause of your issue. Give outputs for
```
avahi-browse -rt _ipp._tcp
```
```
ls -l /usr/lib/cups/filter/rastertopwg
```

---

