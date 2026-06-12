---
title: "ACPI problem on Asus m6r"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by eagle331 on 2005-07-22
Hey everyone, so this is my problem:

At booting I encounter this problem:

-> When loading ACPI modules, it never completes (no [ok] :p), but X server starts and I can work normally, although acpid doesn't start and I get 2 errormessages on startup: 
                          "Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running."
             This results in: no battery status, no fn functions ...

My laptop:

Asus m6r centrino 1.6 ghz, bios version is the newest (I updated it yesterday, because it was adviced, but it didn't solve anything)

Conclusion:
acpid doesn't start, manually starting doesnt do anything i guess
changing acpi=force etc in grub doesnt work eiter.
I'm curtainly not the most advanced linux user, I must admit, so it is possible I overlooked a thing or two (look at my state: "newbie brew ...", and that prooves it) :p

If anyone can help me, I'd really appreciate it!

Something important I have to add:
When installing ubuntu, it comes to a point where it is setting up acpi en acpid (1.0.4-1ubuntu4) and then it holds on "loading acpi modules", so I have to make it continue manually (long live ctrl-C) (this was when the problem first occured ...)

---

### Post by eagle331 on 2005-07-22
While installing ubuntu, there also seams to be a problem with 'setting up pax' (powermanagment) and 'powernowd' (but is says it is related to acpi, so that is obvious)

The error with pax: "powermanagement-interface depends on acpi-support (>=0.17); however: Package acpi-support is not configured yet"

---

### Post by eagle331 on 2005-07-22
I read something about acpi4asus patch for the kernel, but I never recompiled a kernel before.

Does anybody know if this might work ? If so, does anyone know a good howto for compiling a kernel ? cause I don't want to mess up my system, even though that would the case for the 25th time or so :)

---

### Post by luca_linux on 2005-07-22
acpi4asus is already included in the kernel.
I've got an Asus M6N laptop and acpi works.
First of all you have to update your bios to the latest version available, then you have to compile your customized DSDT to get ACPI to work.

---

### Post by eagle331 on 2005-07-22
Never heard of DSDT before, but I am looking in to some docs about it. Currently I don't have time to do this, but I will surely give the results as soon as I can !

... Unless anyone can tell me how I can compile a custumized DSDT ? That would be a big help :)

---

### Post by luca_linux on 2005-07-23
Here are the main steps:
1) Install the flex-old package with Synaptic or apt and download Intel IASL utility from [this page](http://developer.intel.com/technology/iapc/acpi/downloads.htm)
2) Compile it as reported in the page linked above
3) cat /proc/acpi/dsdt > dsdt.dat
4) iasl -d dsdt.dat
5) iasl dsdt.dsl
6) You'll get some errors during the previous step (that was the compilation of dsdt.dsl in dsdt.aml)
7) Correct the errors manually
8) Save the edits
9) iasl dsdt.dsl
10) Follow the instructions reported here to loading the custom DSDT: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)
That's all

---

### Post by hayalci on 2006-06-18
Well, I have a ASUS M&R laptop (M6000R) The ACPI support was a problem since I bought it. If you wait, next kernel update will include the necessary solution probably. If you cannot wait, and are not afraid of compiling kernels and patching  files, read on.

There are two important bugs for the problem;
[http://bugme.osdl.org/show_bug.cgi?id=4150](http://bugme.osdl.org/show_bug.cgi?id=4150)
[http://bugme.osdl.org/show_bug.cgi?id=6111](http://bugme.osdl.org/show_bug.cgi?id=6111)

The  comment #31 in the second bug contains a (small) patch that solves the problem and make acpi work like a charm ( The patch is here: [http://bugme.osdl.org/attachment.cgi?id=7513&action=view](http://bugme.osdl.org/attachment.cgi?id=7513&action=view)). 

I downloaded a vanilla 2.6.17 kernel from kernel.org, configured and tested it so that the config settings are right for my hardware [[ I never managed to compile working kernels on the first try :) ]] Then I applied the patch and recompiled, the acpi problems are gone and now asus-acpi module (acpi4asus.sf.net , also compiled from scratch) works without problems. I use the "patch" command with filename as the parameter and patch contents pasted on command prompt followed by a ctrl+d. do not forget to add acpi-asus into /etc/modules file.

---

### Post by smylie on 2006-07-10
> **hayalci said:**
> 
I downloaded a vanilla 2.6.17 kernel from kernel.org, configured and tested it so that the config settings are right for my hardware [[ I never managed to compile working kernels on the first try :) ]] Then I applied the patch and recompiled, the acpi problems are gone and now asus-acpi module (acpi4asus.sf.net , also compiled from scratch) works without problems. 

Has this had any effect on suspend/hibernate? I've been trying to get this going with my m6r, but although it suspends, it never wakes up correctly. . .

---

### Post by hayalci on 2006-07-19
Well, actually I didn't try the suspend/hibernate. But the bug reports may mention them also.

---

### Post by norman_h on 2006-07-22
> **smylie said:**
> Has this had any effect on suspend/hibernate? I've been trying to get this going with my m6r, but although it suspends, it never wakes up correctly. . .

I think hibernate/resume can be activated on a vanilla dapper 6.06 install by adding the [COLOR="Red"]resume=/dev/hda<your_swap_partition>[/COLOR] parameter to the "kernel" line in your [COLOR="Red"]/boot/grub/menu.1st[/COLOR] file.  I'm still hacking away at getting acpi to read battery states.  I can do it with a new kernel, but my  wireless and cpu throttling doesn't work with the new kernel... yet.

The relevent section in my [COLOR="Red"]/boot/grub/menu.1st[/COLOR] file is as follows:

```
title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda4 ro quiet splash resume=/dev/hda3
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

```

EDIT: this should work, however I have done a little hacking around on my system which has made it non-vanilla 6.06 so your results may vary...  I'd love to hear from anyone who tries this.

---

### Post by norman_h on 2006-07-22
> **hayalci said:**
> There are two important bugs for the problem;
[http://bugme.osdl.org/show_bug.cgi?id=4150](http://bugme.osdl.org/show_bug.cgi?id=4150)
[http://bugme.osdl.org/show_bug.cgi?id=6111](http://bugme.osdl.org/show_bug.cgi?id=6111)
It appears that these fixes will be included with the 2.6.18 kernel when it is released.  Apparently the fixes shipped with 2.6.17-git9 

This should fix all the problems with the M6R.  :cool:  Just gotta wait for the ubuntu team to release the new kernel.  I'm not sure if it is possible to request that the patch be applied to the next kernel upgrade or not, I'm also not sure how I would request this.  I have tested the patch at bugme #6111 on kernel 2.6.17.6 and it fixes my battery and [w,m]lan light problems, it may also fix the extra button problems, but I haven't tried.

---

