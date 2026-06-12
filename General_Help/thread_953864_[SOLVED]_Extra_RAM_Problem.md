---
title: "[SOLVED] Extra RAM Problem"
date: 2008-10-20
forum: General Help
---

### Post by skathrein on 2008-10-20
I am running Ubuntu Server (8.04) with two 1 GB sticks of RAM for a total of 2GB. Does anyone have a guess as to why it takes 30-40 minutes to load (literally) with 2GB of RAM, but if I pull one stick out leaving only 1GB, it loads within minutes? I have also tried each stick in each slot and everything is fine as long as I don't have both in at the same time.  Therefore, it seems both the RAM and slots are working fine, it's just a problem when I have both in.  Thanks for your help.

---

### Post by DGortze380 on 2008-10-20
> **skathrein said:**
> I am running Ubuntu Server (8.04) with two 1 GB sticks of RAM for a total of 2GB. Does anyone have a guess as to why it takes 30-40 minutes to load (literally) with 2GB of RAM, but if I pull one stick out leaving only 1GB, it loads within minutes? I have also tried each stick in each slot and everything is fine as long as I don't have both in at the same time.  Therefore, it seems both the RAM and slots are working fine, it's just a problem when I have both in.  Thanks for your help.

Run a memtest off the live cd. Sounds like a bad stick of RAM.
Are you using more RAM than the board supports? Just because you have two slots doesn't mean the board supports 2GBs. Whats the model number on your board and RAM?

---

### Post by Hangwire on 2008-10-20
> **DGortze380 said:**
> Run a memtest off the live cd. Sounds like a bad stick of RAM.
Are you using more RAM than the board supports? Just because you have two slots doesn't mean the board supports 2GBs. Whats the model number on your board and RAM?

Indeed, I agree. I vote for a bad memory stick, my board that is from 2004 supports 2GB.

---

### Post by CorvisRex on 2008-10-20
both sticks work fine if they are by themselves?  If so, sounds like a ram/mother board problem  I would run mem test on is all the same.  But can your mother board handle 2gb ram?  Don't know your setup.  

As far a bad ram sticks are concerned though, I only had it happen once  Ubuntu/linux in general, loaded fine, but suffered intermittent problems. (actually it was the only time I have ever had linux crash on me)but it loaded fine.

---

### Post by skathrein on 2008-10-20
I was thinking that the RAM is ok since each by itself is fine, but I will try running a memtest.  The motherboard is a PC Chips P23G and the memory is two 1GB DDR2 533.  2GB should work from what I've read.  Thanks again for the help.

---

### Post by DGortze380 on 2008-10-20
> **skathrein said:**
> I was thinking that the RAM is ok since each by itself is fine, but I will try running a memtest.  The motherboard is a PC Chips P23G and the memory is two 1GB DDR2 533.  2GB should work from what I've read.  Thanks again for the help.

Are the RAM DIMMs matching? Same model, size, timings, etc.? The board should support the amount of RAM assuming all the other specs are supported. RAM can be tricky to diagnose though, let us know the results of the memtest. Remember to run it for a few cycles, not just one.

---

### Post by skathrein on 2008-10-21
Thank you to everyone for the help.  Turns the memory was ok, it was the bios. After I updated the BIOS, everything went smoothly.  So while it is probably unlikely anyone else will have this problem, here is what I did just in case.

For a PC Chips P23G (v.3.0) motherboard (not reading 2GB of memory):
1. You can download the most current BIOS [here]("http://www.pcchips.com.tw/PCCWebSite/Downloads/ProductsDetail_Download.aspx?detailid=387&DetailName=Bios&DetailDesc=&CategoryID=1&MenuID=6&LanID=2").  If that page changes or doesn't work in the future, just google PC Chips and then search their site for P23G.  
2. You can only flash the new bios with DOS.  So download the Windows 98 boot CD image from allbootdisks.com ([here's the link]("http://allbootdisks.com/download/iso.html") to the Win98 CD page).  
3. You now have to add the unzipped bios files to the Win98 ISO.  You can do this with ISO Master (in the repositories).  If anyone wants the one I used, just email me.
4. You have to then boot the Win98 disk and tell it to start using help from the CD.  Once it takes you to a prompt, type "D:" to switch over to the disk.  If your bios files are in a directory, switch to that.  Mine are just with all of the other files on the CD.  To flash the bios, type
```
AFUDOS 070528.ROM /p /b /n /c /x
```
5. You will have to go into bios setup and change what you want and save it.  If you have any problems, try holding pageup while booting after you have installed the new bios.

That's what worked for me.  Thanks again!

---

