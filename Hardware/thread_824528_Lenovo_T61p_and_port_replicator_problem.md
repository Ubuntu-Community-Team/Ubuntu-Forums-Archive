---
title: "Lenovo T61p and port replicator problem"
date: 2008-06-10
forum: Hardware
---

### Post by nampat on 2008-06-10
Hello,

I have switched totally to linux few months ago. Only problem that is annoying me is, that I can't use my port replicator with my Lenovo T61p. It has Nvidia Quadro NVS 140M graphics.

When i attach my laptop to my port replicator, my external keyboard works, network works, mouse works, but i see "No Signal" on my external monitor. Why is that I can't switch my display to external one? At first place I had Windows on my latop and everything worked...

If anyone can help me, I would be more than thankful :)

---

### Post by govt_cheese on 2008-06-12
First, back up your current xorg.conf file!!!!

Try loading the nvidia-settings tool:

```
sudo apt-get install nvidia-settings
```

Open the nvidia-settings app from:

System->Administration->Nvidia X Server Settings

From the GUI, select the option for "X Server Display Config..."
Select and enable the external display via "Configure".
Configure monitor modes as-needed then save your changes.

Good luck!

---

