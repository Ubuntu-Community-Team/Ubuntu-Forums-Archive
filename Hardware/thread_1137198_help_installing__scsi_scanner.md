---
title: "help installing  scsi scanner"
date: 2009-04-25
forum: Hardware
---

### Post by ray17374 on 2009-04-25
I just installed Jaunty and am trying to install an old HP Scanjet5p scanner with a Kouwell scsi card. I was able to find drivers for the card which is a KW-801V10P in the zip format.
Reading the install instructions it tell me to extract the files to /usr/src/linux/drivers/scsi. The problem I have is that when I extract to that path I get a pop up telling no such folders exist and I do not have permission to create one.

Can anyone help me install these drivers so Xsane will recognize my scanner.

Thanks,
Ray

---

### Post by cariboo on 2009-04-25
THe drivers for your scsi may already be installed, open a terminal and type:

```
lsmod | grep scsi
```

to see if the drivers are already installed.

---

### Post by ray17374 on 2009-04-25
I get scsi_transport_spi  30080 1 sym53c8xx.

Xsane says no devices available.

thanks for the quick reply.

Any Ideas?

---

