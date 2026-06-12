---
title: "No integrated GPU detected in Ubuntu 20.04.3 | HPE Proliant XL270d"
date: 2022-04-20
forum: Hardware
---

### Post by neaxyyy on 2022-04-20
[COLOR=#000000][FONT=&amp]Hi there,
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][FONT=&amp]I'm using Ubuntu 20.04.3 on my XL270d server, with 6 Nvidia Tesla A100 GPU installed. Then i install Nvidia 470 driver, but when i run "prime-select nvidia" it show "no integrated gpu detected".
I already reinstall my nvidia driver and ubuntu, it still show no integrated GPU detected.

What should i do?[/FONT]
[/FONT][/COLOR]
Thanks

---

### Post by Yellow Pasque on 2022-04-20
prime-select is for laptops with hybrid graphics. The XL270D has a built-in Matrox GPU to handle basic video functions. Please be more specific in what you are trying to accomplish.

---

