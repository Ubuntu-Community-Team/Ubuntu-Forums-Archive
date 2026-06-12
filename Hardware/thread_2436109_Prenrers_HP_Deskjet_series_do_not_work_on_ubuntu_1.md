---
title: "Prenrers HP Deskjet series do not work on ubuntu 18 LTS"
date: 2020-01-31
forum: Hardware
---

### Post by albel2 on 2020-01-31
I have two very old printers of the HP Deskjet series (D4163 and 3940). They seem to be installed. But when docs prints, the page just rolls. The printer carriage remains motionless.
>Can such old printers work on new ubuntu?

---

### Post by Autodave on 2020-01-31
Are you sure that the printers work at all?  What driver/softwarehave you installed?  How are they connecting to the PC?

---

### Post by slickymaster on 2020-01-31
*Thread moved to **Hardware**.*

---

### Post by CelticWarrior on 2020-01-31
If the printer aren't broken, please make sure you have the drivers and HP printers management software installed, for better control:

```
sudo apt install hplip hplip-gui
```

---

### Post by brian_p on 2020-01-31
> **albel2 said:**
> I have two very old printers of the HP Deskjet series (D4163 and 3940). They seem to be installed. But when docs prints, the page just rolls. The printer carriage remains motionless.
>Can such old printers work on new ubuntu?

Let's see. Please give what you get for ```
lpinfo -v
```

---

