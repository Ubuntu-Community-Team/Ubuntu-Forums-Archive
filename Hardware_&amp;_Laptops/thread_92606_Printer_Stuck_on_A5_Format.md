---
title: "Printer Stuck on A5 Format"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by Funktown on 2005-11-20
I've got a Canon i950 printer that I've got all hooked up, detected, and ready to roll. I got the drivers for it from a HowTo posted a while ago (linked to a japanese ftp site). This printer has worked on Hoary before, as I had it set up before I hopped to Gentoo. Missing the Ubuntu goodness, I hopped back after about a week. I set up my system to how I had it-- staying in Gnome instead of KDE this time, and was ready to churn out those oh-so-fun reports my professors make me do.

After a 22 hour essay-writing period, I'm finally ready to print the mass of tangled words. There's only one problem.. they all print in A5 size. Gnome-cups-manager tells me that my default printer is set to "Letter" paper size and paper region.. but OpenOffice.org (1) won't get off of A5. If I edit "Printer Properties" in OO, putting the paper size to "Letter", it sets back to A5 once I close the dialogue. This is very, very frustrating.

Any ideas how to get OpenOffice to accept my "Letter" paper-size request and print correctly? I've tried printing from other wordprocessors (Abiword, OO2).. but they ask me to use command "lpr", which doesnt seem to work. Maybe setting that up would be easier? Anything?

---

### Post by guhpraset on 2008-05-08
change it from /etc/papersize
go to terminal
sudo gedit /etc/papersize

and change it to whatever you like

---

