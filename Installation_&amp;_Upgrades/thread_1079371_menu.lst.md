---
title: "menu.lst"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by skezza on 2009-02-24
Hello,
Ive installed Ubuntu via Wubi (mainly because I need to be able to uninstall it very quickly). I am trying to configure the menu.lst to allow me to declare the Label instead of the UUID, but im still getting the alert, device not found. 

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=LABEL=/ loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio acpi=off noapic nolapic quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
```

Any ideas how i can correct that :)?

---

### Post by cariboo on 2009-02-24
Is your partition actually labeled as /? If not you will have to go to System-->Administration-->Partition editor and change the partition label to "/".

Jim

---

### Post by skezza on 2009-02-25
Hi,
No i dont think it is called that. The problem with Wubi is that I don't know how it labels the virtual partition. Wubi is installed on the primary partition, as is ubuntu. How would i go about writing the labels such as hda0 etc? /hda0/ or dev/hda0? ??

Cheers

---

### Post by skezza on 2009-02-25
Anyone?

---

### Post by skezza on 2009-02-28
Is there anyway I can find out my labels, using like a System Rescue CD? the only thing is, i need to know how to write them in the actual menu.lst...

---

