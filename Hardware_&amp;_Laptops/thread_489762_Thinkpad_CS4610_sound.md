---
title: "Thinkpad CS4610 sound"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by slush1000 on 2007-07-01
Ive just finished installing (K)ubuntu 7.04 on a Thinkpad 600E - everything is working great except for the sound. I am able to get the sound card working by entering the code 

```
sudo /sbin/modprobe cs4232 io=0x530 irq=5 dma=1 dma2=0
```

Then I restart KDE with Ctrl-Alt-Bkspce and the sound is working great.

My question is: 
How do I get that to automatically load and have the sound working on boot rather then having to enter the command and restarting KDE.

Thanks.
PS I know I could probably just restart the sound server with some command rather then restarting KDE but I am also unaware on how to do that too.

---

### Post by yorkie on 2007-07-01
Have a look at this site
[http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_600](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_600)

---

### Post by slush1000 on 2007-07-01
wow :D
thanks for the link.

I have an older desktop that has a ISA sb16 card in it that requires the same treatment. Hopefully I will learn enough from this resource.

---

