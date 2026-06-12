---
title: "ThinkPad T43 overheating, maybe insufficient RAM?"
date: 2014-06-18
forum: Hardware
---

### Post by Warrior4Christ on 2014-06-18
[COLOR=#141823][FONT=Helvetica]Greetings, friends[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]I have a quick question about my laptop. It's a ThinkPad T43. Lately, whenever it's on and being used for more than 15 to 20 minutes, the bottom, the left side (where the fan is) and under the trackpad get uncomfortably hot, and if you touch the bottom of the computer, it's nearly hot enough to give you a slight burn if you leave it on there for more than a few seconds. I don't know why this has started happening, any help? I'm thinking that maybe I have insufficient RAM and it's making my CPU work harder. The laptop is also running Ubuntu 12.04. Any help or tips would be appreciated, thanks![/FONT][/COLOR]

---

### Post by tgalati4 on 2014-06-18
Blow some compressed air through the slots and see how much dust comes out.  Was the laptop dropped recently?  Open a terminal:

```
free
```

---

### Post by Warrior4Christ on 2014-06-18
No, it hasn't been dropped recently. And what will the "free" command do?

---

### Post by Warrior4Christ on 2014-06-18
Oh wait, never mind, I know what the "free" command will do. I apparently have 288 mb of RAM left. Not too much.

---

### Post by tgalati4 on 2014-06-18
How much total RAM and how large is your swap file?  The output of *free* will tell you.  I have a T43p and they do run hot, but if the heat sink is loose, then the heat may not be transferred properly.  If the fan or the vanes on the heatsink are clogged, then that will cause it to run hot.  What is the output of:

```
sensors
```

Install *htop* and see if you have a stuck process:

```
sudo apt-get install htop
htop
```

---

### Post by Warrior4Christ on 2014-06-18
Here's the output of *free:*


 ```
             total       used       free     shared    buffers     cached
Mem:       1545008    1380576     164432          0      41016     328236
-/+ buffers/cache:    1011324     533684
Swap:      1569788     164996    1404792
```

Swap file size is 1569788 bytes, and I have 1545008 bytes of RAM, or 1508 megabytes of RAM and a swap file size of 1532 megabytes.  I don't seem to have a stuck process when I run *htop*.

---

### Post by tgalati4 on 2014-06-18
1.5 GB of RAM is sufficient.  You are using some swap, but not a lot.  Without knowing the temperatures (and Thinkpads have a lot of sensors), I can't say if it is running hot or not.

---

### Post by mörgæs on 2014-06-18
Please use CODE tags when posting terminal output.

**free -m** gives output which is easier to read.

For old hardware Lubuntu 14.04 is often a better choice, that is puts less load on the processor.

---

