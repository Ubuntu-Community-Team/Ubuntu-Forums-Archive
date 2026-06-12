---
title: "Can't choose a different drive for grub installation?"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by Azlum on 2009-03-13
Hey guys...

I've been trying to install various builds of Kubuntu 9.04 and I keep running into the same issue....

I'm installing onto a partition on SDB and I am getting through the whole installer just fine(I'm not new to linux by the way, I'm just not an expert)... until I get to the end where you can click "Advanced" and choose the location to install Grub to....

When I click advanced, the only choice for installing grub is to SDB... There is nothing else in the combo box and it wont let me type in my own choice.  If I leave it set to SDB, grub will fail to install at the end and I will be left with no way to boot linux.

When installing 8.10 or earlier, when I click Advanced it will let me type in my own choice for the grub install, and since I'm installing linux onto SDB, I would type (hd1) and grub would install just fine...

Why can't I choose something other than SDB when I'm installing 9.04???  How can I get around this issue?  To be frank I have looked at guides for installing grub manually before and it's way over my head.

Thanks!!!

---

### Post by meierfra. on 2009-03-14
> When I click advanced, the only choice for installing grub is to SDB... There is nothing else in the combo box and it wont let me type in my own choice

Did you check the LiveCD for defects?

> If I leave it set to SDB, grub will fail to install at the end and I will be left with no way to boot linux.

What error messages do you get?

It might be possible to install Grub manually from the LiveCD. 
After you installed ubuntu, how about downloading the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

