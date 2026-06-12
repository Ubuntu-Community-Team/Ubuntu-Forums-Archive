---
title: "Asus A6KT-Q001H"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by m4t7e0 on 2006-06-13
Hello, i'm italian and don't speack english very well..
I have this Notebook e a lot of Problem..
1. If I install the Ati display driver don't have a 3d Acceleration...
fglrxinfo NOT give me ATI Radeon X1600 but a table... 
2. If i connect the usb mouse first of the Notebook PowerOn the Kernel in the boot state stay blocked..
3. The WebCam don't Work...
4. In the normal execution, on the osd appear a messagge "Display LCD: Change OFF" or  ON
5. The UP/DOWN Volume Keys don't Work..
6. The external key don't Work
7. The Wireless and Bluetooth led don't work
8. The email led don't work
9. The cpu profile key don't work
10. The Email key don't work
11. the Browser ket don't work
12. The touchpad disabilitation key don't work

Now the point 1 - 2 - 3 - 4 -5 Is Important.. and from 6 to 12 is an Optional..
The WebCam is an
USB2.0 Video 
Produttore: Syntek Semicon. 
Identificativo venditore 0x174f (Vendor ID)
identificativo prodotto 0xa311 (Product ID)

IF ANYONE can help me i'm stay here!! :) Thanks!!! 
CPU: AMD Turion 64 Mobile MT-34
Chipset: SIS 756+964L

---

### Post by [h2o] on 2006-07-27
Think I got the same model. No luck with finidng drivers yet. Tried the m560x drivers project, but that didn't work.

---

### Post by krazyd on 2006-07-27
Sweet! finally found others with the same notebook!

After spending some time screwing around with Dapper on this notebook, I've decided to just wait for Edgy. :( Too many issues at the moment.

1. This worked for me: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

2. This is due to a bug in the BIOS (apparently. I don't understand why this is not a bug in the kernel if WinXP can handle it.. oh well) It cannot be fixed by upgrading to the latest BIOS from ASUS. Hopefully it will be fixed in Edgy (if anyone has tried installing Edgy on a A6Kt, please let us know how it went). You can work around it adding 'acpi=off' to the boot command, but this b0rks the power settings and shows the battery as charging constantly. I wouldn't recommend it.

4. Haven't seen this.

5. Works for me. Try the Keyboard Shortcuts menu in Gnome Preferences.

10,11,12. These can be set in Keyboard Shortcuts AFAIK.

---

### Post by alditch on 2006-11-10
hi. I have got asus A6M-Q0033H. it doesn't have ati but nividia, so i am not able to help you with this but :
i've installed edgy 64 and 32 bit and if you want to install it, set the kernel to boot with: noapic nolapic, if this doesn't help try adding acpi=off, once installed, you can delete acpi=off line and then all buttons and leds should work well. webcam - i've got the same chipset,no luck till now, though i am still thinking about this:)
i have to admit that usb works strange... my mouse sometimes works well, sometimes not at all.

---

