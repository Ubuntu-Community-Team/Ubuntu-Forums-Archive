---
title: "Resume via Keyboard"
date: 2008-08-08
forum: General Help
---

### Post by Rebelli0us on 2008-08-08
This is such a basic function but it's still not working. I've searched and read all the posts on this topic. I get the general idea but it's too technical for me.

I did:

cat /proc/acpi/wakeup
echo USB0 > /proc/acpi/wakeup

it worked but wakeup from keyboard works ONCE or only for the session, then it stops working after you reboot. Is there a permanent solution? People posted about a startup script, but I'm really uncomfortable typing system config commands that I don't understand.

Same goes for resume from hibernation. I have a fresh 8.04 install on a new machine, so I'm sure others are having the same problem.

Thanks.

---

### Post by caljohnsmith on 2008-08-08
Most everything in the /proc directory is dependent on currently running processes and such and subject to change, so it's not a big surprise that the solution you found does not work upon reboot. There might be some configuration file somewhere to do what you want to do permanently, but you could easily just run that command automatically every time you boot Ubuntu. Just add your command to the /etc/rc.local file
```
gksudo gedit /etc/rc.local &
```
And at the bottom add:
```
echo USB0 > /proc/acpi/wakeup
```
[COLOR="Blue"]But a caveat:[/COLOR] that command you run replaces the entire "wakeup" file with only "USB0". That probably means that only your keyboard can cause your computer to wake up, and not the mouse or anything else. I would imagine what you really want is:
```
echo USB0 >> /proc/acpi/wakeup
```
That will add USB0 at the end of the wakeup file, so it doesn't erase the references to your mouse, etc.

---

### Post by Rebelli0us on 2008-08-08
Thank you it worked. Is “rc.local” the equivalent of the “autoexec.bat” file?

---

### Post by sdennie on 2008-08-08
> **Rebelli0us said:**
> Thank you it worked. Is “rc.local” the equivalent of the “autoexec.bat” file?

You could think of it as the same, yes.  There are also various other hooks you can use that get executed on certain events such as when the state of the AC adapter changes or when the machine turns on.  I've written a very simple tutorial on how to use these hooks at: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) and, for laptops, a more thorough example of using them for a specific laptop model here: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by john.ennew on 2008-08-10
Hi, this looks like it would work for I want to do as well.  However, when I run the command to add USB0 to be enabled in S3 I get a permission denied error:
```
 echo USB0 >> /proc/acpi/wakeup
 -bash: /proc/acpi/wakeup: Permission denied
```

```
 sudo echo USB0 >> /proc/acpi/wakeup
 -bash: /proc/acpi/wakeup: Permission denied
```

 Any ideas?

Thanks,
John

---

### Post by caljohnsmith on 2008-08-10
John.ennew, when you put a sudo in front of a command and also use redirection, only the command is run as root, but not the redirection. There are a couple tricks to get around this, and here is one that should work for you:
```
sudo bash -c 'echo USB0 >> /proc/acpi/wakeup'
```

---

### Post by Rebelli0us on 2011-11-11
I'm working on a different machine but the solution posted above **works only once**, then the mouse/keyboard device no longer wakes the machine from S3.

in /etc/rc.local I added:

echo UHC4 >> /proc/acpi/wakeup

That seems to enable **all** usb devices for wakeup:

```
cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCE2	  S4	 disabled  
PCE3	  S4	 disabled  
PCE4	  S4	 disabled  pci:0000:00:04.0
PCE5	  S4	 disabled  
PCE7	  S4	 disabled  
PCE9	  S4	 disabled  
PCEA	  S4	 disabled  
SBAZ	  S4	 disabled  pci:0000:00:14.2
P0PC	  S4	 disabled  pci:0000:00:14.4
UHC1	  S4	 enabled   pci:0000:00:12.0
UHC2	  S4	 enabled   pci:0000:00:12.2
USB3	  S4	 enabled   pci:0000:00:13.0
UHC4	  S4	 enabled   pci:0000:00:13.2
USB5	  S4	 enabled   pci:0000:00:16.0
UHC6	  S4	 enabled   pci:0000:00:16.2
UHC7	  S4	 enabled   pci:0000:00:14.5
PE20	  S4	 disabled  
PE21	  S4	 disabled  
PE22	  S4	 disabled  
PE23	  S4	 disabled  
GEC	  S4	 disabled  
PS2K	  S3	 disabled  pnp:00:09
PCE6	  S4	 disabled  pci:0000:00:06.0
PWRB	  S3	*enabled   

```


How do I enable this device for wakeup permanently?

---

