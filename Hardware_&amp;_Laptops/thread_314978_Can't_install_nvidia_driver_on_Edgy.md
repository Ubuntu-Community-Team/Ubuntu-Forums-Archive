---
title: "Can't install nvidia driver on Edgy"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by josepvm on 2006-12-08
Hi, I'm new to Ubuntu, (I've used SuSE in the past) and I'm trying to configure  Ubuntu 6.10 on my new Asus F3JC Core Duo laptop.

I've tried to install the nvidia driver, according to instruccions in:
[http://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](http://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

but when I try to enable the installed driver (sudo nvidia-glx-config enable) I get the following message:

[I]Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.
[/I]
I'm using the generic kernel. Before attempting to install nvidia driver, I experimented with installing the "linux-686-smp" pakage, as I saw suggested in several webpages, to enable the dual core...only to see that this is not necessary in Ubuntu 6.10, because the generic kernel image already supports  dual core.  So I deinstalled "linux-686-smp", than really does not seem to do anything 

But now nvidia driver understands I have a non standard kernel... I've tried to install again the 686 package, and the nvidia restricted 686 kernel package, and nothing. Then uninstall them and reinstalling the generic versions, and the same error message.

Any ideas, please?

Thank you very much for your help
Josep

---

### Post by PurplePenguin on 2006-12-08
If you get completely fed up with doing it manually, you can always let [Automatix 2]("http://www.getautomatix.com/") install everything for you.

---

### Post by josepvm on 2006-12-08
Thanks, I've found the solution in another thread: the FAQ I was using is outdated. With Edgy's new generic kernel image the nvidia tool used to enable the driver is "nvidia-xconfig"

so, instead of typing "sudo nvidia-glx-config enable", I've used "sudo nvidia-xconfig" and everything works ok now.

---

### Post by maddog39 on 2006-12-08
To be honest with you, the easiest way to do this is to just go to:

Applications->Add/Remove...

Then search for nvidia in the search bar. Install your proper nvidia X.Org driver and then edit your xorg.conf, replacing the driver name as usual. Work flawlessly every time for me.

---

