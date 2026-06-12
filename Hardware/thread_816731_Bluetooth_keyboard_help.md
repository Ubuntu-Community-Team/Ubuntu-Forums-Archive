---
title: "Bluetooth keyboard help"
date: 2008-06-03
forum: Hardware
---

### Post by c3lica on 2008-06-03
First: If this is the wrong forum I am sorry, I would consider a keyboard more of an input device then hardware but did not see a section I thought suited this thread better. 

**If you want the condensed version only read the bold.**


Basically I have a bluetooth keyboard (Logitech DiNovo Edge) that I use with Ubuntu (Hardy on a 64 bit PC but running the 86 distro) and my ps3. I would like to connect my keyboard to my ps3 and PC without getting up (My PC and PS3 are in a closet). I can easily connect to my keyboard with my PS3 if it is all ready connected with my PC but doing the opposite is not so easy. (I can do it but I have to push the button on the "Dongle" (is that the right word?) for the keyboard to make it work and with the PC in the closet it would be much easier considering how much I switch back and forth.)
**I was wondering if anyone knew how to connect to a bluetooth keyboard without pushing the physical button? **(It would be nice if it did notrequire me to use a keyboard to do so, BUT I can figure out how to automate it later if you don't know how.

---

### Post by hotweiss on 2008-06-03
The following steps solved my mouse woes, maybe this will work for your keyboard:

**Step 1:** Get the address of your keyboard.

> hcitool scan

**Step 2:** Connect your keyboard.

> sudo hidd --connect XX:XX:XX:XX:XX:XX

You have to do this manually once or it won't connect it automatically at start-up.

**Step 3:** Edit the file /etc/default/bluetooth.

> sudo gedit /etc/default/bluetooth

[B]
Step 4:[/B] Turn on HIDD.

Set the variable HIDD_ENABLED=1.

**Step 5:** Add this line below HIDD_ENABLED=1

HIDD_OPTIONS="--connect XX:XX:XX:XX:XX:XX --server"

**Step 6:** Reboot.

---

### Post by c3lica on 2008-06-04
I get this when I run hcitool scan.

```
hcitool scan
Device is not available: No such device
```

Any suggestions?

EDIT:
I think the adapter that is provided with the keyboard just makes the system think it is a usb keyboard rather then it being and actual bluetooth keyboard so I am gonna go out and buy something that will give my computer bluetooth.

---

### Post by zuikway on 2008-08-15
If all that is needed is the dinovo keyboard and mouse, and no other bluetooth devices are needed, uninstall all the blueZ packages and let the dinovo default itself as a keyboard/mouse.

---

