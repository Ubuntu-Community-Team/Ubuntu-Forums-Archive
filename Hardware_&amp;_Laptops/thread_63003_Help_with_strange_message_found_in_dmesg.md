---
title: "Help with strange message found in dmesg"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by rickympl on 2005-09-06
Help, a few mnutes after booting up I type dmesg in a konsole and I get the following lines:


 Buffer I/O error on device hda, logical block 2
hda: tray open
end_request: I/O error, dev hda, sector 12
........ (continues with different sector and block)


I can't figger any of this out since my hda is a dvd recorder, my hard drives are connected to a maxtor 133 adapter and they start off as hde.

can anyone make sense of this?  I really appreciate it.

Thanks

---

### Post by s_p_a_r_k_y on 2005-09-07
well in general input output errors (i/o) aren't good, however it could mean a scratched CD or one that wasn't burnt well. At first I thought it was your harddrive until I saw that your hard drivewas hde and then it made sense why the tray had been opened. 

Do you see this error with all dvd/cds or just a select few?

---

### Post by rickympl on 2005-09-07
[QUOTE=s_p_a_r_k_y]well in general input output errors (i/o) aren't good, however it could mean a scratched CD or one that wasn't burnt well. At first I thought it was your harddrive until I saw that your hard drivewas hde and then it made sense why the tray had been opened. 

Do you see this error with all dvd/cds or just a select few?[/QUOTE]


The thing is that there is no cd in the drive to begin with. And the dmesg also shows that it does this with fd0 as well, and there is no floppy inserted.

I know its strange. that's why I posted in the forum.  Does this mean that there is a prog or service trying to access the dvd drive and the floppy?

Thanks.
i'm using edonkeyclc 1.3 and FAH502-Linux.exe (protein folding cpu share program)

---

