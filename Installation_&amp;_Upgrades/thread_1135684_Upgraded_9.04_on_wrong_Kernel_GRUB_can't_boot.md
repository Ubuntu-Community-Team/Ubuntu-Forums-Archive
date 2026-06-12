---
title: "Upgraded 9.04 on wrong Kernel? GRUB can't boot"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Gibbs on 2009-04-24
I had issues with the latest kernel in Ibex (mainly graphics related) so have been using 2.6.27-7-generic. I upgraded to 9.04 forgetting I was on an older kernel and now GRUB won't boot. I have the option to boot older versions from GRUB but that means I'm stuck on Ubuntu 8.10...

Pretty stupid on my behalf. I've tried running update-grub but the problem persists.

Any ideas?

Thanks

---

### Post by frevh on 2009-04-24
have the same problem ;

the upgrade went very easely onlin like i did with previous 2 versions without big problems 
but this time ;
Bug Int 14 CR2 ffffb0f0
Edi 0000000...
Eby 000000046
errr 000000...
Stack c011a26e...

can work with linux old = 8.10

foud some explanation : it seems to be a regression ... I really don't understand this and what can I do ? 
thanks
Fre

---

### Post by meierfra. on 2009-04-24
**Gibbs:**

> I've tried running update-grub but the problem persists.

Try this:

```
cd /boot/grub
sudo mv menu.lst menu.lst.old
sudo update-grub
```

[B]If this did not solve your problem:
[/B]

In order to get a clearer picture of your setup,  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, (use the code tags).

---

### Post by meierfra. on 2009-04-24
**frevh:**  Could you start a new  thread  for your problem?  Trying  to solve two cases in one thread usually is very confusing. Thanks.

---

### Post by frevh on 2009-04-24
ok I understand   'll try

---

### Post by frevh on 2009-04-24
can't find how to start a niew thread:(

---

### Post by frevh on 2009-04-24
can you folow me on this new thread?:confused:

http://ubuntuforums.org/showthread.php?p=7137393#post7137393[/URL]

---

### Post by Gibbs on 2009-05-14
Very late reply, apologies. The install seemed really quick so when prompted to "upgrade" again on the old kernel I did and it worked. I'm assuming it was just a bad/faulty upgrade...

Thanks for all the help though :)

---

