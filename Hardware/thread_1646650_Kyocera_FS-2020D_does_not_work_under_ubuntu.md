---
title: "Kyocera FS-2020D does not work under ubuntu"
date: 2010-12-16
forum: Hardware
---

### Post by ultraxx on 2010-12-16
Hi all,

I have a Kyocera FS-2020D and Ubuntu 10.10 operating system. I followed the manufacturer instructions to install the printer, but it does not work.

Manufacturer's PPD for the printer: [http://usa.kyoceramita.com/americas/jsp/upload/resource/19915/0/Kyocera_FS-2020D.PPD]("http://usa.kyoceramita.com/americas/jsp/upload/resource/19915/0/Kyocera_FS-2020D.PPD")

Cups always says processing and than nothing happens. I use PCL 6 emulation in the printer but tried the KPDL also.

I contacted the Kyocera support, and they provided me a Mac OSX driver and they told me that will work because linux and mac are unix based systems...

I tried to print from command line. I run this command:

```
echo -en "Hello World!" > /dev/usb/lp0 
```

But I never got back the prompt. Maybe this is some sort of communication problem related to the kernel? (There is no problem printig from windows)

Thank you in advance all help.

---

