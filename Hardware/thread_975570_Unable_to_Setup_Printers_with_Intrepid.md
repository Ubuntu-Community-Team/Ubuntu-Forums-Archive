---
title: "Unable to Setup Printers with Intrepid"
date: 2008-11-08
forum: Hardware
---

### Post by Anlace on 2008-11-08
Greetings,

I am having significant challenges setting up a networked printing in Kubuntu 8.10.

Here is the setup:

Dual-boot desktop computer with Epson R220 and HP Photosmart C4470 printers attached and working via USB.  Both printers work great in XP Pro and in Kubuntu 8.04 64 bit.

A second desktop computer and a Toshiba laptop running XP Home can print to both printers when the other desktop computer is booted into either Kubuntu 8.04 or XP Pro.

A HP Laptop (Inspiron 9400 series) that dual-boots Vista Business and Kubuntu 8.10.  Vista can print to both printers when the other computer is running either Kubuntu 8.04 or XP Pro.

The problem is I have not been able setup printing with Kubuntu 8.10.  It simply does not "see" the printers at all, neither one of them.  I have tried everything I could find including manual setup using the CUPS interface using both IPP:// and SOCKET:// addresses in as many configurations as was suggested.

The printer utility provided by KDE 4.1 wasn't able to discover the printers either (obviously).

So what is it about Kubuntu/KDE 8.1 that is preventing me from finding networked printers?  I can access all of the shared folders on the other computers via Samba.  I feel like it's probably something obvious and I am just not seeing it.

As always any help with this is very much appreciated!

Peace,
Gail

---

### Post by Anlace on 2008-11-08
Ok, so this step apparently wasn't needed in any other printer setup that I've had to date.  The thing that I was missing was to go to KDE menu > System > Printing and enable "Share published printers connected to this system."  I also enabled "Allow printing from the internet."

Go figure, I knew it was something in front of my face.  I hope this info helps someone else along the way.

Peace,
Gail

---

