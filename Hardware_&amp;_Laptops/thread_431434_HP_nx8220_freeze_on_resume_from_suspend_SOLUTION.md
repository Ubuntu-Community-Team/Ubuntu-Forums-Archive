---
title: "HP nx8220 freeze on resume from suspend SOLUTION"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by Lux1983 on 2007-05-03
Hello,

Here's my solution for freezing while resuming from suspend state for Feisty.

My system is HP nx8220 with Mobility Radeon X600.

Open terminal and type: sudo gedit /etc/default/acpi-support

Input root password

change following line from true to false:

POST_VIDEO=true

you should modify to

POST_VIDEO=false.

Hopefully this works on other laptops, too. This is probably issue with ATI graphics cards.


Best regards,

Tomislav

---

### Post by KillerBob-it on 2007-05-03
it didn't work for me on HPnx9105

---

### Post by apollo77 on 2007-06-11
Hi

I have an HP nx8220 laptop and does not resume from suspend..
What kind of version Ubuntu version are you using?

Can you post all your acpi-support  file here please?
A

---

