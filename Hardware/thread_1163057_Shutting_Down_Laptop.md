---
title: "Shutting Down Laptop"
date: 2009-05-18
forum: Hardware
---

### Post by verbal.kint on 2009-05-18
When I shut down my laptop I get the ubuntu loading screen thing and then I just get some text in the corner 

```
[12345.6789] shutdown 
```

The fan is left running and I have to hold the shutdown button to turn off the laptop completly.


I had this issue when I was using gutsy, apparently it was some kernel thing, I can't quite remember. I thought it would be fixed by 9.04 but it appears not.

So I am now prepared to try and fix this issue if anyone has any ideas?

It's a [Packard Bell EasyNote MV]("http://www.packardbell.co.uk/products/on-the-go/notebooks/easynote-mv/easynote-mv46-008/productsheet-PB66M00401-805.html")

---

### Post by carlbeech on 2009-06-05
I'm also having this problem - I also had a white screen when shutting down. I got around this by taking off the word 'splash' from the grub menu.

However, I still can't shut down - it's either hold the power button down, when the 'shutdown' message is on the screen, or perform a reboot - and press the power button before the grub menu appears (I don't have to hold it down this way).

Anyone had any thoughts? - I've heard you have to put 'acpi=force' in the grub startup line, however, this doesn't appear to help...

- Carl.

Asus x59GL - apart from that, most is running fine (3d/wifi etc)

---

