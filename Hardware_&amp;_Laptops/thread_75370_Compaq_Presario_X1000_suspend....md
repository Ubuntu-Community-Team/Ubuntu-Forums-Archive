---
title: "Compaq Presario X1000 suspend..."
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by ScatterBrain on 2005-10-13
Has anyone been able to successfully suspend and resume this model laptop?

With Hoary (and now Breezy) I can suspend the machine, but it never wakes back up.  Or maybe it tries to wake back up (ie, the power light and things come back on), but it never comes all the way up.  I never hear the hard drive spin back up, see the USB devices come back alive, nor does my LCD panel power back up.

I know this may not be possible, *BUT* if it can be done, I'd like to know how.

---

### Post by John.Michael.Kane on 2005-10-13
try here [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles)

---

### Post by strawman on 2005-10-13
try adding the options "resume=/dev/hdaX" to your kernel options in your grub file with "X" being the location of swap and adding "acpi=s3_sleep".  i think this is what enabled me to get suspend to ram working on my hp nc8000.

---

### Post by ScatterBrain on 2005-10-14
[QUOTE=SD-Plissken]try here [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=suspend&titlesearch=Titles)[/QUOTE]

I did try some of the things listed on the links that you gave - none of them helped. :(   The machine would suspend, but it would not wake back up.

For the record, here is what I tried from those links:

In **/etc/default/acpi-support**, I changed several lines so that they now look like this:

```
ACPI_SLEEP=true
[...]
SAVE_VBE_STATE=false
[...]
POST_VIDEO=false
[...]
USE_DPMS=false
```

I still have these lines in place, as they just make sense to me.  But, in addition to those changes I tried adding "nolapic" to the kernel line in **/boot/grub/menu.lst**.  I booted with that option in one time, it didn't work, so I removed it.

[QUOTE=strawman]try adding the options "resume=/dev/hdaX" to your kernel options in your grub file with "X" being the location of swap and adding "acpi=s3_sleep".[/QUOTE]

I tried that, no joy. :( 

Can you post your **/etc/default/acpi-support** file?  Maybe there's something in there that I missed.  Also, are you using the **fglrx** drivers?  I've tried suspend with and without the fglrx drivers and it didn't make a difference, I'm just curious.

---

### Post by ScatterBrain on 2005-10-14
UPDATE:

I have successfully been able to suspend and resume my laptop. \\:D/   That's the good news.  The bad news is that I can only suspend/resume once between reboots. :-k   If I suspend twice, then the machine will fail to resume on the second attempt.

What seems to have done the trick is the removal of one my normal settings on the kernel line: **vga=791**.  I like using a hi-res console framebuffer.  If I leave the option on the kernel line, then I can't even suspend/resume once successfully.  I got a clue about this from this post in this forum: [http://ubuntuforums.org/showthread.php?t=75028]("http://ubuntuforums.org/showthread.php?t=75028")

So, now the big question is how do I make it suspend/resume every time I try?  ](*,)

---

### Post by shadowman on 2005-11-05
FWIW I was having similar problems on a Toshiba Tecra.  Prior to posting this I hibernated my machine three times using ```
System>Log Out>Hibernate
``` after making the following changes to menu.lst

before:
```
# nonaltoptions=quiet splash
```
after:
```
# nonaltoptions=quiet
```

and before:
```
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
```
after:
```
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet acpi=noirq resume=/dev/sda5
```

where /dev/hda5 is my swap space.  My ipw2200 NIC kept working as well.

Caveat:  The boot isn't as pretty without the Ubuntu splash screen but at least it's functional with hibernate and wireless working like I need them to.

hth

John

---

