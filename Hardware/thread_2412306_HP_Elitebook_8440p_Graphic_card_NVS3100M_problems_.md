---
title: "HP Elitebook 8440p Graphic card NVS3100M problems after latest update Ubuntu 18.04"
date: 2019-02-11
forum: Hardware
---

### Post by janeku2 on 2019-02-11
Hello.
Couple of days ago my system has updated to latest one system event. My HP Elitebook 8440p has Nvidia NVS3100M (GT218M) video card and running nouveau drivers for it (I tried to install Nvidia's suggested in system but just got stuck with low resolution login and give up on them)
After this when booting to Ubuntu I stuck with a screen login problem:
System does boot up normally, but no logon screen appear at all. At one moment while booting screen just turn off and I can access login screen again if I press power buton and put to suspend mode and after that turn it on, or pressing FN+F9 (F10) adjusting brightness control at logon. Everything else works normally.
I tried to put ACPI=OFF but after that I got to low resolution login and working screen.
Any idea how to solve this login problem ?
Link to video file: [https://ufile.io/l6rd1](https://ufile.io/l6rd1)
Regards,
Petrika

---

### Post by janeku2 on 2019-02-24
Bump.

---

### Post by gary73 on 2019-08-04
MY 8540W bit the bullet with the latest Linux 5 updates as well. Gets stuck in a boot loop trying to start gui when using the nvidia drivers. Moving to the nouveau drivers allows it to come up but locks up with a pgraph_status tvl flsh error way more often to make the video usable.  Anyone have a solution Any nviida drivers for linux 5?

---

### Post by Autodave on 2019-08-05
You both could try going back one release version when you boot your machines.

---

