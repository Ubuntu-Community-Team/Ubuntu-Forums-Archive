---
title: "Epson CX11NF + Gutsy ?"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by MrEgg on 2007-10-25
Hi all,

Since I have upgraded to Gutsy, I can no longer print from my Epson AcuLaser CX11NF. Prior to upgrading to Gutsy, I had had to follow the instructions on [http://www.gedda.info/?p=132](http://www.gedda.info/?p=132) to install the driver properly, and after that everything was working just fine.

Since the upgrade, I can see that Gutsy is trying to communicate with the printer, as I have an icon giving me some printer warnings such as 'cartridge almost empty', but no printing job can get through (I have tried both printing a test page and printing directly from an application).

I did a fresh install of Gutsy on another computer, and here again, no printing.

I have also tried printing from the network and printing from the USB, and there as well, no printing.

Is there any way to solve this ? Is there any way to maybe revert back to Feisty as far as printing is concerned ?

[Edit 1]
I made different tests today regarding my printing problem, and here is the outcome :
- printing does work at the office (Dell 3100 and Brother 5060 printers)
- printing at home on the Epson CX11NF does work if I revert back to kernel 2.6.20.16 ; but it still doesn't if I use kernel 2.6.22.14

[EDIT 2]
I did solve the problem on the laptop, which is a Feisty install upgraded to Gutsy :

```
sudo aa-complain cupsd
```

[EDIT 3]
This command has also solved the problem in the fresh Gutsy install, but only after a reboot.


Regards,
Fred

---

### Post by Bdanger on 2008-05-02
It seems that website is no longer valid (the gedda.info one..) Do you know where else I can find these instructions?  I have the same pringer.

---

### Post by MrEgg on 2008-05-12
> **Bdanger said:**
> It seems that website is no longer valid (the gedda.info one..) Do you know where else I can find these instructions?  I have the same pringer.

This must have been a temporary problem only, as I just tried now and the site was online :)

---

### Post by ltkermit on 2008-06-09
Thanks for the info!  I could not get the Epson to print until I ran that command, now it works perfectly, thanks again!

> sudo aa-complain cupsd

Epson Acculaser CX11NF
Ubuntu 8.04

---

