---
title: "Shutdown 'hanging'."
date: 2008-10-05
forum: Hardware
---

### Post by Dervheid on 2008-10-05
[FONT="Comic Sans MS"]Just installed Ubuntu on my sad old laptop, on a dual boot setup with windows. All working fine, connecting to my wi-fi network etc. Only issue I'm having at present is when I restart or shutdown, the laptop seems to 'hang' on a blank screen with a rapidly pulsing cursor, and fails to completely shut down or reboot.
To get the laptop to shut down completely I'm having to do a reset by holding down the power switch until the laptop powers down. It then refuses to restart unless I remove (and reinstate) both the mains supply and the battery.
Not a major problem, just a pain in the proverbial. 
Anyone experience this / have a solution?[/FONT]

---

### Post by glotz on 2008-10-05
Try this. Open the terminal. Make a backup of your /boot/grub/menu.lst with
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup**

Then let's edit the file
**sudo nano /boot/grub/menu.lst**

scroll down to a kernel line of a boot option you wish to use. Then append *acpi=force* to the end of it. To exit (and save) hit
**Ctrl-X**

and answer
**Y**

when asked if you want to save and hit
**enter**

when prompted for the name. Now reboot and see if it works.

---

### Post by Dervheid on 2008-10-05
[FONT="Comic Sans MS"]Thanks. I'll give it a try next time I actually get a chance to do some work on the ol' lappy. Which, with my life will likely be next weekend. I'll let you know how it goes.[/FONT]

---

### Post by Dervheid on 2008-10-07
[FONT="Comic Sans MS"]I got some time to have a look at that last night. Not sure where you propose I insert that piece of code (or what it's designed to do)
The Problem now seems to be limited to the REBOOT option (I did get a whole shedload of updates via the update manager) as the laptop does power down completely when I select shutdown.
A little more info for this Linux virgin would be greatly appreciated.[/FONT]

---

### Post by run1206 on 2008-10-07
> **Dervheid said:**
> [FONT="Comic Sans MS"]I got some time to have a look at that last night. Not sure where you propose I insert that piece of code (or what it's designed to do)[/FONT]

open a terminal end use the edito of your choice ( i use gedit)
```
sudo gedit /boot/grub/menu.lst
```

then go the the line that says kernel...
here's mine.
```

title		Ubuntu intrepid (beta), kernel 2.6.27-5-generic
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=1b0caa0a-86ac-4be0-be45-55fbb7ed5e46 ro splash vga=792 rootflags=data=writeback**
initrd		/boot/initrd.img-2.6.27-5-generic
quiet

```

and type in acpi=force

should show this...

```

title		Ubuntu intrepid (beta), kernel 2.6.27-5-generic
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=1b0caa0a-86ac-4be0-be45-55fbb7ed5e46 ro splash vga=792 rootflags=data=writeback acpi=force**
initrd		/boot/initrd.img-2.6.27-5-generic
quiet

```

edit: i just tried it, doesn't work for me :(
but my system is different than yours, give it a shot. worse case scenario, remove acpi=force when you bootup again.

---

### Post by glotz on 2008-10-08
It's just something I found online. It worked for me with one computer that wouldn't power down. Not sure if this really has to do with your problem.

You'll want to make sure your boot menu has more options than the one you modify if it causes problems. (or that your boot menu is set up so you can easily edit it at boot time, or you have a boot disk handy... etc)

Looks like it's some sorta power control thang [http://en.wikipedia.org/wiki/Acpi](http://en.wikipedia.org/wiki/Acpi)

---

### Post by rafe101 on 2008-10-08
Sometimes mine doesn't want to startup unless I unplug the power and let it boot up off the battery.  It is annpying sometimes, but I've just been living with it.

---

### Post by xranitel on 2008-10-08
Possibly related problem. Installed Ubuntu from the live CD (for the 4th time already: last time the OS files were wiped out after the filesystem got unreadable and I used fsck to fix it). Restarted the computer. Entered the name and password, the password was not recognized. Followed the instructions in the thread of logging in with no password: [http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html) After logging in as a root used passwd to reset the password, new password prompt appeared and after one letter was typed I was immediately prompted to retype the password. Then I stopped seeing the input on the screen, only the output. I typed "reboot" and the message is  "shutdown: Unable to send message: Connection refused". shutdown -r now returned the same. I pressed alt+ctr+del and rebooted. Once the username prompt comes up, and I enter the username, instead of the password prompt I get "the system is going down for maintenance NOW min" I click ok and it tells me the password is incorrect.
Gateway 1626, amd64.

---

