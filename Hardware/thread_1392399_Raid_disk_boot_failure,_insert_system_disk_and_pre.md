---
title: "Raid disk boot failure, insert system disk and press enter"
date: 2010-01-28
forum: Hardware
---

### Post by Xephyrind on 2010-01-28
Hi, I am using Asus P5N-T Deluxe 780i Motherboard with Intel Q9550 core2quad. I have 3 hard disks on Sata 2, 3 and 5. I enabled RAID control for all 6 Sata Ports. I then went into RAID management window and combined all 3 drives for striping. then I set it to boot = Yes on this combined RAID drive. Then I exited and all I got is DISK BOOT FAILURE... Any expert's and/or experienced veteran's opinions? Help plz T_T

---

### Post by Xephyrind on 2010-01-28
someone save me T_T~

---

### Post by Xephyrind on 2010-01-29
BUMP~ help plz~ before I drown and cannot BUMP my post above surface of water anymore T_T

---

### Post by tgalati4 on 2010-01-30
So you went into the RAID BIOS and set up your drives.  Now you have to load an operating system onto the RAID.  You will get a boot failure until you do.

If you had an operating system on the drive and you reconfigured it as RAID, then I'm not sure if it is recoverable.

---

### Post by Xephyrind on 2010-01-30
> **tgalati4 said:**
> So you went into the RAID BIOS and set up your drives.  Now you have to load an operating system onto the RAID.  You will get a boot failure until you do.

If you had an operating system on the drive and you reconfigured it as RAID, then I'm not sure if it is recoverable.

Hi, thank you for the reply as you are the first person to do so. When I set up raid, I have emptied everything; therefore, I am not surprised it is doing that. The thing is when I pop in my Ubuntu CD, it doesn't read my CD first. Instead it goes straight to boot up my hard disk, which are empty. I did check my boot order is CD then Hard disks. I don't know why its skipping my CD though.

---

### Post by Xephyrind on 2010-01-30
??~ help plz~?

---

### Post by Xephyrind on 2010-01-31
problem resolved... i realized why my system won't boot.... My DVD-RW drive is using one of the SATA lines... and I enabled RAID on that guy~ hence G_G system never boots up correctly.... I was wondering the heck happened for this past week.... And I finally noticed something is wrong there -.-lll sigh....~

---

### Post by tgalati4 on 2010-01-31
Yea, I was working on a system today with a SATA DVD cable and I thought of that.  Depending on the BIOS, it will group SATA plugs into RAID arrays.  If your DVD/CD drive is in one of those groups, strange things happen.

I'm glad you figured it out.  It was hard to visualize the problem from your initial post because when you first set up a RAID, the very next thing is to load the OS.  There is no expectation to boot from disk.

---

