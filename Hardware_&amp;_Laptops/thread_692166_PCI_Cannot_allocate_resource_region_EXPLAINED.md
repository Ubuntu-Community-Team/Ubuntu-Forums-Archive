---
title: "PCI: Cannot allocate resource region EXPLAINED"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by aBitLater on 2008-02-09
Hello,

I've seen a lot of posts about the "PCI cannot allocate resource" message at boot startup, and most have endless repetitive *"Me too, I have this error too"* replies. 

I found this explanation at bugzilla.kernel.org.  Hopefully it helps someone.

[http://bugzilla.kernel.org/show_bug.cgi?id=9861]("http://bugzilla.kernel.org/show_bug.cgi?id=9861")

>  ------- Comment  #14 From ykzhao  2008-02-04 00:39:44   -------

Thanks for the info.
    From the info in comment #3, #12 and #13 OS will report the following debug
message: 
    > PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
    > PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0

   The above debug message is caused by bios configuration . The details are
listed in the following:
   a. The PCI bridge (1c.0 and 1.c3) is programmed by BIOS. For 1c.0 : The IO
resource ranges from 0 to 0xfff. Memory resource ranges from 0 to 0xfffff. For
1c.3: there is no IO resource defintion and memory resource ranges from
d0000000 to d00fffff. 
   b. The memory&IO resource will be reserved by OS in the phase of PCI
initialization. If the resource can't be reserved , OS will report the error
message. For example: the IO resource (0-0xfff) is reserved for 1c.0 bridge;but
unfortunately the IO resource(0-0xfff) is used by other devices(RTC timer; DMA;
8259). So the OS will report the above error essage.

   Of course the above message won't break anything because there is no PCI
device behind the PCI bridge (1c.0). The message is confusing. 

   Since the message is caused by BIOS configuration and won't break anything,
the bug will be rejected. 

   Thanks for the info.



---

### Post by Symbolis on 2008-02-18
That is...unfortunate.

The PCI issue causes a lengthy boot time on my laptop. Back to Windows, I guess, til I see if the issue's any better under 8.04(I doubt it).

Just for the record: This wasn't an issue with 7.06, for me. So, if anyone's having this issue you might want to stick to 7.06.

---

### Post by roaldz on 2008-02-18
> **Symbolis said:**
> That is...unfortunate.

The PCI issue causes a lengthy boot time on my laptop. Back to Windows, I guess, til I see if the issue's any better under 8.04(I doubt it).

Just for the record: This wasn't an issue with 7.06, for me. So, if anyone's having this issue you might want to stick to 7.06.

If you´d read more about ubuntu, you´d have known that there is no 7.06 version. These messages don´t cause bootup delays, so that´s probably another thing. Install bootchart and check /var/log/bootchart for logs.

---

### Post by Symbolis on 2008-02-18
> If you´d read more about ubuntu, you´d have known that there is no 7.06 version..

Sorry. 7.04. Didn't feel like reaching back to check the disc sleeve to make certain I had the exact version number.


> These messages don´t cause bootup delays, so that´s probably another thing. Install bootchart and check /var/log/bootchart for logs.

Alrighty.

Laptop's running Kubuntu(7.10) and Windows XP Pro, for the record.(Windows just so I can play City of Heroes/Villains...well, once this boot issue is figured out)

Bootchart output is attached.(First time attaching a file on here. Quite like the attachment manager!)

Any ideas about what might be causing the delay?

If you prefer, I can put Ubuntu back on and try again. :)

---

### Post by roaldz on 2008-02-18
> **Symbolis said:**
> Sorry. 7.04. Didn't feel like reaching back to check the disc sleeve to make certain I had the exact version number.




Alrighty.

Laptop's running Kubuntu(7.10) and Windows XP Pro, for the record.(Windows just so I can play City of Heroes/Villains...well, once this boot issue is figured out)

Bootchart output is attached.(First time attaching a file on here. Quite like the attachment manager!)

Any ideas about what might be causing the delay?

If you prefer, I can put Ubuntu back on and try again. :)

Looks like that Usplash problem.

The easy way:
```
gksu gedit /boot/grub/menu.lst
```

Find your kernel command line.

Looks someting like this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6247b01f-c131-4cd0-8491-2407fa491503 ro **quiet splash**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
Remove ¨quiet splash¨ at the end of the ¨kernel¨ line.

Save the file. The next time you boot, you´ll see verbose boot messages, no splash screen. I bet it´ll be faster, but also somekind of ugly.

The good way:


Hope it helped, if so, please thank me.

Roald

---

### Post by aBitLater on 2008-02-18
you can add a vga=xxx to the end of your kernel line in grub if the boot output is wild all over the screen.

xxx = a number for your resolution and color depth.  you can check a chart here:

[http://en.opensuse.org/SDB:Setting_up_Unsupported_Graphics_Cards_with_the_Framebuffer_Device_(GRUB)]("http://en.opensuse.org/SDB:Setting_up_Unsupported_Graphics_Cards_with_the_Framebuffer_Device_(GRUB)")

---

### Post by Symbolis on 2008-02-18
Well, I guess that's something.

Still slower than I'd like, but it'll do.

Now, after all that fun...back on Windows with me for some City of Heroes with my fiancee!

---

### Post by roaldz on 2008-02-18
> **Symbolis said:**
> Well, I guess that's something.

Still slower than I'd like, but it'll do.

Now, after all that fun...back on Windows with me for some City of Heroes with my fiancee!

If it´s still not fast enough, you can check another bootchart and see what´s to speed up:)
Bootchart reports a boot time of 21 sec´s for me..

This is on a laptop.

---

### Post by aBitLater on 2008-02-18
you can check for other problems that have output to your console at startup with the message log.

from a terminal, 

sudo dmesg | grep -i "pci"

that searches for any messages about pci.  Replace with any term that you might think you should investigate.

Alternately, you can use the gnome system logs for a nice GUI of the logs.  If not in your System / Administration menu, go to Synaptic and search and install gnome-system-log

---

