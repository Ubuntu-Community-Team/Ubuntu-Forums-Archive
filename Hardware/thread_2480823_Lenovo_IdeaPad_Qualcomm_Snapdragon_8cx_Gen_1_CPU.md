---
title: "Lenovo IdeaPad: Qualcomm Snapdragon 8cx Gen 1 CPU"
date: 2022-11-11
forum: Hardware
---

### Post by pachainti on 2022-11-11
Hi,
I would like to buy this lenovo IdeaPad 5G 14Q8X05 notebook which runs a [Qualcomm Snapdragon 8cx Gen 2 SoC]("https://wikiless.org/wiki/List_of_Qualcomm_Snapdragon_processors?lang=en#Snapdragon_8cx_Compute_Platforms") which should be supported by linux [kernel 6.1]("https://lore.kernel.org/linux-arm-kernel/20220916124214.3881948-1-vkoul@kernel.org/") (not the Gen3 recently added to linux [kernel 6]("https://www.omgubuntu.co.uk/2022/10/linux-kernel-6-released-new-features")). How is the support for ubuntu 22.04 LTS and 22.10 using kernel 5.15 and 5.19 respectively? Do all applications work given the different architecture?
The notebook is intended for basic functions such as browsing, reading, streaming video. I'm interested in long battery life, not performance. What do you think?
Thanks

---

### Post by pachainti on 2022-11-27
Hi,
I investigated further and found some positive information about the [Snapdragon 8cx SoC]("https://en.wikipedia.org/wiki/List_of_Qualcomm_Snapdragon_processors#Snapdragon_8cx_Compute_Platforms"):

[LIST]
[*][Gen 1 aka SC8180X]("https://lore.kernel.org/linux-arm-kernel/20220916124214.3881948-1-vkoul@kernel.org/")
[*][Gen 2 aka SC8180XP]("https://lore.kernel.org/linux-arm-kernel/20220916124214.3881948-1-vkoul@kernel.org/")
[*][Gen 3 aka SC8280]("https://lore.kernel.org/linux-arm-kernel/CAK8P3a1DVcc=AV29AJJxMzBVoU-grFaNet0ndxPgPFvpK-ZANQ@mail.gmail.com/T/")
[/LIST]

The Gen 1 and Gen 3 appear here to be supported by the linux kernel 6.1 and 5.19 respectively.

---

