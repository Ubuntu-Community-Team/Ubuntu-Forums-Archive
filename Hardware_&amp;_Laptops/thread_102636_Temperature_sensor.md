---
title: "Temperature sensor"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by christooss on 2005-12-12
Hello.

I know I have a temperature sensor on processor. I see temperature in BIOS.

How can i see it in GUI or in terminal? I tried gdesklets but temperature space is empty. Is there any command or application to show temperature in terminal?

Thanks for the anwsers

---

### Post by depp on 2005-12-12
I can check my cpu temperature by typing ```
acpi -t
```
I can enable an acpi sensor in sensor-applet, which you can find in synaptic.
Hope it works for you.

---

### Post by arpunk on 2005-12-12
You need to:
*sudo apt-get install lm-sensors*
Then:
*sudo sensors-detect*
And follow the instructions, then reboot to see the sensors and now you can use them the gnome applet and the others.

---

### Post by christooss on 2005-12-12
Thank you very much. Both of you.

Thanks

---

### Post by Griff on 2005-12-13
[QUOTE=arpunk]You need to:
*sudo apt-get install lm-sensors*
Then:
*sudo sensors-detect*
And follow the instructions, then reboot to see the sensors and now you can use them the gnome applet and the others.[/QUOTE]
Did this, everything went ok, then rebooted.  Don't see any change.  No new applications.  Did sudo sensors-detect again to see if it would go through the same motions again and it does.  Am I just missing the applet somewhere?  If so, what is it under by default?

---

### Post by teaker1s on 2005-12-13
you need to look at this
[https://wiki.ubuntu.com/SensorInstallHowto?highlight=%28sensor%29](https://wiki.ubuntu.com/SensorInstallHowto?highlight=%28sensor%29)

---

### Post by arpunk on 2005-12-13
Well that installs the modules and configures them but you still need other applications that can *read* the sensors output. *sensors-applet* can handle them (its available in *universe*).

---

### Post by Griff on 2005-12-13
[QUOTE=arpunk]Well that installs the modules and configures them but you still need other applications that can *read* the sensors output. *sensors-applet* can handle them (its available in *universe*).[/QUOTE]
*head smack* *Thank you.* :p

---

### Post by arpunk on 2005-12-13
Did it work?

---

### Post by Griff on 2005-12-13
[QUOTE=arpunk]Did it work?[/QUOTE]
Yes.  :rolleyes:

---

### Post by hen3rz on 2006-01-21
Any other alernatives to lm-sensors? currently they do not support my chip Winbond W83627EHF, it detects it but there arnt any drivers for it.

---

