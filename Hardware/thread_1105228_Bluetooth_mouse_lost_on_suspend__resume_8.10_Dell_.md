---
title: "Bluetooth mouse lost on suspend / resume 8.10 Dell Mini - SOLVED??"
date: 2009-03-24
forum: Hardware
---

### Post by webkris on 2009-03-24
Greets -

I bought a nice new expensive $50 Bluetooh mouse. (Toshiba N554)
I'm running Intrepid 8.10 on my new Dell Mini 9.
Got home - connected device - no issues!

Suspend / Resume = no mouse :(

Did a number of searches. Tried a number of things - restart bluetooth, etc.
The only thing that worked was to DELETE the device, close Bluetooh prefs, open and add new device. This was absolutely silly.

After trying a number of new things this morning, I resumed the Mini, and a notification popped up in Bluetooth panel: "Authorization request for device" I had NEVER seen this until now. (no updates loaded or any OS changes other then an HCITool scan and a Bluetooth restart) It included an "Always allow this device" check box. 

**Once clicked - I have had no issues with my bluetooth mouse on resume / suspend.**

The question I have (and I'm sure others) -
**What makes the authorization popup happen?**

I don't recall that I did anything with the mouse other then suspend and resume the machine a couple of times...
If one can reliably initiate a hardware authorization, you should be able to check the box. I'm sure there is a settings file with this. Please post if you know.

- Kris

---

### Post by pnutzh4x0r on 2009-03-24
I'm not sure about the authorization part.  Perhaps the settings are lost when you remove the device?

My workaround for connecting the mouse after a resume is to have the following script:

```

$ cat /etc/pm/sleep.d/47hci

#!/bin/sh

. "${PM_FUNCTIONS}"

pscan()
{
    /usr/sbin/hciconfig hci0 pscan
}

case "$1" in
    thaw|resume)
        pscan
        ;;
    *) 
        exit $NA
        ;;
esac

```

Whenever you resume, pm-utils it will automatically run this script and do the hci scan to re-connect to your mouse.  If you perform a different hci command, you can simply replace the ond I had up there and it should work the same.  I hope this helps.

---

### Post by webkris on 2009-03-26
**Side note update:**

Now that I've been using the mouse for a few days, part of the issue was my patience. Upon resume it will take a few moments for the OS to recognize my Toshiba Bluetooth mouse. I would resume the PC and turn the mouse on, after 20 seconds or so, the mouse will work. Don't look for it to be instant.

I still have yet to see that authorization popup or know what triggers it.

-Kris

---

### Post by webkris on 2009-03-28
> **pnutzh4x0r said:**
> I'm not sure about the authorization part.  Perhaps the settings are lost when you remove the device?

My workaround for connecting the mouse after a resume is to have the following script:

Whenever you resume, pm-utils it will automatically run this script and do the hci scan to re-connect to your mouse.  If you perform a different hci command, you can simply replace the ond I had up there and it should work the same.  I hope this helps.

**pnutzh4x0r:**
How do you exactly go about implementing this script?
Create a file called "47hci" or whatever in the /etc/pm/sleep.d/ folder.
You'll have to sudo it there and probably chmod it to execute.
What does the line $ cat do?
How do I get this working? Thanks for the help.

Here's what I get when I run that script:
```
kris@pico:/etc/pm/sleep.d$ sudo chmod +x 47hci 
kris@pico:/etc/pm/sleep.d$ ls
[COLOR="Lime"]47hci[/COLOR]
kris@pico:/etc/pm/sleep.d$ ./47hci
.: 3: : not found
kris@pico:/etc/pm/sleep.d$ 

```


I've found that 75% of the time the mouse returns after being patient. Otherwise I have to delete and re-add the device: total weaksauce.

- Kris

---

### Post by webkris on 2009-04-05
Help? I still have to occasionally re-attach the bluetooth device.
I still need help with this script.
- Kris

---

### Post by webkris on 2009-04-13
_-=bUMp=-_

Help?! - Kris

---

### Post by webkris on 2009-04-24
Anyone get better Dell Mini bluetooth functionality with 9.04?

- Kris

---

### Post by coffeeaddict22 on 2009-04-24
I've added ```
sudo hciconfig hci0 down
sudo hciconfig hci0 up
```
to the bottom of my etc/default/bluetooth file, and don't seem to have too many problems.

---

### Post by webkris on 2009-04-25
Okay - I popped that in there, we'll see how it goes.
Thanks!
- Kris

---

