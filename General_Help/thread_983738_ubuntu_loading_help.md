---
title: "ubuntu loading help"
date: 2008-11-16
forum: General Help
---

### Post by banana jama on 2008-11-16
I downloaded ubuntu 8.10 about 2 weeks ago and this problem has always occured but i've just ignored it until now. this is the problem : when i turn on my computer and ubuntu loads the loading bar (that orange thing that moves left to right) stops and it doesn't move unless i press the power button. after i press the power button it continues loading and i have no further problems. o yea im running the 32bit version of 8.10 
         Does anyone no why the loading bar keeps getting stuck midway? is there a way that i can fix this?


P.S. about my computer: HP Palivion dv6000 Amd turion64 x2 2GHZ, 2 GB ram, 250 Gb Hard drive.

---

### Post by taurus on 2008-11-16
Try to see which process causes the hang up.  Boot your computer and at the GRUB menu (if you see the word GRUB at the upper left corner, you have 3 seconds to press the ESC key to bring up the menu).  Then, hit e to edit and move to the end of the kernel's line and remove both **quiet splash**.  Then, hit b to boot.  

Now, instead of seeing start up bar, you would see text scrolling on the screen and see which is the last process before it hangs.

---

### Post by 73ckn797 on 2008-11-16
I was noticing a similar issue with the last Intrepid rc version, but that has stopped with the "official" release version upon subsequent updates. The bar would jump erratically while loading. It has not occurred since.

Did you perform a md5 checksum on your download? Could be something related to a bad burn?

Could be something related to your system specs.

Just a few questions.

---

### Post by banana jama on 2008-11-16
no it's not a bad burn i upgraded from 8.04 also i don't think its specs since it handled 8.04 nicely i didn't have any trouble with it loading. also what am i suppose to do if i find out what's the last thing it does before it hangs.

---

### Post by taurus on 2008-11-16
Just post it here.

---

### Post by TopEnder on 2008-11-16
taurus, re your post #2 is thers anyway to stop/pause the script while loading. I get a few minor [COLOR="Red"]errors[/COLOR] while loading but the script loadas to quickly to read these errors.
Thanks TopEnder

---

### Post by banana jama on 2008-11-16
ok i did what you said and this is what it said it's alot:
> 
r3
[2.702245] ochi_hcd 0000:00:02. 0i ir18,i0 0xf6486000
[2.759339] usb3i configuration #1 chosen from 1 choice
[2.759339] hub3-0:1.0: usb hub found
[2.759407] hub 3-0:1.0: 7 ports detected
[173.707753] clocksource tsc unstable (delta=4398045518571ns)
[173.708204] usb-2: new high speed usb device using echi_hcd and address 2
[173.709389] ACPI:PCI interrupt link[Z018] enabled at IRQ 18
[173.709458] ochi_hcd 0000:00:04.0:PCI INT A -> Link[Z018]-> GSI       18(level,low)->IRQ 18
[173.709548] ochi_hcd 0000:00:04.0: OCHI Host Controller
[173.709643] ochi-hcd 0000:00:04.0: new usb bus registered, assigned bus number 4
[173.709729] ochi_hcd 0000:00:04.0:irq 18,io men 0xf6487000
_


 
So.... what now? o yea i see a lot of usb stuff in this stuff above and just to let you know that i didn't have anything in any of my usb ports. i don't know if that was helpful.

---

### Post by banana jama on 2008-11-16
does anyone no what to do????

---

