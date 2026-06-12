---
title: "HOWTO fix ACPI/battery problems on an Acer Aspire 5050 using a custom DSDT"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by bmartin on 2007-11-11
Other DSDT files can be found [here]("http://acpi.sourceforge.net/dsdt/index.php").

[COLOR="Red"]If these instructions don't work for you, there's not much I can do to help you. You might want to try changing your BIOS version (this has been tested and works on the 1.3309 BIOS, which was the version that came with this computer).

I take no responsibility for what happens to your computer if you follow these instructions. To the best of my knowledge, there are no repercussions if the steps are followed incorrectly. The instructions are straightforward and shouldn't require any further explanation.[/COLOR]

The Acer Aspire 5050 line tends to come with a buggy ACPI table that causes the following symptoms in its laptops:
[LIST]
[*]Battery monitor program shows power as always plugged in
[*]Computer gets VERY HOT (fails to cool)
[*]Computer locks up occasionally
[/LIST]

If you're experiencing any of the following problems, this HOWTO might be for you.

[LIST=1]
[*]Open up a terminal
[*]Install Intel's IASL compiler
```
sudo aptitude update
sudo aptitude install iasl
```
[*]Download the fixed DSDT file
```
wget -O dsdt.asl http://blakecmartin.googlepages.com/acer-aspire-5050.asl
```
[*]Compile the custom DSDT (you should receive 4 warnings and 0 errors; this is normal)
```
iasl -tc dsdt.asl
```
[*]Install the custom DSDT
```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
```
[*]Update your kernel images to use the custom DSDT
```
sudo update-initramfs -c -k all
```
[/LIST]

Restart your computer. Hopefully, the problem is fixed.

[COLOR="Red"]If this breaks your system[/COLOR], execute the following commands to undo the changes:
```
sudo rm /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -c -k all
```
Then restart your computer.

---

### Post by moises.marangon on 2007-11-12
not worked for me ACER 5050-3785 bios 1.3309
Kubuntu 7.10

battery::
not present

root@moises-laptop:/home/moises# modprobe acpi
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy


Any way great tutorial.

---

### Post by cathectic on 2007-11-12
> **bmartin said:**
> The Acer Aspire 5050 line tends to come with a buggy ACPI table that causes the following symptoms in its laptops [... ]Download the fixed DSDT file

Please make sure you file a bug on the kernels bugzilla for ACPI (explaining what you had to fix, and why) - 'fixed' DSDTs are a workaround, not a long term solution (and I've been coming across other Acer laptops that also have this problem lately).

---

### Post by wmoonw on 2007-11-13
This worked for me. Thanks!

---

### Post by moises.marangon on 2007-12-11
Fallow this step 


do `cat /proc/acpi/dsdt > DSDT.dat`
disasm: 'iasl -d DSDT.dat' you should see DSDT.dsl.
edit DSDT.dsl line 3906 "Store (\_SB.PHSR (0x0D, 0x00), TJ85)" to look
"Store (\_SB.WMID.PHSR (0x0D, 0x00), TJ85)". "WMID." inserted.
'iasl -tc DSDT.dsl' to compile DSDT back.
Unselect Device Drivers->Generic Driver Options->Select only drivers...
Select Power Management->ACPI->Custom DSDT
Put DSDT.hex into Custom DSDT location field.
Copy file DSDT.hex into drivers/acpi
do make/make install/...


For Bios 3309 works great

thanks ***Alexey  Starikovskiy***

---

### Post by yakolev on 2007-12-25
I've got a 5050-3785 and whenever I do this the monitor does indeed work but... my wireless breaks! I've tried this with both ndiswrapper and the patched madwifi and whenever I boot after following the OP instructions I simply can't see any wireless networks, even though the card gets picked up fine. As soon as I remove the DSDT and make an initramfs without it everything goes back to as it was.
(puzzlement)

---

### Post by chadjohnson on 2008-01-21
This worked for me. Thanks.

---

### Post by Wagner de Queiroz on 2008-02-19
Dear Bmartin.

Very very tanks for your post. My **Acer 5050-3284** works great now :popcorn:
*[CENTER]You´re a great man! [/CENTER]*

---

### Post by gabzor on 2008-02-21
Hi guys.

I am pretty new to ubuntu and this is the first time I install Linux. I have passed already some hard time installing wifi vid card, etc but I have managed to get it fixed. Now my problem is about the Batery Icon.. I have the Acer Aspire 5050-4677 but instead of Intel i have AMD Turion 64. I have tried those steps with no result. I don't know if any of you guys have come across this issue and have fixed it, since it is very anoying to have my pc shutdown with no reason at all.

Thanks a lot
Hope you can guys help!

---

### Post by snowstep on 2008-02-24
t worked for me!
But i have another one problem!!! I upgrade memory and now I have 2x1Gb in my Aspire 5050. When i leave only 1Gb the battery status works and if there are both 2Gb of memmory it doesn't work!!! I suppose it can be fixed by editing DSDT but I don't know how! Please help me! And I flashed new BIOS 3315 but it didn't decide my problem (((!

---

### Post by gabzor on 2008-03-11
I finally corrected the problem from the aspire 5050-4677 I had just a few weeks after with a lot of researching. I finally decided to flash the new bios which is now a 1.3315 ( was 1.3309 i think) and it was released just a month ago in this year 2008 . Finally everything worked perfectly including the battery problem

I am finally quite happy with the result.

The latest bios 1.3315 [ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3315.ZIP](ftp://ftp.work.acer-euro.com/notebook/aspire_5050/bios/3315.ZIP)
Thanks and good luck

---

### Post by andré ribeiro camargo on 2008-04-18
> **yakolev said:**
> I've got a 5050-3785 and whenever I do this the monitor does indeed work but... my wireless breaks! I've tried this with both ndiswrapper and the patched madwifi and whenever I boot after following the OP instructions I simply can't see any wireless networks, even though the card gets picked up fine. As soon as I remove the DSDT and make an initramfs without it everything goes back to as it was.
(puzzlement)

I got a 5050-3284 with same behaviour: wireless stop working after loading the new DSDT.

When I removed DSDT, wireless back to working again (I'm using ndiswrapper).

Am I alone with that problem?

---

### Post by maab on 2008-05-02
Thanks. It worked for me too. Aspire 5050-5954.

---

### Post by khunphil on 2008-05-27
Hi,

The DSDT fix works for my battery indicator. No Problem. But wireless still down.
Now I tried to install Hardy and there is a big Boot problem (Soft bug / CPU stcuk for 11s...), acpi=off allowed the boot to process but no functional network after.

So I read about the acer_acpi package. Is this related to this problem ?
Is this DSDT fix "included" in Hardy (maybe my question means nothing, sorry) ?

Thanks

Philippe

---

