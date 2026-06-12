---
title: "Ubuntu 14.04 doesn't recognize new keyboard"
date: 2014-09-09
forum: Hardware
---

### Post by ricardo072 on 2014-09-09
Hi All,

By some reason Ubuntu 14.04 x64 LTS doesn't recognize my new keyboard, it is a USB Perfect Choice model PC-200628.

what can I do? as you can see I do not have keyboard to execute commands from the console.

Thank you,
best regards.

---

### Post by ibjsb4 on 2014-09-10
I have not been able to find a pdf in English for this keyboard.

There does not seem to be any linux support for it, just windows.
The driver download I found for it is windows only.

---

### Post by Vladlenin5000 on 2014-09-10
It's just a keyboard like any other. I've used many similar ones, although not this model in particular, all they all work as they should. 
If the keyboard isn't recognized it's either faulty or in conflict (same keyboard aren't properly recognized if booted along with some other USB devices).

---

### Post by ibjsb4 on 2014-09-10
> **Vladlenin5000 said:**
> It's just a keyboard like any other.
Most keyboards are, but not all.  This is a high tech keyboard and I believe not yet recognized by ubuntu.
missing, wrong, bugged keyboard device drivers
Bottom of page
[https://help.ubuntu.com/community/InstallUSBKeyboard](https://help.ubuntu.com/community/InstallUSBKeyboard)
Could be wrong, you think?

---

### Post by Vladlenin5000 on 2014-09-10
> **ibjsb4 said:**
> This is a high tech keyboard and I believe not yet recognized by ubuntu.

Are you being sarcastic? If so, :lolflag:

What's "high tech" about it? The rubber?

Obs. 1: There are keyboards with additional keys that may or may not be already supported in Linux/Ubuntu (most multimedia keys sets already are and so are many gaming oriented keys most of them need to be assigned for special profiles, regardless of the OS, anyway), that may or may not require some proprietary software to assign function to those keys. Anything deviating from the standard is a potential problem but the keyboard itself should always work, albeit partially.

Obs.2: There are also cases of deviations from the USB HID standard - Logitech wireless and a few others - resulting in annoying issues in Linux/Ubuntu whereas in Windows, thanks to proprietary drivers, the same hardware works flawlessly.


Other than the aforementioned scenarios no, it doesn't happen.


> [https://help.ubuntu.com/community/InstallUSBKeyboard](https://help.ubuntu.com/community/InstallUSBKeyboard)
Could be wrong, you think?

Quoting:

```
[COLOR=#333333][FONT=Ubuntu]We have to distinguish three specific and chronologically ordered situations where a USB keyboard is used:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]1) to enter and optimise the BIOS setup;
2) to select the operating system to boot, by the use of the boot manager (e.g. Grub, [LiLo]("https://help.ubuntu.com/community/LiLo")...);
3) during and after o.s.' log-in (both in the character terminal as in graphic windowing mode).
[/FONT]
[/LIST]
**[COLOR=#333333][FONT=Ubuntu]Coherently with what we have stated before, only the first two options are covered on this document, therefore some rough indications are given at the end of this document to address the right destination for your further actions.[/FONT][/COLOR]**
```

(My bold)

In a nutshell, the document covers scenarios #1 and #2, where #1 is OS independent, #2 refers to the bootloader (part of the OS but not the OS yet).
The OP has a problem as #3 and we don't know about #1 or #2.

---

### Post by ibjsb4 on 2014-09-10
Think you went a bit overboard, but fine, fix this for the OP.

---

### Post by Vladlenin5000 on 2014-09-10
The usual troubleshooting...

1. Test the keyboard in another computer, hopefully available. Good? Then...
2. Test if it works in BIOS/UEFI - it should in any recent hardware; issues occur mostly in older machines with PS/2. 

At this point studying the document you linked - [https://help.ubuntu.com/community/InstallUSBKeyboard](https://help.ubuntu.com/community/InstallUSBKeyboard) - may come in hand.

Now, enabling/disabling 'USB legacy' and/or other settings like "Plug & Play OS", and/or other USB related settings at the BIOS may be required also. It should be a matter of finding the settings that enable USB keyboards (and other HID devices) for the bootbloader (after POST, before OS) and the OS itself, Ubuntu.

---

### Post by ricardo072 on 2014-09-10
Hi ibjsb4 & Vladlenin5000,

I really appreciate your feedback and comments (it is a lot of info, great I have learned a lot)... finally it was a hardware failure, Best Buy gave me a new one and that's it.. everything is working fine now (will mark this as resolved).

Thank you,
Bert regards.

---

### Post by ibjsb4 on 2014-09-11
Good call Vladlenin5000

Didn't mean to push your buttons :)  I will try to be more gentle with you in the future.

---

### Post by Vladlenin5000 on 2014-09-11
Thanks. :p

Anyway, unlike the OP's keyboard, my buttons aren't usually that soft.

---

