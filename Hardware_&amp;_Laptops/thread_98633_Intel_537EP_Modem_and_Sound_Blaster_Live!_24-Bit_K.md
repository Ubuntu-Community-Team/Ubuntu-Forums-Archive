---
title: "Intel 537EP Modem and Sound Blaster Live! 24-Bit Kubuntu 5.10"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by iamkrillin on 2005-12-03
I finally got my Intel modem and my sound blaster live working in Kubuntu 5.10.  These are the steps I had to take.

Modem:
1.  Download driver from intel website(make sure you get partially uncomplied version)

When i tried to make the modules It gave me several errors.  the first error was being caused a version check script to fix it

first make backup of file before edit

2. sudo cp /lib/modules/2.6.12-9-386/build/scripts/gcc-version.sh /lib/modules/2.6.12-9-386/build/scripts/gcc-version.sh_backup

Now edit file

3. sudo nano /lib/modules/2.6.12-9-386/build/scripts/gcc-version.sh
Commit (#) out all the lines but the last and put this in the last line
printf "0295" "0295"

that fixed the first error the last error was a bit more complex it was being caused when the script to make the modules was being called. to fix it takes a bit more work

first make a backup.

4.  sudo cp /lib/modules/2.6.12-9-386/build/Makefile /lib/modules/2.6.12-9-386/build/Makefile_backup

Now edit

5. sudo nano /lib/modules/2.6.12-9-386/build/Makefile

On line 204 you will see this "HOSTCC= gcc-3.4"
Remove the "-3.4"
leaving "HOSTCC=gcc"

On line 321 you will see "CC= $(CROSS_COMPILE)gcc-3.4"
Again you need to remvoe the "-3.4"

Now its time to build
6. {dir you extracted files to} sudo make clean
7. {dir you extracted files to} sudo make 537
8. {dir you extracted files to} sudo make install
8. rm /dev/ttyS15
9. ln -s /dev/537 /dev/ttyS15
10. ls -l /dev/modem /dev/537

That got the modem working for me.  Using it now actually
the soundblaster was not as complicated


Sound Card:
1. Open Mixer
2.  Make sure your using "CA0106"
this was auto detected for me
3. Mute the SPDIF out

---

