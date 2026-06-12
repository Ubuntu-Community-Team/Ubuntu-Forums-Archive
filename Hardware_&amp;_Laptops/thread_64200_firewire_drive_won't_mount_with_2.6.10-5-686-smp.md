---
title: "firewire drive won't mount with 2.6.10-5-686-smp"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by akutz on 2005-09-10
I upgraded my kernel yesterday when I saw the update on synaptic.  Now my external 300gb maxtor one-touch drive is not recognized.  Forget mounting, it doesn't even show up in the dev tables.

If I connect it via usb it works fine, but firewire is still faster, so I'd like that if possible.

---

### Post by evilghost on 2005-09-10
Hmm, I updated last night too, same kernel as you.  No issues at all on my end with firewire.  I've got a 80GB firewire/usb 2.0 drive, running/automounted with firewire.

---

### Post by negatory on 2005-09-11
I'm using a maxtor one-touch with 160GB and I cannot mount it using firewire...it doesn't automount...Everything is working with usb2!
Pedro Carrico

---

### Post by dukeleto on 2005-09-11
I have the same problem with a non-smp 2.6.10-5-686 kernel; it's frustrating, 
especially since it used to work beautifully!
Olivier

---

### Post by mlomker on 2005-09-11
[QUOTE=akutz]I upgraded my kernel yesterday when I saw the update on synaptic.  Now my external 300gb maxtor one-touch drive is not recognized.  Forget mounting, it doesn't even show up in the dev tables..[/QUOTE]

Oh?  **sudo fdisk -l** doesn't list the partitions?

---

