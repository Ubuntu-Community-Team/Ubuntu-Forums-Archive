---
title: "Slow Boot on Ubuntu 8.04"
date: 2008-10-02
forum: General Help
---

### Post by globemast on 2008-10-02
Hi all,

I have upgraded my HP Pavilion laptop to Ubuntu 8.04 a couple of months ago and i have noticed that it takes too much time to boot up. Ubuntu 7.10 (previous distr on my laptop) could boot up at least a third of the time faster than now.

Could someone point me in the right way in order to discover what is causing these delays during boot time??

Thanks in advance..

---

### Post by Calmatory on 2008-10-02
There is a utility called bootchart which might show you what takes up most of the time. Bootchart can be found via repository, and documentation can be found [here](http://www.bootchart.org/docs.html).

---

### Post by globemast on 2008-10-02
Hi...thanks for the prompt reply.

I am attaching the bootchart image below:

---

### Post by Calmatory on 2008-10-02
Actually, that shows that the machine boots fast. In 25 seconds to launching X11. However, the problem might occur after X11 is being launched, and thus it won't show up in bootchart. Sadly, I can not help any further. :|

---

### Post by globemast on 2008-10-03
Could it be something before the init phase ?? 

Thanks in advance for your help.

---

### Post by Calmatory on 2008-10-03
Well, that is also possible, but as far as I know, there is not much before init, as init is the first process to be started and it controls other process' starting.

---

### Post by globemast on 2008-10-03
Could dmesg show something??

Thanks.

---

### Post by Calmatory on 2008-10-03
Possibly. Though, at least I can not grep anything useful out of them.

Could you try installing another installation of Ubuntu to a different partition? Just create one 5GB partition to test stuff and possibly do bootchart chart if that could show something(doubt it, as your bootchart already shows 25s boot time).

Other than that, I am completely clueless. :(

---

### Post by globemast on 2008-10-03
Ok Calmatory,

Thanks for the so far help....

Maybe some of the other forum members can also provide some extra hints.

---

### Post by globemast on 2008-10-04
Hi, 

anyone which might have a comment on the above problem???  :confused::confused:

Thanks in advance.

---

