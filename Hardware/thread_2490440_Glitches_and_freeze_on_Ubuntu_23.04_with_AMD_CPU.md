---
title: "Glitches and freeze on Ubuntu 23.04 with AMD CPU"
date: 2023-09-04
forum: Hardware
---

### Post by quiquoqua48 on 2023-09-04
Hi,
I've got a big problem on Ubuntu 23.04. I think could be a problem with graphic drivers, I randomly get glitches then laptop freeze and become unusable. It happen really often, about 4-5 minutes.
[IMG]https://i.postimg.cc/SN9CXdXM/photo-2023-09-04-14-24-31.jpg[/IMG]

Thanks

---

### Post by agentl074 on 2023-09-05
Yeah... that would be a GPU problem lol. When I had an AMD 5500U with Radeon graphics and it wouldn't work on kernel 5.4 with Mint, I switched to 5.13 -- snowballed everything... had to grub into 5.4 and remove 5.13, install 5.11, and that worked (kinda) until I permanently fixed it by going to Ubuntu 22.04. 

It sounds like your GPU does not like that default kernel. I wonder if it would like 5.15 LTS better?

---

