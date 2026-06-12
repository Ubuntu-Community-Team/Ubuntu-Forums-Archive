---
title: "IBM R40e and ACPI"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by Beta-Glitch on 2005-05-25
Ok, First off, let me say Ubuntu has been my fav distro I've tried (yey! Gnome by default!), well done to the Ubuntu developers!

Ok, now the problem. My IBM R40e laptop has a problem with ACPI causing any Linux distro (and FreeBSD) to hang during startup. I'm also not very experienced with Linux at all. To install ubuntu 5.04 I've had to add acpi=off to my boot parameters. This has obviously left me without my battery information, which I could do with knowing as I run it off battery alot.

I know the problem is related to the processor.ko ACPI module. Under SuSE 9.2, I could move the files processor.ko and thermal.ko (dependant on the processor.ko module) from /lib/modules/{kernel version}/kernel/drivers/acpi/ to anywhere else on the system, and the ACPI module's would **NOT** be loaded. I've tried the same trick under ubuntu and it unfortunately doesn't work.

on [http://pc.freeshell.org/tp/](http://pc.freeshell.org/tp/) there is a kernel patch listed to fix the problem. Unfortunately, being new to linux, I have no idea how to start with something like a kernel recompilation.

So,

1) Can I deactivate the processor and thermal ACPI modules from not loading in a config file?

2) if not, can someone tell me **EXACTLY** how to apply the above patch and recompile the kernel, Step by Step instructions would be good!

Many thanks in advance

---

### Post by Beta-Glitch on 2005-05-31
I don't mean to sound rude, but People are taking an awful long time to answer a question that should be quite easy to answer.

I am still using this laptop, and not being able to see the battery status is quite annoying.

Any help would be good

---

### Post by consecratus on 2005-06-01
Good day mate,

Enable back your ACPI, in Hoary or 2.6.10 if you want to refer to the kernel the ACPI problems have been fixed as for the patch, it was bit of a pain as I have no experience in Gentoo but found some interesting thing for ya.

First of, Go to Computer > /usr/include/asm
You will find processor.h

Just copy and paste this (obviously in the BIOS version you need to change to your BIOS version) and save.

static struct dmi_system_id __initdata processor_power_dmi_table[] = {
      { no_c2c3, "IBM ThinkPad R40e", {
        DMI_MATCH(DMI_BIOS_VENDOR,"IBM"),
        DMI_MATCH(DMI_BIOS_VERSION,"1SET60WW") }},
      { no_c2c3, "Medion 41700", {
        DMI_MATCH(DMI_BIOS_VENDOR,"Phoenix Technologies LTD"),
        DMI_MATCH(DMI_BIOS_VERSION,"R01-A1J") }},
      {},
};

I am pretty certain that this will work as processor file mentioned in the website you referred to has pretty similar infos on it.

But before you try this backup your system!

See how you go.

---

### Post by Beta-Glitch on 2005-06-01
thanks for your reply :)

Ok, so I edited that file, replacing '1SET60WW' with '1SET56WW' (my BIOS version), and rebooted, adding an entry to grub's menu.lst that starts the 2.6.10-5 kernel without the acpi=off argument and it got further, but then locked up at 'loading ACPI modules...'.

Also, I have done a bit of experimenting myself, and have downloaded a linux-image of 2.6.12-1, which also fails to boot. I also had to download initrd-tools 0.81.1 to install the linux-image, and I think that may have actually been the thing that made it boot further.

Any other suggestions anyone?

---

### Post by Beta-Glitch on 2005-06-02
well, it's fanally sorted.

After the steps above which were getting me further in the bootup, I then moved the processor.ko and thermal.ko to elsewhere so they could not load and it boots fine, reading battery and AC info fine!

thanks for the help consecratus.

I must say, this problem took a while to solve, and for what i read to be a great support forum for help, I'm a little disapointed with the response to something as routine as an ACPI problem.

---

### Post by Phanatic on 2005-10-12
this problem has been fixed with breezy (kernel patch applied), but the lastest bios version wasn't added (April 2005: 1SET68WW), so i had to downgrade my bios to be able to use acpi...

---

