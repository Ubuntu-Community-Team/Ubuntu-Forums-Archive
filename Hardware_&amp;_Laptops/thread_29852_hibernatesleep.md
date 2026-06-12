---
title: "hibernate/sleep"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by tara_zw on 2005-04-26
Hi 

I'm still a newbie! I've got an NEC versa P440. Hibernate and sleep turn off the screen but neither will un-hibernate or un-sleep unless I reboot......really painful as the hibernate and sleep functions are so useful to laptop users.

I searched the forums and it seems there's an issue with the swap command and/or the resume setting.

I need detailed advice if I'm to use the terminal etc....

Please help!

;-)

---

### Post by pardasaniman on 2005-04-26
For the hibernate, you need to add resume=/dev/hdaX  to your kernel boot parameters <-- Read someone elses post, if you choose the wrong X, you could bork a partition.

For sleeping, that sounds like an ACPI issue.  I reccomend trying out apm instead of ACPI.  I used to be unable to wake-up from ACPI, but then APM could do it fine.

You'll have to change your kernel boot parameters to do:  acpi=off apm=on 

Then to sleep type, 
sudo apm -s

If you need more detailed instructions let us know

--Utsav Pardasani

---

### Post by tara_zw on 2005-04-26
Thanks! Please may I have more detailed instructions....serious newbie. But can follow terminal and synaptic and settings instructions :-)

Thanks again.

Tara xox

---

### Post by awaldram on 2005-04-27
for your hibernate problem 

yes I think it is an ACPI issue 

I had the same problem machine wouldn't unhibernate (or rather it would but the screen stayed black)

to fix this

 my solution was to add acpi_sleep=s3_bios to kernel options

this worked like a charm

---

