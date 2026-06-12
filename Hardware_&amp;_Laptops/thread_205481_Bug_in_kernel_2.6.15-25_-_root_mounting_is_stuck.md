---
title: "Bug in kernel 2.6.15-25 - root mounting is stuck"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by Richard Roy on 2006-06-28
After updating kernel 2.6.15-23 to 2.6.15-25, when the computer boots, the system is stuck for several minuts on "mounting root filesystems". I have a laptop IBM thinkpad x60s. The problem did not exist before the last upgrade.

I posted a bug about that:
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/50313](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/50313)

but it is not being taken care of for several weeks.
I heard other people have this bug.
This is a serious bug, and I want the community to help me. If it will not be fixed, I'll have to leave ubuntu on the next upgrade, and it's a pitty, since I really like this distro.
Please tell what should I do to pay the attention of the developers of ubuntu to fix this serious bug.

Many thanks.

---

### Post by FenrisAbraxas on 2006-06-28
Did you used the same .config as in the other kernel you were using? did you compiled the kernel manually? Did you tried another kernel already? hmmm probably is something with the SCSI support or something :)

---

### Post by Richard Roy on 2006-06-28
[QUOTE=FenrisAbraxas]Did you used the same .config as in the other kernel you were using? did you compiled the kernel manually? Did you tried another kernel already? hmmm probably is something with the SCSI support or something :)[/QUOTE]

I am using the regular apt-get software to update everything (using synaptic). I am not compiling kernel manually. I am using Ubuntu packages.

---

### Post by Hellkeepa on 2006-06-28
HELLo!

Got the same problem, on an Amilo Pro 2040 from Fujitsu Siemens. Intel chipsert, and an Centrino M 1.6 GHz prosessor.
ALT + F1 doesn't give any output either, it just hangs after "uncompresing kernel... OK"; Never saw any "Loading Linux", so I thought it had locked up the first time. Second time I had to do some stuff, and when I got back 5 minutes later I noticed that it had booted anyway.

Oh, yeah, almost forgot: I updated from Breezy doing a manual apt-get installation, and used nothing of my own configure files. Updated the kernel and everything that was possible to update, to ensure I had as few troubles as possible.

Hopefully not a serious issue, but rather annoying still. Especially when you're in a hurry, or running on battery power.

*Edit, added:*
Just tried the -386 kernel, and it does not have this issue. In fact, it was rather snappy at getting up and running.

Happy codin'!

---

### Post by thefrug on 2006-06-29
I have had the same problem with my Thinkpad X60 since the upgrade to 2.6.15-25. It is extremely frustrating, and I was sort of looking for some way to fix it. I didn't at first realize it was related to that upgrade, and since I needed to reinstall anyway, I did, but the problem was still there.

Has anyone come up with any solutions?

---

### Post by deldar on 2006-06-29
perhaps you can try to add acpi=off to kernel options
(worked for me)

---

### Post by Richard Roy on 2006-06-30
[QUOTE=deldar]perhaps you can try to add acpi=off to kernel options
(worked for me)[/QUOTE]

This is not a solution. You need the acpi support for sleeping, etc.

---

### Post by Richard Roy on 2006-07-02
someone please?

---

### Post by saldie on 2006-07-02
I have the same problem on my Hp core duo.
When the kernel would load(very rare) I would have odd problems like, no sound and the laptop suddenly turning off.
The fix for me was to install kernel 2.6.15-23 686.
Everything is fine now, hopefully this will be fixed.

---

### Post by FenrisAbraxas on 2006-07-04
Then try to boot in recovery mode :P.

I usually compile my kernels :S so dont know what happened :(

---

### Post by geos2 on 2006-07-20
You can fix the problem on the x60s by going into the BIOS and changing the SATA mode from AHCI to "Compatibility"

Has anyone with an x60s had severe problems with 2.6.15-25? It cause my x60s to become so slow as to be unusable...

---

### Post by iimre on 2006-07-22
I've got the same problem on my HP-Compaq nc6000.
It doesn't happen (for me) if I run from battery at boot time. I know it is not a solution, but may help.
Looking forward any real fix to this problem.

---

### Post by lewmnik on 2006-07-22
Last usable Kernel for our laptops (we got Dells and LGs) was 2.6.15-22 after that I haven't been able to use the -686 kernels at all, I am currently using 2.6.15.-26-386[-( ... first the -686 were burning the CPU on 100% and now they won't boot with acpi on;  way to go Kernel Team! I hope someone will try to fix this one.

EDIT:

Read this [POST]("http://www.ubuntuforums.org/showpost.php?p=1288233&postcount=3") I guess he knows why the -686 is not working!

---

