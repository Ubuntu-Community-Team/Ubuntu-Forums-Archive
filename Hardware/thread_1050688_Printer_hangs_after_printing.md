---
title: "Printer hangs after printing"
date: 2009-01-25
forum: Hardware
---

### Post by Trekrider58 on 2009-01-25
I'm now running Intrepid but was running Hardy until two days ago. Same problem with both.

I have an HP 2200 Business Inkjet, when I print anything it prints fine but after wards the printer hangs with 'Printing' displayed on its LCD panel. When it is in this state I can't print anything else either from my PC or any of the other networked PCs. If I cycle the power on the printer I can then print again as normal.

Anyone know what I can do to resolve this problem?

Thanks,

---

### Post by moorsey on 2009-01-28
just been searching the forums and found this.  I have exactly the same issue with my 2200 printer.  I am running Vista also, which does not properly support this printer, so I have to print to pdf and then get my Ubuntu machine to print that.

Works fine for one job, but have to power cycle the printer to print the next job!

---

### Post by Trekrider58 on 2009-01-28
> **moorsey said:**
> I am running Vista also, which does not properly support this printer, so I have to print to pdf and then get my Ubuntu machine to print that.

Why do you say Vista doesn't properly support this printer? My daughters laptop runs Vista and prints with no problems. I had no issues setting that machine up at all. 

I have 4 machines on my home network (2 x XP Pro, 1 x Vista and 1 x Ubuntu). Only problem I have is with the printer hanging after printing from the Ubuntu machine.

---

### Post by moorsey on 2009-01-29
The vista driver is fine, but I have the extra paper tray for this printer and Vista apparently forgot about that.....

So I forced the XP driver on, this works OK apart from when printing anything other than text and images, layered things dont print etc

---

### Post by Trekrider58 on 2009-01-29
> **moorsey said:**
> The vista driver is fine, but I have the extra paper tray for this printer and Vista apparently forgot about that.....
That explains it - I don't have the additional paper tray.

Just need to sort out why it hangs after printing from a Ubuntu machine.

---

### Post by J1m on 2009-01-31
Hi,

On your windows machine - go to the shared printer properties, on to Ports and **UNTICK**"Enable bi-directional support".

I had the same problem with an HP 5610.

Hope that helps,

J1m

---

### Post by moorsey on 2009-02-09
> **J1m said:**
> Hi,

On your windows machine - go to the shared printer properties, on to Ports and **UNTICK**"Enable bi-directional support".

I had the same problem with an HP 5610.

Hope that helps,

J1m

eh?  This is a Ubuntu problem, not Windows

That bi-directional printer support does fix a lot of problems I have at work though.  Especially on HP printers, they just have zero Vista driver support!

Still no advice from anyone on the Ubuntu printing issue then?

---

### Post by divisiontree on 2011-04-17
That bi-directional support option fixed my problem.  Sharing an HP PSC 1210 on a Vista machine, and printing from an Ubuntu netbook.  Thanks!!!

---

