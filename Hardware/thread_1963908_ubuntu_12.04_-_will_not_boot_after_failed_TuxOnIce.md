---
title: "ubuntu 12.04 - will not boot after failed TuxOnIce installation"
date: 2012-04-23
forum: Hardware
---

### Post by nicolasdiogo on 2012-04-23
hi,

i am now looking at my laptop screen that says:
could not stat the resume device file '/dev/dm-0'

i believe the problem is related to installing TuxOnIce on this machine.

the installation failed and i removed the package.

all of this using Synaptic.

but when rebooting this machine - i found the above message.

besides reinstalling the system - which is not really necessary.

how can i fix this problem.

many thanks,

Nicolas

---

### Post by nicolasdiogo on 2012-04-23
i have managed to get a message that says:

```

Begin: Running /scripts/local-premount ... resume: libgcrypt version: 1.4.5
resume: Could not stat the resume device file '/dev/dm-0

Please type in the full path name to try again
or press ENTER to boot the system:

```

i have tried running:
update-initramfs -u -k all

and i have managed to get myself fully locked out.

---

### Post by sandy8925 on 2012-04-23
looks like it's trying to resume from suspend/hibernate. are you sure it was completely powered off or did it just go into hibernate?

---

### Post by nicolasdiogo on 2012-04-23
> **sandy8925 said:**
> looks like it's trying to resume from suspend/hibernate. are you sure it was completely powered off or did it just go into hibernate?

i have definetly shut it down - even pulled the battery out for good measure.

any idea what i can?

---

### Post by LinuxFan999 on 2012-04-23
According to the TuxOnIce website, TuxOnIce has not been updated since may of 2011, so it does not support versions of Ubuntu later than 10.10 (or maybe 11.04). Ubuntu will need to be reinstalled, because it is broken. Ubuntu 12.04 will be officially released on the 26th of April.

---

### Post by nicolasdiogo on 2012-04-24
very interesting to find different views which Ubuntu version is being supported by this package.

[URL="https://launchpad.net/ubuntu/+source/tuxonice-userui"]https://launchpad.net/ubuntu/+source/tuxonice-userui
[/URL]

but that does not quite help me.

i can boot the laptop by adding at the end of the line on to the grub boot line at the boot screen:

```
noresume
```

but that is just wrong.. to do this every time

could i not just reinstall/install a kernel without the TuxOnIce patches?

thanks,

Nicolas

---

### Post by Nigel_C on 2012-04-24
Thanks for your report.

TuxOnIce is a kernel patch, so if you've removed the TuxOnIce support, that's probably just a TuxOnIce patched kernel - from the PPA? (You don't say).

In addition to the kernel patch, people usually make modifications to their initramfs, and from what you've written, it looks like your problem is in this area. Did you install other packages besides a TuxOnIce enabled kernel? Perhaps the hibernate script or uswsusp?

Regards,

Nigel
TuxOnIce maintainer

---

### Post by nicolasdiogo on 2012-04-24
Nigel,

the version i have installed is available on Ubuntu universe/misc repository

i am not using any PPA

and you are right in that i have the package uswsusp installed.

i take that i should uninstall it and rerun ```
update-initramfs
```

i presume the above package uswsusp, was installed when i installed TuxOnIce


is that right?

thanks,

---

### Post by sn0ball on 2012-04-24
Hi,

one more question: did you ever use any tuxonice PPA?

Martin

---

### Post by nicolasdiogo on 2012-04-25
never

i had this idea of testing hibernate on this laptop - which i have been upgrading Ubuntu for ages now.

and found TuxOnIce on the default repo - and tried it.

but never added any PPA for it.

---

### Post by Nigel_C on 2012-04-25
It doesn't sound like you've actually installed TuxOnIce - that would require adding the PPA. It sounds to me like you've just installed the TuxOnIce userspace part (the nice user interface), and via broken dependencies (uswsusp is unrelated to TuxOnIce) uswsusp has come along for the ride.

I would try to uninstall both the userui package and uswsusp.

Regards,

Nigel

---

### Post by nicolasdiogo on 2012-04-26
Thanks Nigel,

i have followed your suggestion and it worked correctly.

but you are better off manually updating *initramfs*
just in case!

---

### Post by sn0ball on 2012-04-29
Hi,

yes, it looks like tuxonice-userui recommends hibernate which in turn recommends uswsusp which probably breaks your setup.

However, if you want to give TuxOnIce on Ubuntu 12.04 another try, you may use the PPA:

[https://launchpad.net/~tuxonice/+archive/ppa](https://launchpad.net/~tuxonice/+archive/ppa)

Just add the PPA and install the following packages:

"tuxonice-userui linux-generic-tuxonice linux-headers-generic-tuxonice"

TuxOnIce kernels and an updated tuxonice-userui are ready now. But beware and backup! I have never tried it with encrypted swap. I would be interested if it works, though ;-)

Note that on Ubuntu 12.04 hibernate is disabled by default. Re-enable it as follows: [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

Martin

---

### Post by johnycage on 2012-05-01
> **nicolasdiogo said:**
> hi,

i am now looking at --- screen that says:
could not stat the resume device file '/dev/dm-0'
Nicolas
I'm facing similar situation. [http://ubuntuforums.org/showthread.php?t=1970589](http://ubuntuforums.org/showthread.php?t=1970589) I dont have TuxOnIce. My installed hibernate & problem arised. 
I just upgrade 
'update-manager -d' from 10.04 LTS to 12.04 Ubuntu edition. 

Did you get the solution?
Please help me at my thread too :) 
Thanks.

---

### Post by nicolasdiogo on 2012-05-02
if you are having problem to boot into the system then add into your boot line (when the boot menu shows up - press 'E') then add

```
noresume
```

you can search for this info if you are not sure what to do.

then when logged in uninstall hibernate and any other like uswsusp

and you should be fine

---

