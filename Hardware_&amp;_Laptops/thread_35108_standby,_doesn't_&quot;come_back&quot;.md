---
title: "standby, doesn't &quot;come back&quot;"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by sevi on 2005-05-17
Hi,
I've a problem with my acer travelmate 8006 notebook
after going to standby-mode (suspend to RAM) it doesn't come back to linux

The Bluetooth-led blinks, i think this is the main problem :(
I don't use bluetooth anyway, so how can i deactivate it?

or is there an other possibility?

---

### Post by defkewl on 2005-05-17
Go to /etc/init.d to see whether there are bluetooth service in there.
If there is then remove it:
$ update-rc.d bluetooth remove

Other than that I don't know. Perhaps you should run :
$ dmesg 
to see the message and paste it here.

---

### Post by Tschaeck on 2005-05-18
i realized that when using kernel parameter vga=792 or anything like that, it did not come back from suspend to ram.
when using vga=normal it worked.

i recently installed the fglrx drivers. now it isn't working at all ;) it comes back to X but then it crashs.

---

