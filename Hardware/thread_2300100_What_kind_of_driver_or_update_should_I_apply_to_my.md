---
title: "What kind of driver or update should I apply to my gtx980m laptop"
date: 2015-10-23
forum: Hardware
---

### Post by Sorawit_Kongnurat on 2015-10-23
This laptop is a Sager and it come with a gtx980m and intel graphic card which display out the images. Should I install a bumblebee or is it better to just install the driver using this set of code :
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update && sudo apt-get install nvidia-355

---

### Post by Bashing-om on 2015-10-23
Sorawit_Kongnurat; Hello;

Until one knows better ,, and the emphasis is on 'know' one should always use our software repository .
What release are you running ?
Nvidia recommends the 352 version driver . That driver is available for 14.04 + in the repository, and also the control tool ' nvidia-prime' will be installed when the driver is installed.

Is there a reason that the open source driver does not meet your expectation ?
What actions have you taken that might at this time preclude/interfere with installing the proprietary driver ?

[INDENT][INDENT]as you want
[INDENT][INDENT][INDENT]we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Sorawit_Kongnurat on 2015-10-23
where can I download that 352 driver ?

---

### Post by Bashing-om on 2015-10-23
Sorawit_Kongnurat; Hey :

As the system recommends the 346 driver, Install it as indicated in the "Additional Drivers" utility .

Won't hurt a thing to 
[INDENT][INDENT]try it and see
[/INDENT][/INDENT]

---

### Post by blm-ubunet on 2015-10-23
346.16 (beta) Nov2014 added support for GTX980m.

---

### Post by myromance123 on 2015-10-24
Whether or not you need bumblebee/NVIDIA Prime depends on whether this laptop treats your graphics card as an Optimus card or a discrete graphics card.

If you can confirm it uses Optimus, then you have no choice but to use bumblebee or Nvidia Prime (Prime can be found from inside the Ubuntu Software Center).

If it treats the card like a Desktop discrete graphics card, then you are safe to install the PPA you listed or even use the Nvidia drivers available in the official Ubuntu repositories (search for 'Additional Drivers' in the Ubuntu Dash).

---

### Post by Sorawit_Kongnurat on 2015-10-24
Thank you I think I got my answer

---

### Post by Bashing-om on 2015-10-24
Sorawit_Kongnurat; Great .

You have marked the thread 'solved' .
Is that resolution the installation of the 346 version graphic's driver ?

[INDENT][INDENT]posterity, needs to know
[/INDENT][/INDENT]

---

### Post by Sorawit_Kongnurat on 2015-10-25
Oh I installed the 346 version but there was no setting to change the graphic driver in that version. As a result I installed driver 355.11 which seem to have one from a ppa.

---

### Post by Bashing-om on 2015-10-25
Sorawit_Kongnurat; Great;

Can not beat what works.

I will keep this under advisement, next time I meet such a situation.

[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

