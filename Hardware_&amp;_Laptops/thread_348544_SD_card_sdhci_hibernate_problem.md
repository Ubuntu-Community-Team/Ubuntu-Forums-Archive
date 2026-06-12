---
title: "SD card sdhci hibernate problem"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by dr_d12 on 2007-01-28
Hi all, 

I'm trying to get hibernate to work on my Thinkpad X40.

1) When I hibernate with an SD-card mounted, during the wake-up the following error repeats several times:

mmc0: timeout waiting for hardware interrupt, contact [email]sdhci-devel@list.drzeus.cx[/email]

2) When I hibernate without an SD card mounted, this error goes away but the SD card is no longer automatically mounted after wake-up.

I think I want to add stop sdhci during hibernate, and start sdhci during restart? How do I do that?

Thanks,
DD

---

### Post by Eddie Hung on 2007-07-14
For the record, I have an X41 and I have this problem also.

A suggestion can be found here:

[http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram](http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram)

which can be performed by editing:
/etc/default/acpi-support

and adding the appropriate modules to MODULES=""

I don't have a SD card handy - so if anyone can confirm that this works, that would be great!

Eddie

---

### Post by dr_d12 on 2007-07-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78634](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78634) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks for the tip,

I added sdhci

 ```
        MODULES="sdhci" 
```

in the file

   ```
            /etc/default/acpi-support
```

and now my suspend to ram and disc will work with the SD-card mounted. Before, it would not suspend-to-disk and would not wake from suspend-to-ram with the SD-card in.




An error shows up while suspending-to-disk that I hadn't seen before:

       ```
     usbdev4.1-ep00: PM: resume from 0, parent usb4 still 2
          usbdev4.1-ep81: PM: resume from 0, parent 4-0:1.0 still 2
```

with or without the SD card mounted. Suspend-to-disk and resume-from-disk will work after similar errors repeat.

Dave

---

### Post by Eddie Hung on 2007-07-23
I've now taken the plunge with Gutsy - and it seems to now be able to suspend with a SD card in, without any acpi-support modifications.

However, when I resume, it moans about the card not having been unmounted properly - which is a little worrying.

I've yet to test whether modifying the acpi-support, as for Feisty, would prevent this message appearing.

Eddie

---

