---
title: "Hi. Is there a method to get the serial number of a laptop / desktop computer via the"
date: 2009-08-10
forum: Hardware
---

### Post by Rytron on 2009-08-10
Hi.
Is there a method to get the serial number of a laptop / desktop computer via the terminal or a program?
I know that in Windows you can use Belarc Advisor or run the command:
```
wmic bios get serialnumber
```
in DOS
Thanks.

---

### Post by Grannun on 2009-08-10
I think the one you are looking for is the very first entry only a couple of lines from the top

```
sudo lshw
```

---

### Post by Rytron on 2009-09-04
> **Grannun said:**
> I think the one you are looking for is the very first entry only a couple of lines from the top

```
sudo lshw
```

Thank you Grannun.

For future reference and easier to read I use:

```
sudo lshw > SN.txt
```

---

### Post by sergiom99 on 2009-09-04
What about 'sudo dmidecode' ?

---

### Post by Rytron on 2009-09-05
> **sergiom99 said:**
> What about 'sudo dmidecode' ?

Thank you sergiom99. Its always great to have multiple methods. Excellent.

---

