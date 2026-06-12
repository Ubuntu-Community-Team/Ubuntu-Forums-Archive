---
title: "installing Ubuntu 12.04/13.10 with HDD and mSATA SSD, and restoring from backup"
date: 2013-12-16
forum: Hardware
---

### Post by LifeEnemy on 2013-12-16
Hello all,

My last computer broke and I'm debating trying something new with the next one. However, there are a lot of pieces to it and I haven't been able to sort them all out on my own.

I just bought an Acer Aspire V5-572G-6679, which apparently has an unoccupied mSATA port inside. Upon looking inside I realized mSATA is not the same as SATA3, so I have to return the SSD I bought (but that's not particularly relevant). I've read about setting '/' and '/home' on the SSD for maximum performance, and using Symlinks for music, pictures, documents, and such. Here are my concerns:

1) Would it even be worth the hassle installing and potential trouble later? I know SSDs are supposed to be one of the best upgrade you can make for computer performance, but I've read with mSATA the SSDs might not perform to their fullest.

1b) [This]("http://www.crucial.com/upgrade/Acer-memory/Aspire+V5/Aspire+V5-572G-6679-upgrades.html") page suggests that the motherboard can handle 6gb SATA (so it shouldn't restrict SSDs?). Is there any reason this wouldn't apply to the mSATA as well?

2) I'll be restoring my data from a Deja Dup backup. It worked great last time (restored my settings and everything), but I'm worried it might not work if the folders are organized differently. If the symlinks are set up properly it shouldn't be an issue though, right?

3) Is [this ]("http://askubuntu.com/questions/252140/how-do-i-install-and-use-flashcache-bcache-to-cache-hdd-to-ssd/340059#340059")something I might have to worry about booting from an SSD, or is it something optional? I had trouble understanding the pack and packages referenced.

4) Can anyone recommend a decent mSATA SSD or brand (I bought a Samsung, but they don't make mSATA I think). I'm looking for 120 or 128gb, around $100-150 range.
*--I'm think of the [Crucial M500 120gb mSATA]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820148697"). Any reason not to get that one?*

5) the boot sector should be on the SSD, correct? Where should I put swap, and how big should it be? The comp has 6gb of ram now.
[I]--(Boot, or an UEFI sector if I stick with that mode? I think I'll just go with 'legacy' instead for simplicity. I don't plan to dual-boot.)
[/I]--Maybe I don't even need a boot sector with only one OS?

6) I just read that /home doesn't need to be on a separate partition, as Ubuntu can preserve /home even when reinstalling the OS now. Is this true? Is there any advantage to have /home on a separate partition anymore?


Sorry to ask so many questions! I've just never tried setting up a comp with multiple drives and it feels complicated. I don't want to under-prepare and end up with a problem on my hands.

Thank you so much!!

(edited to put similar questions near each other)
[I]--edit to add info
[/I]edited again now that I've tested it with just HDD for now - answered some of them myself

---

### Post by LifeEnemy on 2013-12-17
One more question: What should I mount the HDD as during installation? Should I ignore it and mount it later? I think I'd have to modify fstab to make it auto-mount on boot then, yes?

---

