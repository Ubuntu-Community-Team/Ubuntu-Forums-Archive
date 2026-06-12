---
title: "Bluetooth 2.0+EDR"
date: 2008-05-20
forum: Hardware
---

### Post by marcon00 on 2008-05-20
For some reason my Bluetooth is not being detected at all on my laptop. Searched in forums for similar model , couldn't find anything.
 
Hardy
Bluetooth ( part number V000090200  ) FCCID ryyeytfxcs IC 4389b-eytfxcs 

I'm frankly not that much oriented when it comes to drivers/modules or anything that is inside "filesystem" ( still getting to know )

:) ANy suggetsions ?

---

### Post by marcon00 on 2008-05-31
*bump*

---

### Post by hotweiss on 2008-05-31
**Step 1:** Change to the directory where we are going to have the script file.

> 
cd /etc/init.d

**Step 2:** Creat the script file.

> sudo nano tosh-bluetooth

**Step 3:** Paste this script.

> 
#! /bin/bash

# script to start/stop Toshiba Bluetooth adapter
# requires toshset

case "$1" in
 start)
 /usr/bin/toshset -bluetooth on
 ;;
 stop)
 /usr/bin/toshset -bluetooth off
 ;;
 *)
 echo "Usage: /etc/init.d/tosh-bluetooth {start|stop}" >&2
 exit 1
 ;;

esac

exit 0



Make sure that there is an empty line after exit 0.

**Step 4:** Save and exit Nano.

Type Ctrl-O to exit and Ctrl-X to exit.

**Step 5:** Make the script executable.

> 
sudo chmod 755 tosh-bluetooth

**Step 6:** Add it to the startup scripts.

> sudo update-rc.d tosh-bluetooth defaults

**Step 7:** Reboot.

Your Bluetooth should now be working as expected.

---

### Post by marcon00 on 2008-05-31
I wish i could say its working, its not :(

---

### Post by hotweiss on 2008-05-31
> **marcon00 said:**
> I wish i could say its working, its not :(

Hmmmm, that usually gets the Bluetooth working in Toshiba notebooks.

---

### Post by marcon00 on 2008-05-31
i tired most of the things online, nothing works !

maybe give it another shot?  :) anyone ?

---

### Post by hotweiss on 2008-05-31
> **marcon00 said:**
> i tired most of the things online, nothing works !

maybe give it another shot?  :) anyone ?

The Toshiba A200 uses the same Bluetooth module as the F40. This user got it working:

[http://wiki.archlinux.org/index.php/Toshiba_Satellite_A200](http://wiki.archlinux.org/index.php/Toshiba_Satellite_A200)

---

### Post by marcon00 on 2008-06-02
> **hotweiss said:**
> The Toshiba A200 uses the same Bluetooth module as the F40. This user got it working:

[http://wiki.archlinux.org/index.php/Toshiba_Satellite_A200](http://wiki.archlinux.org/index.php/Toshiba_Satellite_A200)




I tried omnibook after all, does not work, it does not support Qosmio F40.

---

### Post by marcon00 on 2008-06-15
This is weird, after Kernel upgrade , to the *19 version, after reboot i had Bluetooth icon shownig !! but it disappeared again after restart .. :S:S:S

---

