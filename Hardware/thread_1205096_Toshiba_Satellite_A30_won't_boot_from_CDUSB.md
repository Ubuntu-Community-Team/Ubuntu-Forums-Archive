---
title: "Toshiba Satellite A30 won't boot from CD/USB"
date: 2009-07-05
forum: Hardware
---

### Post by uberben on 2009-07-05
I am trying to install 9.04 on an old Toshiba Satellite A30 I got second hand. I set the BIOS to boot first from CD plus pressing F12 at the BIOS logo screen allows me to select what I want to boot from. I have tried a few different live cds and none of them will boot (I get an underscore character for about 30 sec. and then Windows will boot). If I have a CD in the drive, entering the "boot selection menu" takes forever. I was able to read CD's while in Windows before this process started, but now it would appear as though I can't. I can still read USB drives in Windows, but I can't seem to boot from live drives. Does anyone have any suggestions? Let me know if you need more detail.

---

### Post by 67GTA on 2009-07-05
Bad CD drive? You can install from USB through Windows with Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by uberben on 2009-07-05
I remembered that recent versions of Ubuntu have Wubi built in, so I have installed 9.04 using a disc image and a virtual disc drive. This install is failing to fully boot (sitting at the Ubuntu logo screen with the loading bar bouncing back and forth until it sticks, which oddly enough unsticks if I tap the power button a few times). I checked the system requirements for 9.04 and it needs about 30mb more ram than I have, so I'm not sure if this would be an issue or not.
Even if I can get the Wubi install to boot, I am scared to commit the install as I do not have the ability to boot any other installer media if something goes wrong.

---

### Post by uberben on 2009-07-05
Thanks for the reply, 67GTA. UNetBootin gave me some error message as soon as I booted into the "frugal" install. I meant to copy the error message, but I got rid of it already. Again, even if it had worked, I would have been afraid to keep that install as I would not have any way to fix the machine (ie get it back to Windows) if anything went wrong with the partition.

---

### Post by 67GTA on 2009-07-05
If it were me, I would make sure I didn't have any hardware problems first. You could try something like Tufftest or Sandra. They are both free for home use:

[http://www.sisoftware.net/index.html?dir=&location=home&langx=en&a=](http://www.sisoftware.net/index.html?dir=&location=home&langx=en&a=)

[http://www.tufftest.com/tt01-lite.htm](http://www.tufftest.com/tt01-lite.htm)

---

### Post by uberben on 2009-07-14
Thanks for the links, 67GTA. It looks like that second link is to a software that runs off of CD, which won't work in my scenario, but I am about to tri this SiSoftware one. In the meantime, I went to fix something on my main desktop computer (it has a strange, high pitched sound coming from something other than the HDD, DVD drives, graphics card, CPU fan, or case fans, and I'm pretty sure it isn't the PSU fan either, so it might be a capacitor in the PSU or motherboard...) and I wanted to boot a live CD for some diagnostics and reinstallation of things, but I can not boot from CD on this machine either! I know that CD booting has for sure worked on this computer and it would appear to still be able to read discs when I am in Windows, but it can't boot to any bootable CD. I can boot from USB on this machine, though, but if I want to repair Windows (I'd rather have Ubuntu, but I have a few mission criticals in there at the moment) I would have to hack my way to a bootable XP USB installer. Any tips on the new situation while I try out this software on the laptop?

---

### Post by dan_kent on 2009-07-15
have youtired to boot with the apci=off option. I member of our lug has this laptop and needed to turn on apci in order to get it to boot

---

### Post by gibbylinks on 2009-07-16
I have this laptop and can confirm it won't boot without the "acpi=off" in grub.

Also I couldn't boot from CD/DVD-Rom after a firmware upgrade to the CD drive. Bought a new drive (off E-Bay £12.00) and it booted fine.

Jaunty installed and working fine, my only gripe is it doesn't power off, just sits there with "system halted" message :D

---

### Post by uberben on 2009-07-20
turning off acpi is something i have to do once it has booted off the disc, but i can't boot off ANY disc nor can I boot from a usb drive. if it were just a cd firmware issue, that wouldn't explain the lack of usb boot. i can't boot from a windows disc either. you would think that if they released an update to the cd drive that broke windows booting, they would have to fix that. how long ago did they release that update? maybe there is another update that fixes things that i could use.

---

### Post by davidmohammed on 2009-07-20
I've got this model - have you checked that you've got the latest bios update ?(go to the [toshiba]("http://eu.computers.toshiba-europe.com/innovation/download_drivers_bios.jsp?service=EU") website) - this fixed booting issues and shutdown issues for me.

---

### Post by uberben on 2009-07-21
Is there a simple way to check the BIOS version I currently have? I'd like to avoid updating the BIOS if I can, although I might just do it anyway in case the BIOS has become corrupted or something.

---

### Post by 67GTA on 2009-07-21
Run ```
sudo dmidecode
``` in a terminal. The BIOS version will be about the 4th-5th line from the top.

---

### Post by uberben on 2009-07-23
Maybe I haven't mentioned this yet, but I currently have XP installed, so no sudo for me.

---

### Post by davidmohammed on 2009-07-24
quick google search recommends the following:

Click on Start and then Run. 

In the text box in the Run window, type msinfo32 and click OK. This will open the System Information program. 

When System Information first opens, it defaults to the System Summary, a short list with some of the most important information about your computer system listed. 

On the right side of the program, locate the BIOS Version/Date entry. 

This field contains the BIOS version that is currently running on your motherboard. This field may also contain additional information such as the BIOS date, BIOS manufacturer, motherboard manufacturer and the motherboard model number. 

Note: If the BIOS date is shown, it can be useful in determining the current BIOS version from a motherboard manufacturer's website if the version is not clear here. 

Close System Information.

---

