---
title: "4k display"
date: 2014-11-25
forum: Hardware
---

### Post by spiros88 on 2014-11-25
Hello.
I'm tempted to buy a 4k display because I would like to have a high DPI for my work. But I'm not sure that my setup would support such a display.
I have a Nvidia GTX 460 graphics card. I could use both DVI and HDMI plugs (I suppose VGA is not even an option).

What should I check? Would I need a particular DVI or HDMI cable? Would both nouveau and nvidia drivers work?

---

### Post by grahammechanical on 2014-11-25
Check the Nvidia GTX 460 graphics card specifications to see if it can output a signal at 4K. Video drivers cannot give us what the graphic adapter cannot provide.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_4kgpus&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_4kgpus&num=1)

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_4kgpus&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_4kgpus&num=2)

Forget VGA. It simply was not designed to do what you are asking it to do. Old technology. Go with HDMI. It is the standard designed for high definition. You may find that the Display does not even have a DVI port as that too is becoming old technology.

VGA is common place but you will not get the screen resolution you desire. It can be used as a stopgap until we buy an HDMI cable. And then there is the matter of the digital to analogue conversion that the graphic adapter has to do to output VGA and the analogue to digital conversion that the display screen has to do to the VGA input in order to display the signal. Expect signal quality to degrade.

Regards.

---

### Post by Mark Phelps on 2014-11-26
Maximum resolution on that card is 2560x1600 -- a LOT lower than 4K, which is 3840x2160. Don't know if 4K displays can display crisply at resolutions lower than their standard setting.

---

