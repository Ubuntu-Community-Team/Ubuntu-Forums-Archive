---
title: "Optimus Laptops and Compatibility"
date: 2011-12-12
forum: Hardware
---

### Post by rba1988 on 2011-12-12
Hi

Decided to start a thread to list some of the laptops that have nvidia optimus in them and get it to run with Ubuntu (or other variants) with Bumblebee or Ironhide or other solutions that exist out there.

Basically I'm curious about the Ubuntu laptop users' answers to the following questions:

1) What kind of laptops do you use and with what NVIDIA video card? How were you able to get Optimus to work (switching the discrete card off, using bumblebee/ironhide etc.)?

2) How can you determine if your laptop and graphics card is optimus enabled?

3) Would you recommend this laptop to other Ubuntu/Linux users? <-- probably useful for people running wine (like me hehe) or developers who are working on CUDA (like me again. hehe).

Let me start:

I recently acquired two laptops for testing:

Acer 4750g 
- Labeled Gt540m (2gb of RAM) for its video card. But when running "lspci | grep VGA" it displays both the Intel GPU and the NVIDIA but is labeled as GT555. 
- nvidia-current package breaks it
- Installed bumblebee (the forked version) and now I can run wine programs (actually I just wanted to play Starcraft 2 on it and it works with all low settings. pretty smooth although I did have 4gb of ram in it)
- I would recommend it if you don't mind the heat it produces

Asus k43SV
- Also labeled gt540m for its video card. Running "lspci | grep VGA" displays only the NVIDIA card even if its advertised as Optimus enabled. What's up with that? Anyway, I'm just glad it doesn't have optimus in it when running Ubuntu.
- A good laptop but only has 1GB of dedicated memory for its video card. Would recommend it (primarily because it has no optimus). HAven't tried SC2 with it though.

---

