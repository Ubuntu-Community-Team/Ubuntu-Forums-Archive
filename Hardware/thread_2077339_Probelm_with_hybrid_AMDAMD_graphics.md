---
title: "Probelm with hybrid AMD/AMD graphics"
date: 2012-10-28
forum: Hardware
---

### Post by marcin1147 on 2012-10-28
Hi!
I have a HP G62-a35ew with hybrid ATI HD4250/HD5470 GPU. I can't use any fglrx driver above 12.4 version because stupid AMD has dropped HD4250 series support and I have "Low graphics mode" alert after reboot. I can use fglrx legacy but then i can't turn on my high-power HD5000 GPU.

I DON'T WANT TO USE HD4250 BUT HD5470... But I can't. What should I do? AMD support isn't responding to my emails, you are my only hope. Maybe there is any way to... blacklist my integrated GPU?

BTW. I can't turn off my integrated GPU in BIOS...

Please, help me! :)

---

### Post by RLDr on 2012-10-28
I have successfully activated the dual graphics (Intel HD + AMD ATI) of my Dell Vostro 3550 Laptop running Ubuntu 12.04 LTS after a long time of trial & error.:guitar:

Please Read Carefully:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by marcin1147 on 2012-10-28
Unfortunately, this method is not working with my system.

---

### Post by RLDr on 2012-10-28
> **marcin1147 said:**
> Unfortunately, this method is not working with my system.
Hmmm.... Seems bit difficult for you....
Let this driver installation process hand over to built-in "Additional Drivers".

1.
Save a backup copy of xorg.conf in case this process doesn't work (to avoid reinstallation of ubuntu).

$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

2.
You need an active internet connection.

3.
You can search for "Additional Drivers" in the Ubuntu Dash Home (Unity).
Or click on wheel button located on top right hand corner of desktop "System Settings" => "Hardware" => "Additional Drivers".
A window will show you up the available drivers applicable for your hardware.
Select "ATI/AMD proprietary FGLRX graphics driver".
Now click on "Activate".
After downloading it will install appropriate driver for your graphics system.

4.
Restart your system.

5.
Now open terminal and run:

$sudo aticonfig --initial -f

6.
Restart your system again.

7.
Search for "AMD" in Ubuntu unity dash home.

8.
Open "AMD Catalyst Control Center".
If you want to change default settings open
"AMD Catalyst Control Center (Administrative)".

9.
EnJoY.:guitar:

---

### Post by Miktor on 2012-10-28
There's currently an issue with ati hybrid graphics cards. It's probably going to be solved in the coming week or so, but I'm not sure at all.

---

### Post by marcin1147 on 2012-10-28
> **RisingMan said:**
> Hmmm.... Seems bit difficult for you....
Let this driver installation process hand over to built-in "Additional Drivers".

1.
Save a backup copy of xorg.conf in case this process doesn't work (to avoid reinstallation of ubuntu).

$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

2.
You need an active internet connection.

3.
You can search for "Additional Drivers" in the Ubuntu Dash Home (Unity).
Or click on wheel button located on top right hand corner of desktop "System Settings" => "Hardware" => "Additional Drivers".
A window will show you up the available drivers applicable for your hardware.
Select "ATI/AMD proprietary FGLRX graphics driver".
Now click on "Activate".
After downloading it will install appropriate driver for your graphics system.

4.
Restart your system.

5.
Now open terminal and run:

$sudo aticonfig --initial -f

6.
Restart your system again.

7.
Search for "AMD" in Ubuntu unity dash home.

8.
Open "AMD Catalyst Control Center".
If you want to change default settings open
"AMD Catalyst Control Center (Administrative)".

9.
EnJoY.:guitar:
Unfortunately, this method is not working with my system xD

> **Miktor said:**
> There's currently an issue with ati hybrid graphics cards. It's probably going to be solved in the coming week or so, but I'm not sure at all.
Wow! Awesome news! What's the source of this news?

---

### Post by RLDr on 2012-10-29
> **marcin1147 said:**
> Unfortunately, this method is not working with my system xD 

We don't try to learn something new until we stumbled upon something strange difficulties. I solved my dual-graphics-driver related issues after lots of study.

So don't give up.... keep patience.... keep searching for solution....

And when you done, please return back & leave here your process of solving.

[Please mark this thread solved, when you resolve your problem by a method posted here]

---

