---
title: "A little help needed with suspend."
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by menokh on 2008-02-11
I have always had suspend issues on my Compaq V2000 laptop(it would lockup hard upon resume) until recently when I discovered something called pm-utils and now I can get this machine to suspend and even hibernate with almost no issues.  Almost.

I still have a couple problems.  First I noticed that sound never works upon resume, I always have to manually restart alsa in order to get sound working again.  Is there any way to automate that task when using pm-suspend?

Also is there any way to tell Ubuntu that I want to use pm-suspend and pm-hibernate instead of the default that Ubuntu uses?  This would be useful for ACPI triggers such as low battery.

Thanks for any help.

---

### Post by GXP on 2008-02-14
Menokh, I think this might be helpful to you.

The location of the scripts you are looking can be found in: 

```
/etc/acpi
```

From here start by modifying the following scripts:

```
hibernate.sh

sleep.sh
```

Then depending on how your machine is configured you may need to alter other scripts in this directory.

If you then decide that you want the gdmgreeter "ActionMenu", now called the SystemMenu to use pm-utils you can modify the configuration located in:

```
/etc/gdm
```

Open the gdm.conf file in one window and make any changes in a file called  gdm.conf-custom. Being sure to keep the entries under the correct headings. If this file is not present then update gdm.conf directly.

I did not mention to make backups of any of the files you modify, but I do highly suggest a copy before making any changes ;) .

I hope you find this info usefull and helpful. Maybe somebody else will have some additional info.

---

