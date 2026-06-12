---
title: "[SOLVED] Quick Keys not working"
date: 2008-09-24
forum: Hardware
---

### Post by jpeery on 2008-09-24
My quick yeys stopped working, for example I could push a button on the laptop and adjust the sound, now it stopped working.  Any ideas how to troubleshoot that one?
Thanks,
Jason

---

### Post by jpeery on 2008-09-24
> **jpeery said:**
> My quick yeys stopped working, for example I could push a button on the laptop and adjust the sound, now it stopped working.  Any ideas how to troubleshoot that one?
Thanks,
Jason

Oh yeah, it's an HP Pavilion Laptop

---

### Post by jpeery on 2008-09-24
> **jpeery said:**
> Oh yeah, it's an HP Pavilion Laptop

Bump?  Any ideas how I can troubleshoot?  I was looking through the keyboard shortcuts and it looks like the setting is a hex value, but that doesn't really tell me much...  I don't see anything in any of the logs, although I'm not quite sure what to look for.  Any ideas?
Thanks,
Jason

---

### Post by IcarusR on 2008-09-27
You should be able to reset fromKeyboard shortcuts. left clik the setting & then hit the required key. Close & test.

---

### Post by jpeery on 2008-09-27
> **IcarusR said:**
> You should be able to reset fromKeyboard shortcuts. left clik the setting & then hit the required key. Close & test.

I'm starting to think I've got bigger issues, when I try to set the value, it does nothing when I hit the "Quick Play" button (eg Volume Up).  So it seems that the computer itself, perhaps, isn't recognizing it, something.  I'm wondering if there is a way, like lsusb to see if this thing is even being seen/recognized?  I'm not even sure what to look for, and assume it may just be listed as keyboard hardware.  I guess I'll try an lshw and see if I can tell anything.
Thanks!
Jason

---

### Post by jpeery on 2008-09-27
This seems to be the only suspect entry:

 *-generic UNCLAIMED
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 5.4
             bus info: pci@0000:07:05.4
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255


Maybe it's time I take the keyboard off this laptop and make sure it's clean

---

### Post by jpeery on 2008-09-27
Well, that wasn't it, BUT I got to fooling around with the keyboard, was going to remove it and clean it, when the quick keys started working again...  So I suspect gunk in the cracks somewhere.  Whew, this ol laptop sure is starting to show some character :-)

Thanks for the help!
Jason

---

