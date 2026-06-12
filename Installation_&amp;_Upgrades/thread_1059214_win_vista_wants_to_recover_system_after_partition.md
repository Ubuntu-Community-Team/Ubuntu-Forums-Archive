---
title: "win vista wants to recover system after partition"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by eskararriba on 2009-02-03
hi everyone,

I just installed ubuntu 8.10 on a sony vaio VGN-NR21S, doing a partition of the hard drive. unbuntu works perfectly, but when I tried to boot into vista, the "vaio recovery center" pops up, offering me either to recover windows, recover the hard drive, recover vaio hardware or to save my data... what am I supposed to do? 

thanks a lot, folks

---

### Post by caljohnsmith on 2009-02-03
Are you booting into Vista via the Grub menu on start up? Or how is your computer configured? I think it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Pumalite on 2009-02-03
Maybe you partitioned with Gparted instead of the Vista partitioner.

---

### Post by eskararriba on 2009-02-03
thanks to the two of you - 
but in fact, the problem was neither a grub nor a partition problem, but completely due to stupidity: of the two possibilities to boot into windows, which actually have the same name, the friend whose hard drive we recently partitioned chose the first one, which apparently is some "recovery mode"; choosing the second one resolved all our problems... 
cheers

---

