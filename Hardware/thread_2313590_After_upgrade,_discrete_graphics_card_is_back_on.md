---
title: "After upgrade, discrete graphics card is back on"
date: 2016-02-13
forum: Hardware
---

### Post by lesliek2 on 2016-02-13
I upgraded from 12.04 to 14.04. In 12.04, I was able to turn off my discrete graphics card and rely solely on my integrated graphics. That suited me. However, now that I've upgraded, I see that both graphics are working and the method that I used in 12.04 to turn off the discrete graphics card is no longer working. The driver shown as being used both for the integrated and the discrete graphics is "radeon".

Is there some SIMPLE way I can turn off the discrete graphics card and rely solely on the integrated graphics, as formerly? I did look for answers online, but they were too complicated for me to understand. I just want my fan to stop running so loudly!

Leslie

---

### Post by lesliek2 on 2016-02-14
I believe I've found an answer and will set it out here in case it helps someone else.

First, I installed acpi_call_GUI ([https://github.com/marcoDallas/acpi_call_GUI](https://github.com/marcoDallas/acpi_call_GUI)).

However, it wouldn't run using the open source version of Java that came installed with 14.04.

I therefore installed Java 8 ([http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)) and then reran acpi_call_GUI.

It now worked and appears to have allowed me to choose to turn off my discrete graphics card automatically at every bootup.

So far at least, all seems to work.

Leslie

---

