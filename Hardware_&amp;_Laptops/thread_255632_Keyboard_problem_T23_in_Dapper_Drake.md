---
title: "Keyboard problem T23 in Dapper Drake"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by briggella on 2006-09-11
I installed Ubuntu dapper Drake onto my Thinkpad T23 laptop about a month ago and after a few struggles have got most bits working. I have used mandriva/mandrake, suse and fedora core in the past. I still have a problem with the keyboard. If I open a console, every so often the key will spontaneously repeat as if it were held down. This can be stopped by pressing a cursor key. Also some of the keys will randomly not register. This is a major pain when typing a password as it may take ten attempts to get a password accepted even when it is being typed correctly. I have found little that has helped the situation on Google or These fora. Any ideas as I really will not be able to continue to use this distro if I cannot fix the keyboard. It works perfectly in knoppix. I have tried the clock=tsc in grub to no avail.

---

### Post by briggella on 2006-09-13
Found the solution. It appears to be due to PLPtools and battery status monitoring programs. There is a link [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315")

---

### Post by briggella on 2006-09-13
Forgot to mention that the bit that worked for me was to remove plptools and remove the modules acpi_sbs and i2c_acpi_ec. This means I can no longer monitor the battery status, but the keyboard was such a critical issue that if I didn't solve it by this weekend, I would have been wiping Ubuntu off as I cannot work without a keyboard.

---

### Post by davie on 2007-02-28
After a lot of looking around, I finally realised that this bug was fixed - thanks to the good work of [Paul Sladen]("https://launchpad.net/ubuntu/+source/plptools/+bug/40956"), may the Lord always keep him safe on his favourite fold-up bike.
So if - like me - you're eager to try to use your Psion handheld with Ubuntu, you can do what I did and download the latest plptools source package from [here]("http://sourceforge.net/project/showfiles.php?group_id=8797"). No keyboard problems so far. And if - like me - you're a total newbie, [here]("http://www.monkeyblog.org/ubuntu/installing/#source")'s how to install it.
Now... I'll probably be back on these forums tomorrow trying to get the thing mounted.

---

