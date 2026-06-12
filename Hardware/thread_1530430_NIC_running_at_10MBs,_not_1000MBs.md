---
title: "NIC running at 10MB/s, not 1000MB/s"
date: 2010-07-13
forum: Hardware
---

### Post by nixIT on 2010-07-13
Hello all,

I apologize if this is not eh right place for this, but I thought I would pick some of your technical brains.

I have a strange issue, not really Ubuntu related, but more related to my motherboard and onboard NIC.

I have the [ASUS M4A79XTD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131402") mobo, 2 hard drives, one formated with windows 7 64bit and the other Ubuntu 9.10, with the option to boot to either OS controlled via the bios.  Worked great when I set the system up back in November 2009.  

Two weeks ago I upgraded the bios to the latest version, the upgrade went fine, upon the first boot after the bios upgrade I booted to linux (my default boot order), and everything was fine, NIC running at 1000MB/s.  I booted to windows and I could not access my windows boot, I was prompted with the MS boot menu to repair windows or start normally.  Starting normally resulted in my system rebooting.  launching the repair started to load, but then I came right back to the MS boot menu.

I cleared the CMOS, loaded defaults and rebooted, this time I booted into windows first.  I was amazed that my NIC was working at 1000GB/s.  I booted to Ubuntu and NIC was at 10, rebooted to windows and it was at 10.  GRRRRRRGGGGHHHH.

After successfully downgrading my bios, several cmos clears later and multiple reboots, I have determined the following to be pretty consistent:

1)  After a BIOS flash, cmos clear and load of defaults, when I boot into Ubuntu first I get 1000MB/s network speed but can't boot to windows

2)  After a BIOS flash, cmos clear and load of defaults, when I boot to windows 7 first (it does work in this order), I get 1000MB/s NIC the first time only.  Any other boots to Ubuntu or Windows downgrades my NIC to 10MB/s, sometimes I may get 100MB/s speed.

Ever since the bios flash, I can no longer have a NIC speed of 1000GB/s AND dual booting into windows and linux, I am stuck with either 100 or 10MB/s, but mostly 10.  If I choose to have the NIC speed of 1000GB/s, I have to perform the option 1 above, booting into linux first after a cmos clear.

Does this make sense?  anyone else experiencing this?  Is the mobo fubar and should be RMA'd?

I talked with ASUS support and they swear it's a windows network driver issue, though this system worked perfectly before I decided to upgrade the bios.

any ideas?

--nixIT

---

### Post by nixIT on 2010-07-15
Marking the solution as a POS motherboard and retiring it after 7 months of service.

---

