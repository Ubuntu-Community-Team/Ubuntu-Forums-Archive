---
title: "scsi_proc_hostdir_add: proc_mkdir failed for &lt;NULL&gt;?"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by Maharg on 2006-01-02
Hello, I'm super new to linux so I was wondering if this message during boot is something to worry about.  The system boots fine though it pauses for about 30 seconds before this message comes up but then everything else is fine.  I have a 3ware 9500s4lp raid card in my system that ubuntu is booting from. No other hard drives.  Also, the drivers that come with ubuntu are not the latest that 3ware has. Do I need to upgrade them?  If I do, 3ware only provides the drivers for Red Hat, SUSE and the source and I'd need some help to know what to do with the source.

Here's what my log says:

localhost kernel [4294740.366000] SCSI subsystem initialized
localhost kernel [4294740.367000] 3ware 9000 Storage Controller device driver for Linux v2.26.02.002.
localhost kernel [4294740.367000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 21 (level, low) -> IRQ 21
localhost kernel [4294740.367000] scsi_proc_hostdir_add: proc_mkdir failed for <NULL>
localhost kernel [4294741.235000] scsi0 : 3ware 9000 Storage Controller
localhost kernel [4294741.235000] 3w-9xxx: scsi0: Found a 3ware 9000 Storage Controller at 0xe4800000, IRQ: 21.
localhost kernel [4294741.541000] 3w-9xxx: scsi0: Firmware FE9X 2.06.00.009, BIOS BE9X 2.03.01.051, Ports: 4.
localhost kernel [4294741.541000]   Vendor: AMCC      Model: 9500S-4LP  DISK   Rev: 2.06
localhost kernel [4294741.541000]   Type:   Direct-Access                      ANSI SCSI revision: 03

If this is not a problem (because the system is working) then great. Many thanks to anyone that would teach a newbie like me and put my mind at ease.

Thanks,
James

---

### Post by thomas b on 2006-02-09
James,

I just installed a machine with ubuntu 5.1 server and am getting the same error message at boot. I am using a 8006-2lp 3ware raid controller. Everything seems to be working fine so far, however I'd be grateful if you could tell me whether this has given you any headaches since the start of January. 

I'd also be interested to learn more about what is actually happening when it thows up this message.

---

### Post by darkpixel on 2006-06-29
I'll third this.
I have two 3ware cards (9500S-4LP and 8006-2LP) in an AMD64 system and I'm getting the same message at boot.
No apparent problems though...

---

### Post by darkpixel on 2006-06-29
Bug filed.
[https://launchpad.net/distros/ubuntu/+bug/51323](https://launchpad.net/distros/ubuntu/+bug/51323)

---

