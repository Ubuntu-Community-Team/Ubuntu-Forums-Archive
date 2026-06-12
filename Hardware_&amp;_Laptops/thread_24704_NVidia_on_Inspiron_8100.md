---
title: "NVidia on Inspiron 8100"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by TjaBBe on 2005-04-08
I installed hoary on my laptop yesterday, and as there is a [bold]NVIDIA GeForce2 Go[/bold] in it I tried to install my nvidia drivers with:
```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo reboot

```
And now my screen just starts white, flows to green, and ends up with two wide green bands, shortly, screwed :).
On Warty my laptop + nvidia drivers worked well. And I installed hoary on my desktop, wich had a GeForce 4 ti4200 I have no problem either. 

So I'm affraid the problems can be traced back to the combination of the Geforce2 Go with the NVIDIA drivers supplied with hoary only. 

Does anyone have an idea how to solve this? I figure I can download the nvidia drivers from nvidia itself, but I'd rather use the one in the repos...

---

### Post by orion_114 on 2005-04-08
Check out this wiki page:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Make sure you goto the correct section for your release.
Hope that helps you out.

---

### Post by TjaBBe on 2005-04-08
[QUOTE=orion_114]Check out this wiki page:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Make sure you goto the correct section for your release.
Hope that helps you out.[/QUOTE]

Thanks! I made a bug report this morning. I will try this out when I get home!

---

