---
title: "Acer Aspire 3613 - power management, etc."
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by ccf on 2006-02-11
90 minutes of battery life clearly is not acceptable.

Under Windows, as pre-installed (now wiped out), I was able to set things like CPU and graphics power levels to extend the battery life, however, when I try using the frequency scaling applet, it tells me that it is not supported.  How do I make the whole power management thing work, and thus get a sensible life out of my battery?

I checked out the ACPI site at SourceForge with the DSDTs.  The only table listed for the 3613 is claims to be for use with BIOS revision "0xfd70e", though the only hint I can find in my BIOS is "V1.03".  If I'm not loking at the right number, where do I need to look?

---

### Post by ccf on 2006-02-15
After a bit of fiddling (including temporarily rendering the lappy unbootable - hurrah), I managed to find the *p4-clockmod* module gives me 8 frequencies, and the possibility of using conservative, on-demand, frequency governors, as opposed to being on full-speed, high-performance all the time.  Unfortunately, this has only extended my battery life by a paltry 10 minutes, though this is still less than 2 hours.  That, and the frequency ticks up from 187 to 500MHz whenever I try and do anything useful, such as typing.

Any other suggestions for getting more time out of the battery?  I recently had someone telling me their laptop, now several years old, gives him "only 2.5 hours".

---

### Post by ccf on 2006-02-20
Mmm.  Yeah, thanks for all the feedback, folks ... :neutral:

---

### Post by Crayoneater on 2006-02-20
i have an acer aspire 5002WLMi and i get about 2 hours and 45 minutes from my battery....i had an initial problem with ubuntu reading the battery status.  i fixed it by adding:
 
acpi_os_name=Microsoft Windows 2000

as a kernel boot option.  i don't know if that made the battery last longer, but it did fix a few acpi related issues.

---

